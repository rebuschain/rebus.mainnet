# Rebus v1 Mainnet

## Instructions Updated

### Genesis Validators

Update the rebus.core pulling the latest code 

```bash
git clone https://github.com/rebuschain/rebus.core.git 
cd rebus.core && git checkout master
make install
```

## Validators files

Remeber to use your previous validator keys used to generate your gentx, these are in the ~/.rebusd/config where you ran rebusd:
```
node_key.json
priv_validator_key.json
```


## Init the data folder and configure the Chain ID 

```
rebusd init <your-moniker> --chain-id reb_1111-1
```

## Consensus timeout_commit 

The rebusd init is configuring in the config.toml [consensus] section the timeout_commit to "2s"

```
#######################################################
###         Consensus Configuration Options         ###
#######################################################
[consensus]
timeout_commit = "2s"
```


## Genesis File

You can download the genesis file for the chain with all the gentxs submitted and accepted and the intial chain state.

```
curl https://raw.githubusercontent.com/rebuschain/rebus.mainnet/master/reb_1111-1/genesis.zip > ~/.rebusd/config/genesis.zip
```

You need to unzip the genesis.
```
unzip genesis.zip
```


We recommend using sha256sum to check the hash of the genesis.

Linux
```
cd ~/.rebusd/config
echo "10cc853d7ccc8ebc67155ee4ffc1bb32caac3f05873df79e866524898b3f20eb  genesis.json" | sha256sum -c
```
MacOS
```
cd ~/.rebusd/config
echo "10cc853d7ccc8ebc67155ee4ffc1bb32caac3f05873df79e866524898b3f20eb  genesis.json" | shasum -a 256 -c
```

The correct genesis file is in the https://github.com/rebuschain/rebus.mainnet/tree/master/reb_1111-1 folder

## Reset Chain Database

There shouldn't be any chain database yet, but in case there is for some reason, you should reset it. This is a good idea especially if you ran rebusd start on a broken genesis file. 

```
rebusd  tendermint unsafe-reset-all 
```

## Seed 

The file seeds contains the Rebus id/ip nodes.


## Details

- Network Chain ID: `reb_1111-1`
- EIP155 Chain ID: `1111`
- rebusd version: `v0.1.0`
