# Welcome Genesis Validators!

### TLDR

Genesis time is: TBA

Block explorer: TBA

Binaries: TBA

Genesis file: TBA

Seeds: TBA

**Minimum hardware requirements:**

-   4 or more physical[1] CPU cores
-   At least 500GB of SSD disk storage
-   At least 16GB of memory
-   At least 100mbps network bandwidth

**dymd version**

```sh
name: dymension
server_name: dymd
version: TBA
commit: TBA
```

## Setup

**Prerequisites:** Make sure to have [Golang >=1.18](https://golang.org/).

### Build from source

You need to ensure your gopath configuration is correct. If the following **'make'** step does not work then you might have to add these lines to your .profile or .zshrc in the users home folder:

```sh
nano ~/.profile
```

```
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export GO111MODULE=on
export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin
```

Source update .profile

```sh
source .profile
```

```sh
git clone https://github.com/dymensionxyz/dymension.git
cd dymension
git checkout v0.1.0-alpha
make build && make install
```

This will build and install `dymd` binary into `$GOBIN`.

Note: When building from source, it is important to have your `$GOPATH` set correctly. When in doubt, the following should do:

```sh
mkdir ~/go
export GOPATH=~/go
```

Check that you have the right Dymension version installed:

```sh
name: dymension
server_name: dymd
version: v0.1.0-alpha
commit: f68b1000f040ace7c266b6c4b5e7c4a8b9a31378
```

## Setup a Validator Node

Below are the instructions to generate & submit your genesis transaction

### Generate genesis transaction (gentx)

1. Initialize the Dymension directories and create the local genesis file with the correct chain-id:

    ```bash
    dymd init <moniker-name> --chain-id=elvis-1
    ```

2. Create a local key pair:

    ```sh
    dymd keys add <key-name>
    ```

3. Add your account to your local genesis file with a given amount and the key you just created. Use only `10000000000udym`, other amounts will be ignored.

    ```bash
    dymd add-genesis-account $(dymd keys show <key-name> -a) 10000000000udym
    ```

4. Create the gentx, use only `9000000000udym`:

    ```bash
    dymd gentx <key-name> 9000000000udym --chain-id=elvis-1
    ```

    If all goes well, you will see a message similar to the following:

    ```bash
    Genesis transaction written to "/home/user/.dymension/config/gentx/gentx-******.json"
    ```

### Submit genesis transaction

-   Fork [the testnets repo](https://github.com/dymensionXYZ/testnets/) into your Github account

-   Clone your repo using

    ```bash
    git clone https://github.com/<your-github-username>/testnets
    ```

-   Copy the generated gentx json file to `<repo_path>/elvis-1/gentx/`

    ```sh
    cd testnets/Dymension-Hub/elvis-1
    cp ~/.dymension/config/gentx/gentx*.json ./gentx/
    ```

-   Commit and push to your repo
-   Create a PR onto https://github.com/dymensionXYZ/testnets
-   Only PRs from selected individuals / groups with a history successfully running nodes will be accepted. This is to ensure the network successfully starts on time.

### Review Genesis File

-   Once all gentx have been collected the Genesis file will be made available:

**Genesis File**

**Genesis sha256**

```bash
sha256sum ~/.dymension/config/genesis.json
1be5d2e0127e7c4b7e2582095544da23b5add3c2d2227b8c055ad78da25f7afa ~/.dymension/config/genesis.json
```

**Validate the Genesis file**

```bash
dymd validate-genesis
```

Add seed nodes in config.toml.

```sh
vi $HOME/.dymension/config/config.toml
```

**Seed nodes**

```bash
# Comma separated list of seed nodes to connect to
TBA
```

**Persistent Peers**

```bash
# Comma separated list of persistent peers to connect to
TBA
```

#### Set validator gas fees

You can set the minimum gas prices for transactions to be accepted into your node's mempool. This sets a lower bound on gas prices, preventing spam. Dymension can accept gas in _any_ currency. To accept both DYM and ATOM for example, set `minimum-gas-prices` in `app.toml`.

```sh
vi $HOME/.dymension/config/app.toml
```

```sh
minimum-gas-prices = "0.025udym,0.025uatom"
```

### Genesis time is: 2022-11-24T14:00:00Z

-   Begin the node, once 2/3rd of staked tokens are online after genesis time the blockchain has begun!
    ```sh
    dymd start
    ```

## Setup

**Prerequisites:** Make sure to have [Golang >=1.18](https://golang.org/).

### Build from source

You need to ensure your gopath configuration is correct. If the following **'make'** step does not work then you might have to add these lines to your .profile or .zshrc in the users home folder:

```sh
nano ~/.profile
```

```
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export GO111MODULE=on
export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin
```

Source update .profile

```sh
source .profile
```

```sh
git clone https://github.com/dymensionxyz/dymension.git
cd dymension
git checkout v0.1.0-alpha
make build && make install
```

This will build and install `dymd` binary into `$GOBIN`.

Note: When building from source, it is important to have your `$GOPATH` set correctly. When in doubt, the following should do:

```sh
mkdir ~/go
export GOPATH=~/go
```

Check that you have the right Dymension version installed:

```sh
name: dymension
server_name: dymd
version: v0.1.0-alpha
commit: f68b1000f040ace7c266b6c4b5e7c4a8b9a31378
```

## Setup a Validator Node

Below are the instructions to generate & submit your genesis transaction

### Generate genesis transaction (gentx)

1. Initialize the Dymension directories and create the local genesis file with the correct chain-id:

    ```bash
    dymd init <moniker-name> --chain-id=elvis-1
    ```

2. Create a local key pair:

    ```sh
    dymd keys add <key-name>
    ```

3. Add your account to your local genesis file with a given amount and the key you just created. Use only `10000000000udym`, other amounts will be ignored.

    ```bash
    dymd add-genesis-account $(dymd keys show <key-name> -a) 10000000000udym
    ```

4. Create the gentx, use only `9000000000udym`:

    ```bash
    dymd gentx <key-name> 9000000000udym --chain-id=elvis-1
    ```

    If all goes well, you will see a message similar to the following:

    ```bash
    Genesis transaction written to "/home/user/.dymension/config/gentx/gentx-******.json"
    ```

### Submit genesis transaction

-   Fork [the testnets repo](https://github.com/dymensionXYZ/testnets/) into your Github account

-   Clone your repo using

    ```bash
    git clone https://github.com/<your-github-username>/testnets
    ```

-   Copy the generated gentx json file to `<repo_path>/elvis-1/gentx/`

    ```sh
    cd testnets/Dymension-Hub/elvis-1
    cp ~/.dymension/config/gentx/gentx*.json ./gentx/
    ```

-   Commit and push to your repo
-   Create a PR onto https://github.com/dymensionXYZ/testnets
-   Only PRs from selected individuals / groups with a history successfully running nodes will be accepted. This is to ensure the network successfully starts on time.

### Review Genesis File

-   Once all gentx have been collected the Genesis file will be made available:

**Genesis File**

**Genesis sha256**

```bash
sha256sum ~/.dymension/config/genesis.json
1be5d2e0127e7c4b7e2582095544da23b5add3c2d2227b8c055ad78da25f7afa ~/.dymension/config/genesis.json
```

**Validate the Genesis file**

```bash
dymd validate-genesis
```

Add seed nodes in config.toml.

```sh
vi $HOME/.dymension/config/config.toml
```

**Seed nodes**

```bash
# Comma separated list of seed nodes to connect to
TBA
```

**Persistent Peers**

```bash
# Comma separated list of persistent peers to connect to
TBA
```

#### Set validator gas fees

You can set the minimum gas prices for transactions to be accepted into your node's mempool. This sets a lower bound on gas prices, preventing spam. Dymension can accept gas in _any_ currency. To accept both DYM and ATOM for example, set `minimum-gas-prices` in `app.toml`.

```sh
vi $HOME/.dymension/config/app.toml
```

```sh
minimum-gas-prices = "0.025udym,0.025uatom"
```

### Genesis time is: 2022-11-24T14:00:00Z

-   Begin the node, once 2/3rd of staked tokens are online after genesis time the blockchain has begun!
    ```sh
    dymd start
    ```