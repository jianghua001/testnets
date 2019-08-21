# How To Participate in Genesis Process

## Requirement

You must have follow this [guide](https://github.com/irisnet/irishub/blob/release0.10/docs/get-started/Install-the-Software.md) to install the correct version of **Iris**.

## Step 1: Create your own account


First you need to create a account as the corresponding validator operator for yourself if you don't have one
or you forgot its password.

```bash
iriscli keys add {account_name}
```
You can get the account information, including account address, public key address and mnemonic
```
NAME: TYPE: ADDRESS:            PUBKEY:
account_name  local faa13t6jugwm5uu3h835s5d4zggkklz6rpns59keju  fap1addwnpepqdne60eyssj2plrsusd8049cs5hhhl5alcxv2xu0xmzlhphy9lyd5kpsyzu
**Important** write this seed phrase in a safe place.
It is the only way to recover your account if you ever forget your password.

witness exotic fantasy gaze brass zebra adapt guess drip quote space payment farm argue pear actress garage smile hawk bid bag screen wonder person
```

## Step 2: Initialize your node

Initialize the configuration files such as genesis.json and config.toml
```bash
iris init --home={path_to_your_home} --chain-id=fuxi-8000 --moniker=key-name
```

This command will create the corresponding files in the home directory.


## Step 3: Execute `gentx` command

```bash
iris gentx --name={operator_key_name} --home={path_to_your_home} --ip=node-ip
```
This commond will generate the transaction in the directory：{path_to_your_home}/config/gentx
Create the `CreateValidator` transaction and sign the transaction by the validator operator account you just created
The default commission data is:
*	delegation amount:           100iris
*	commission rate:             0.1
*	commission max rate:         0.2
*	commission max change rate:  0.01

> IP is your public IP, dont use internal IP

## Step 4: Sumbit your gentx.json

Submit your gentx-node-ID.json to `https://github.com/irisnet/testnets/tree/master/fuxi/fuxi-8000/config/gentx` by createing a pull request.

After the team has collected all the gen-tx transactions, we will publish the genesis file.

You could then download the final genesis file and start a node. 

