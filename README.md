# Burstcoin unRAID Docker Template

Docker template for the [Burstcoin Wallet](https://github.com/poc-consortium/burstcoin/) for [unRAID](https://lime-technology.com/)

## To use:

1. Add `https://github.com/harry1453/burstcoin-unraid-docker` to your list of template repositories under the Docker tab.

2. Add new container, select `burstcoin` as the template, specify where you want to store the database.

3. Start the container!

## Importing database

1. Open a terminal inside the container using the GUI or by running `docker exec -it BurstcoinWallet sh`

2. Install bash by typing `apk update && apk add bash`

3. Open bash by running `/bin/bash`

3. Execute the following:

```BASH
cd /etc/burstcoin
chmod +x burst.sh
./burst.sh import h2
```

4. Accept removing the old database and let it download.
