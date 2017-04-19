# nem-nodejs-bot: Node.js Bot for the NEM blockchain

This is a multi feature Bot written in Node.js for the NEM blockchain. This bot can be deployed to Heroku free tiers
or serving locally.

### Installation

The secure-conf plugin is used to encrypt the config/bot.json file. This file is where you should configure this bot.

The bot can be configured to execute any, none or all of the following features:
 - Payment Channel Listening (Read permission)
 - Balance Modifications Listening (Read permission)
 - Cosignatory Auditing (Read permission)
 - Multi Signature Transaction Co-Signing (Write permission)

Only WRITE features need your Private Key, change the "mode" config to "read" or "write" or "both" to enable/disable read and write.
This allows deploying read-only bots which don't need your Private Key and can be addressed through an easy HTTP API.

For a local installation, first install the dependencies of this package. Using the terminal works as follows:
```
    $ cd /path/to/this/clone
    $ npm install
```

You should now take a look at ```config/bot.json``` and configure your Bot instance.

After configuration, you can start the Bot, locally this would be:
```
    $ npm run_bot.js
```

You can configure your Bot's configuration encryption password with the ENCRYPT_PASS environment variable. In heroku you can add env
variables in the Settings tab of your app. Using Linux you can add environment variable at startup like the following:
```
    $ env ENCRYPT_PASS=notSecurePass node run_bot.js
```

The config/bot.json file will only be removed in "production" mode.

### Deploy on Heroku

This NEM Bot is compatible with heroku free tiers. This means you can deploy the source code (AFTER MODIFICATION of config/bot.json)
to your Heroku instance and the Bot will run on the heroku tier. Before you deploy to the Heroku app, you must configure following
```Config Variables``` in your Heroku App (Settings) :
```
    - Required:
        - ENCRYPT_PASS : Should contain the configuration file encryption password.
        - PORT : Should contain the Port on which the Bot should be addressed.

    - Optional :
        - NEM_HOST : Mainnet default NEM node. (http://alice6.nem.ninja)
        - NEM_PORT : Mainnet default NEM node port. (7890)
        - NEM_HOST_TEST : Testnet default NEM node. (http://bob.nem.ninja)
        - NEM_PORT_TEST : Testnet default NEM node port. (7890)
```

### Private Deploy

You can specify basic HTTP auth parameters in the nem-bot.htpasswd file. Default username is ```demo``` and default password
is ```opendev```. To enable basic HTTP auth you must set the option "bot.protectedEndpoints" to ```true```, the Bot will then
read the nem-bot.htpasswd file.

### Pot de vin

If you like the initiative, and for the sake of good mood, I recommend you take a few minutes to Donate a beer or Three [because belgians like that] by sending some XEM (or whatever Mosaic you think pays me a few beers someday!) to my Wallet:

NB72EM6TTSX72O47T3GQFL345AB5WYKIDODKPPYW

### License

This software is released under the [MIT](LICENSE) License.

© 2017 Grégory Saive greg@evias.be, All rights reserved.