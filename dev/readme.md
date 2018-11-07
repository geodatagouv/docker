# Development environment

Use this docker-compose.yml configuration to setup a full development environment for [geodatagouv/geoplatform](https://github.com/geodatagouv/geoplatform) and [geodatagouv/link-proxy](https://github.com/geodatagouv/link-proxy).

This exposes the following services:

- Redis (6379)
- arena (4567)
- udata (7000)
- mongo-express (8081)
- Minio (9000)
- elasticsearch
- MongoDB (27017)


## Getting started

To run the environment:

```bash
docker-compose up
```

Both `geoplatform` and `link-proxy` repositories should include a `.env.sample` env file that works with this environment.


### udata

#### 1. Bootstrap instance

The first time you run this, you need to bootstrap your `udata` instance, run

```bash
docker-compose run --rm udata init
```

And follow the steps.

#### 2. Create an organization on udata

- Visit http://localhost:7000
- Login with the previously created admin account
- Go to the admin and create an organization

#### 3. Create an OAuth2 client

You need to manually create an OAuth2 client in the mongo database:

- Visit http://localhost:8081/db/udata
- Create a new `oauth2_client` collection
- Create a new document based on the following template:

```json
{
    "_id": ObjectID(),
    "created_at": ISODate("2014-10-02T19:37:23.738Z"),
    "last_modified": ISODate("2014-10-02T19:37:23.739Z"),
    "secret": "secret",
    "name": "name",
    "description": "description",
    "organization": ObjectID("<previously created organization id>"),  // The id of your organization previous
    "redirect_uris": [
        "http://localhost:5001/dgv/oauth/callback"
    ],
    "scopes": [
        "default"
    ],
    "confidential": false,
    "internal": true
}
```
