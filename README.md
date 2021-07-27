# dpaste
multi platform automated build for dpaste docker image

Supported platforms:

- AMD64
- ARM64

## deployment 

Quickstart to run a dpaste container image:

```
$ docker run --rm -p 8000:8000 melashri/dpaste:latest
```

The dpaste image serves the project using uWSGi and is ready for 
production-like environments. However it’s encouraged to use an external
 database to store the data. See the example below for all available 
options, specifically `DATABASE_URL`

```bash
$ docker run --rm --name db1 --detach postgres:latest
$ docker run --rm -p 12345:12345 \
      --link db1 \
      -e DATABASE_URL=postgres://postgres@db1:5432/postgres \
      -e DEBUG=True \
      -e SECRET_KEY=very-secret-key \
      -e PORT=12345 \
      barttc/dpaste:latest
```
