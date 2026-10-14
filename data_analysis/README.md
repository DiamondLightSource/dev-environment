# Data analysis

A Tiled 0.2.18 server that serves files from `./data` and adds a custom `/hello` endpoint.

## Run

```sh
cd data_analysis
docker compose up
```

Once it is up, files in `./data` are registered into the catalog by the `post_start` hook.

- Browse data: http://localhost:8000/ui
- List entries: `curl http://localhost:8000/api/v1/search/`
- Read the example CSV: `curl "http://localhost:8000/api/v1/table/full/example?format=csv"`
- Hello world: `curl http://localhost:8000/custom/hello` (also at `/api/v1/hello`)

## Layout

- `config/config.yml` - Tiled config (catalog over `/data`, custom routers).
- `config/hello.py` - FastAPI router with the hello world endpoint, loaded via `routers:`.
- `data/` - mounted read-only at `/data`. Drop files here and restart (or run `docker compose exec tiled tiled register http://localhost:8000 /data --api-key secret`).

The API key `secret` is for local development only.
