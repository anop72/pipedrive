# pipedrive

document https://developers.pipedrive.com/docs/api/v1/#/

`/GET` activityFields

`curl -X GET https://api.pipedrive.com/v1/activityTypes?api_token={token}`

### library
https://github.com/pipedrive/client-nodejs#supported-operations-for-object-collections

### snippet

`STAGE_ID` stage id from Pipedrive


```js
function login() {

  return new Promise((resolve, reject) => Pipedrive.authenticate({email: '', password: '' }, (err, res) => {

    if (err) reject(err)

    resolve(res)

  }))
}

var addDeal = (title) => {
  return new Promise((resolve, reject) => pipedrive.Deals.add({title: title, stage_id: STAGE_ID}, (err, res) => {

    if (err) reject(err)

    resolve(res)

  }))
}

var addActivities = (dealId) => {
  return new Promise((resolve, reject) => pipedrive.Activities.add({type: '', subject: '', deal_id: dealId}
    , (err, res) => {

      if (err) reject(err)

      resolve(res)

  }))
}

async function drive(req, res) {

  try {

    await login()
    const deal = await addDeal('Arrival')
    const result = await addActivities(deal.id)

    console.log(result);

    res.sendStatus(201)

  }catch(err) {
    res.sendStatus(401)
  }

}
```
