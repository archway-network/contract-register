# contract-register
Register of CW contracts deployed on Archway.

The following [GitHub Issue](https://github.com/archway-network/archway/issues/471) describes an Archway Improvement Proposal (AIP) for the inclusion of a module which can be used by contract deployers to provide metadata about their contracts.

This repository follows the same technical specification format to ensure future compatibility with such a module.

The repository directory is structured as follows:

```
.
|-- LICENSE
|-- README.md         
|-- mainnet
|   |-- 1                   # this corresponds to the code id on mainnet
|       |-- metadata.json   # this will hold the metadata object as below
|       |-- schema.json     # this will hold schema document contents for the code id
|       |-- contracts.json  # this will hold all the instances of the contracts
|   |-- 2
|   |-- 3
|   |-- ...
|-- testnet
|   |-- ...
|   |-- x                   # this corresponds to the code id on testnet
|       |-- metadata.json   # this will hold the metadata object as below
|       |-- schema.json     # this will hold schema document contents for the code id
|       |-- contracts.json  # this will hold all the instances of the contracts
|   |-- ...
```

## Register your contracts

- Create a directory under the corresponding network using the appropriate code id;
- Create the following files in this new directory:
    1. `metadata.json` - contains metadata object;
    2. `schema.json` - contains schema contents for corresponding code id;
    3. `contracts.json` - contains instances of deployed contracts;
- Create a PR to get it merged into this repository;

`metadata.json` example:

```json
{
    "code_id": ,
    "source": {
        "repository": "https://github.com/archway-network/archway",
        "tag": "v1.0.2",
        "license": "Apache-2.0"
    },
    "source_builder": {
        "image": "cosmwasm/rust-optimizer",
        "tag": "0.12.6",
        "contract_name": "counter.wasm"
    },
    "schema": "<path to schema.json>",
    "contacts": [
        "me@mydomain.com",
        "security@mydomain.com",
    ]
}
```

`contracts.json` example:

```json
[
    {
        "label": "My Contract",
        "address": "archway1...",
        "memo": "Any additional information to provide more context, e.g. Responsible for the voting mechanism of x multisig."
    }
]
```
