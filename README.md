# Kaon Network Developer Documentation

## Overview

| **Property**               | **Details**                                  |
|----------------------------|----------------------------------------------|
| **Network Name**            | Kaon                                         |
| **Native Token**            | KAON                                         |
| **Consensus**               | dPoS, cold staking, and leasing              |
| **Validator Commitment**    | Collator TX with OP_CTVL                     |
| **Block Time**              | Every 10 seconds                             |
| **Ecosystem**               | UTXO + EVM                                   |
| **TPS**                     | _Pending Update_                             |
| **Currency Symbol**         | KAON                                         |
| **Chain ID**                | 10101                                        |
| **RPC URL**                 | [https://testnet.kaon.one](https://testnet.kaon.one) |
| **Block Explorer URL**      | [https://explorer.testnet.kaon.one](https://explorer.testnet.kaon.one) |

## Transaction Support

| **Transaction Types**                            | **Details**                                            |
|--------------------------------------------------|--------------------------------------------------------|
| Bitcoin Transaction Types                        | Supported                                              |
| Cascade Signature Transaction                    | Supported                                              |
| EVM Stored Transactions                          | Supported                                              |
| Invoice Address Type                             | All Bitcoin prefixes + Ethereum format address          |
| Sending All Balance                              | Supported                                              |
| Transaction Outputs                              | Enforced to be at least 43 (0conf transactions planned) |

## EVM Interface

| **EVM Interface Specifics**                      | **Details**                                            |
|--------------------------------------------------|--------------------------------------------------------|
| `eth_sign`                                       | Uses different message prefix: `"\x15Kaon Signed Message:\n"` |
| Contract Address Generation                      | Uses TX hash instead of nonce                          |
| Block Hash                                       | Computed differently, block headers behave incorrectly (backlog) |
| Debug Calls                                      | Not supported (on roadmap)                             |
| Sending Coins in Creation                        | Prohibited, transactions rejected                      |
| `msg.value`                                      | Completely supported                                   |
| Non-EVM Accounts                                 | Observable and interactable                            |
| `eth_estimateGas`                                | Completely supported                                   |
| Receipts                                         | Supported for all transactions                         |
| Multiple Receivers (BTC transactions)            | Imitates internal transfers in EVM                     |
| `trace_block`                                    | Supported                                              |

## EVM Compatibility

| **EVM**                                          | **Details**                                            |
|--------------------------------------------------|--------------------------------------------------------|
| **EVMC Version**                                 | 10.1.0                                                 |
| **Ethereum Fork**                                | Shanghai                                               |
| **Contract Max Code Size**                       | 49152 (double of Ethereum’s max size)                  |
| **Unsupported Opcodes**                          | `BLOBHASH`, `BLOBBASEFEE` (from 4844)                  |
| **Gas Refund**                                   | Not supported for `SSTORE` and `SUICIDE` opcodes       |

## Deployed Contracts

| **Contract**                 | **Address**                                     |
|------------------------------|-------------------------------------------------|
| `RELAYHUB` gas_relay_hub      | `0x86209285bA33aecee2C3CaefEF372A2a811468A4`    |
| `MULTICALL` multicall         | `0x6cc1127612fdd0E6c7403eA4852ebb6F5AA0b6C5`    |
| `ENSREGISTRYWITHFALLBACK`     | `0x9A3d1527778d872b86241D0dEe0f269D68e52c6D`    |
| `WETH9` weth                  | `0x4cA7c59043B0D30AcF62f9cCd64BcAb0F86f2aA1`    |
| `UNISWAPV2FACTORY` uniswap_v2 | `0x7465fB21fd210b44c0c1BE5c38729B240cBE588F`    |
| `UNISWAPV2ERC20`              | `0x93F88b0Cc7FB5c2f09b8a1f37CD8Fc7615Ff3E87`    |
| `UNISWAPV2ROUTER01`           | `0x0fe20a7df3d566820dF35b9Ee2039d6dF42179e7`    |
| `UNISWAPV2ROUTER02` router    | `0x1eed0a916a87145383B71175123a0f74CB113736`    |
| `UNISWAPV2MIGRATOR` migrator  | `0xa987aC3C8520eeFc8003503Fb3977E53a022Ecf4`    |

## Metamask Support

- **Supported**: Metamask is fully supported for use with Kaon.
  
## Additional Notes

- **No Changes in Nominations**: Even though Kaon is built over Bitcoin, the denomination remains the same as Ethereum.
- **Contract Address Generation**: Uses transaction hash instead of nonce for contract creation.
- **ecrecover Support**: Fully supported.
- **Gas Refund Policy**: No gas refunds in `SSTORE` or `SUICIDE` opcodes.
