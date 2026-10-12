
# Selfhosted live-sync obsidian storage


Based of https://github.com/oleduc/docker-obsidian-livesync-couchdb


## Set up

1. create and edit env `cp .env.example .env && vi .env` 
2. `docker compose up -d`
3. `cloudflared tunnel --url http://localhost:5984`
4. generate uri

```bash
source .env
export hostname="$SERVER_URL"
export database="$COUCHDB_DATABASE"
export username="$COUCHDB_USER"
export password="$COUCHDB_PASSWORD"
export passphrase="<YOUR_VAULT_ENCRYPTION_PASSPHRASE>"   # required – provide a strong passphrase
#export uri_passphrase="<YOUR_SETUP_URI_PASSPHRASE>"      # optional, omit if not needed
deno run --minimum-dependency-age=0 --allow-env https://raw.githubusercontent.com/vrtmrz/obsidian-livesync/main/utils/setup/generate_setup_uri.ts > setup-uri.txt
```


## TO DO

- [x] ~~remote server configuration playbook~~ github actions
