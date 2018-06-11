# Burstcoin unRAID Docker Template

Docker template for the [Burstcoin Wallet](https://github.com/poc-consortium/burstcoin/) for [unRAID](https://lime-technology.com/)

## To use:

1. Add `https://github.com/harry1453/burstcoin-unraid-docker` to your list of template repositories under the Docker tab.

2. Add new container, select `burstcoin` as the template, specify where you want to store the database.

3. Start the container! Don't forget to turn on auto-start in the unRAID Docker tab!

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

## Setting up CreepMiner

1. Add `https://github.com/harry1453/burstcoin-unraid-docker` to your list of template repositories under the Docker tab (if it's not there already)

2. Add new container, select `CreepMiner` as the template. Select the location of your plotfiles and either remove or add paths as needed. Then click "Show more settings" and specify the config directory - make it somewhere you have access to as you'll need to change the config!

3. Start the container.

4. From the unRAID Docker tab, click on the container icon and select "Console"

5. In the console, run `cp /usr/local/sbin/mining.conf /config && chmod 777 /config/mining.conf`

6. Close the console and go to the config directory you specified earlier

7. Open `mining.conf` using a text editor. Change the `miningInfo` and `submission` URLs to those of your pool. Make sure to include `http://`, so for example for the PoCC 0-100 Pool the address would be: `http://0-100-pool.burst.cryptoguru.org:8124`. You can change the `wallet` URL if you so wish, but it will work fine with the default CreepMiner wallet.

8. Change the `user` and `pass` under `credentials` to those of your choice, for example:
```XML
"credentials" : {
    "pass" : "password",
    "user" : "harry"
},
```

9. Save and close `mining.conf`. Go back to the unRAID Docker tab, click on the container icon, and click restart.

10. Once the container has restarted, click on the container icon and select "WebUI". Login to the CreepMiner WebUI using the username and password you specified.

11. Click on "Plots", and add plot directories as you specified earlier, such as `/plot/01`, `/plot/02`, `/plot/03`, and any other you specified.

12. You are finished! Check that your miner is submitting valid deadlines, and don't forget to turn on auto-start in the unRAID Docker tab!
