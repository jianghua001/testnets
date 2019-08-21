# How to Create Genesis File

1. Backup your `irishome`
2. Export Snapshot of height #157491 from the halted network
  Using iris `0.10.2-patch-c92d1680-1`, run the following command:
```
iris export  --home= --for-zero-height --height=157491
```
This command will generate a new genesis file `genesis.json` in your current path.
Md5sum should be: `3d140361770cd4f18618f1629eead49e`
 
3. Modify fileds in genesis.json
* Add `tx_size` param in `auth`
```json
"params": {
        "gas_price_threshold": "20000000000000",
        "tx_size": "1000"
      }
```
* Modify `Upgrade` field:
```json
"GenesisVersion": {
        "Success": true,
        "UpgradeInfo": {
          "ProposalID": "0",
          "Protocol": {
            "height": "1",
            "software": "https://github.com/irisnet/irishub/releases/tag/v0.11.0",
            "threshold": "0.9000000000",
            "version": "0"
          }
        }
      }
    }
```
* Add  `slash-fraction-censorship`and `censorship-jail-duration` params in `slashing`
```
"params": {
        "censorship-jail-duration": "604800000000000",
        "double-sign-unbond-duration": "432000000000000",
        "downtime-unbond-duration": "172800000000000",
        "max-evidence-age": "86400000000000",
        "min-signed-per-window": "0.5000000000",
        "signed-blocks-window": "20000",
        "slash-fraction-censorship": "0.0200000000",
        "slash-fraction-double-sign": "0.0100000000",
        "slash-fraction-downtime": "0.0050000000"
      }
```
*  Add ` tx_size_limit` param in `service`
```
"params": {
        "arbitration_time_limit": "432000000000000",
        "complaint_retrospect": "1296000000000000",
        "max_request_timeout": "100",
        "min_deposit_multiple": "1000",
        "service_fee_tax": "0.0100000000",
        "slash_fraction": "0.0010000000",
        "tx_size_limit": "4000"
      }
```
Md5sum for new genesis file is: 
6f13af716dad55bb102f953804989ab8

Example output genesis is [here](https://raw.githubusercontent.com/irisnet/testnets/master/fuxi/fuxi-8000/config/new-genesis.json)

# How to Restart
* Verify `iris` version
```
iris version
0.11.0-ae1e491-0
```

* Clear existing data
```
iris unsafe-reset-all --home
```
* Replace existing genesis file with the [new one](https://raw.githubusercontent.com/irisnet/testnets/master/fuxi/fuxi-8000/config/new-genesis.json)

* Start iris

```
iris start --home
```

