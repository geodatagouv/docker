# Development environment

Use this docker-compose.yml configuration to setup a full development environment for [geodatagouv/geoplatform](https://github.com/geodatagouv/geoplatform) and [geodatagouv/link-proxy](https://github.com/geodatagouv/link-proxy).

This exposes the following services:

- Redis (6379)
- arena (4567)
- udata (7000)
- mongo-express (8081)
- Minio (9000)
- elasticsearch (9200)
- MongoDB (27017)


## Getting started

To run the environment:

```bash
$ docker-compose up
```

Both `geoplatform` and `link-proxy` repositories should include a `.env.sample` env file that works with this environment.
