<p align="center">
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="allnodes/images/firedancer-dark-mode.png">
      <img alt="Firedancer Allnodes Edition" src="allnodes/images/firedancer-light-mode.png">
    </picture>
</p>


# Firedancer Solana validator with modifications from Allnodes

## Modifications made by Allnodes

This repository features the following enhancements to the Firedancer codebase:

### 1. Fast snapshot distribution

✅ Only on [Allnodes Bare-Metal Servers](https://www.allnodes.com/hosting)

Our infrastructure includes modifications that improve default snapshot downloading, which combined with
ultra-high-speed channels deliver ultra-fast snapshot downloads. This dramatically reduces the initial sync time for
new validators and enables faster deployment and recovery scenarios. The use of snapshot-finder or any other 3rd party
download tools is no longer needed.

### 2. Enhanced voting logic modifications

✅ Only on [Allnodes Bare-Metal Servers](https://www.allnodes.com/hosting)

Our validator implementation includes voting modifications developed by **Zantetsu | Shinobi Systems** that enhance the
original voting logic.

These modifications work by:

- Taking the next votable slot that the original codebase identifies as potentially ready for voting
- Applying additional criteria before casting the vote
- Providing more sophisticated voting decision-making

This enhancement improves validator consensus participation through more intelligent vote timing and slot evaluation.

### 3. Hardware-optimized SHA256 patch

Our validator implementation includes a third-party performance patch developed by **kagren**. It optimizes SHA256
hashing operations using SHA-NI instructions available on modern AMD processors (Zen3, Zen4, and Zen5
architectures). This enhancement significantly improves hashing performance for block verification and other
cryptographic operations.


# [Firedancer](https://jumpcrypto.com/firedancer/) 🔥💃

Firedancer is a new validator client for Solana.

* **Fast** Designed from the ground up to be *fast*. The concurrency
model draws from experience in the low latency trading space, and the code
contains many novel high-performance reimplementations of core Solana
primitives.
* **Secure** The architecture of the validator allows it to run with a
highly restrictive sandbox and almost no system calls.
* **Independent** Firedancer is written from scratch. This brings client
diversity to the Solana network and helps it stay resilient to supply
chain attacks in build tooling or dependencies.

## Documentation
If you are an operator or looking to run the validator, see the Getting
Started guide in the [Firedancer
docs](https://docs.firedancer.io/)

## Releases
If you are an operator looking to run the validator, see the [Releases
Guide](https://docs.firedancer.io/guide/getting-started.html#releases)
in the documentation.

The Firedancer project is producing two validators,

* **Frankendancer** A hybrid validator using parts of Firedancer and
parts of Agave. Frankendancer uses the Firedancer networking stack and
block production components to perform better while leader. Other
functionality including execution and consensus is using the Agave
validator code.
* **Firedancer** A full from-scratch Firedancer with no Agave code.

Both validators are built from this codebase. The Firedancer validator
is not ready for test or production use and has no releases.
Frankendancer is currently available on both Solana testnet and
mainnet-beta.

## Developing
Firedancer currently only supports Linux and requires a relatively new
kernel, at least v4.18 to build.

```console
$ git clone --recurse-submodules https://github.com/firedancer-io/firedancer.git
$ cd firedancer
$ ./deps.sh +dev
$ make -j run
```

The `make run` target runs the `fddev dev` command. This development
command will ensure your system is configured correctly before creating
a genesis block, some keys, a faucet, and then starting a validator on
the local machine. `fddev` will use `sudo` to make privileged changes to
system configuration where needed. If `sudo` is not available, you may
need to run the command as root.

By default `fddev` will create a new development cluster, if you wish to
join this cluster with other validators, you can define
`[rpc.entrypoints]` in the configuration file to point at your first
validator and run `fddev dev` again.

## License
Firedancer is available under the [Apache 2
license](https://www.apache.org/licenses/LICENSE-2.0). Firedancer also
includes external libraries that are available under a variety of
licenses. See [LICENSE](LICENSE) for the full license text.
