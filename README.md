### Local setup

The below steps assume the following project structure 

```
- Dockerfile
- cgc-api
  - ...
- db_dump
  - cgc_nft_postgres.dump
- dc-bot
  - ...
- docker-compose.yml
- README.md
```

so make sure you've checked out the projects and downloaded the DB dump to proper directory.


#### Steps

1. Spin up DB:

```
docker compose up db -d
```

2. Create role for Grafana (required to restore dump)

```
docker compose exec db psql -d postgres -U postgres -c "create role cgc_grafana_ronly"
```

3. Restore dump

```
docker compose exec db psql -d postgres -U postgres -f /db_dump/cgc_nft_postgres.dump
```


4. Setup `.env` files for both projects 


5. Run all services 

```
docker compose up -d
```

6. Tail logs for all services

```
docker compose logs -f
```

