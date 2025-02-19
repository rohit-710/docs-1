`celocli account`
=================

Manage your account, keys, and metadata

* [`celocli account:authorize`](#celocli-accountauthorize)
* [`celocli account:balance ARG1`](#celocli-accountbalance-arg1)
* [`celocli account:claim-account ARG1`](#celocli-accountclaim-account-arg1)
* [`celocli account:claim-domain ARG1`](#celocli-accountclaim-domain-arg1)
* [`celocli account:claim-keybase ARG1`](#celocli-accountclaim-keybase-arg1)
* [`celocli account:claim-name ARG1`](#celocli-accountclaim-name-arg1)
* [`celocli account:claim-storage ARG1`](#celocli-accountclaim-storage-arg1)
* [`celocli account:create-metadata ARG1`](#celocli-accountcreate-metadata-arg1)
* [`celocli account:deauthorize`](#celocli-accountdeauthorize)
* [`celocli account:delete-payment-delegation`](#celocli-accountdelete-payment-delegation)
* [`celocli account:get-metadata ARG1`](#celocli-accountget-metadata-arg1)
* [`celocli account:get-payment-delegation`](#celocli-accountget-payment-delegation)
* [`celocli account:list`](#celocli-accountlist)
* [`celocli account:lock ARG1`](#celocli-accountlock-arg1)
* [`celocli account:new`](#celocli-accountnew)
* [`celocli account:offchain-read ARG1`](#celocli-accountoffchain-read-arg1)
* [`celocli account:offchain-write`](#celocli-accountoffchain-write)
* [`celocli account:proof-of-possession`](#celocli-accountproof-of-possession)
* [`celocli account:recover-old`](#celocli-accountrecover-old)
* [`celocli account:register`](#celocli-accountregister)
* [`celocli account:register-data-encryption-key`](#celocli-accountregister-data-encryption-key)
* [`celocli account:register-metadata`](#celocli-accountregister-metadata)
* [`celocli account:set-name`](#celocli-accountset-name)
* [`celocli account:set-payment-delegation`](#celocli-accountset-payment-delegation)
* [`celocli account:set-wallet`](#celocli-accountset-wallet)
* [`celocli account:show ARG1`](#celocli-accountshow-arg1)
* [`celocli account:show-claimed-accounts ARG1`](#celocli-accountshow-claimed-accounts-arg1)
* [`celocli account:show-metadata ARG1`](#celocli-accountshow-metadata-arg1)
* [`celocli account:unlock ARG1`](#celocli-accountunlock-arg1)
* [`celocli account:verify-proof-of-possession`](#celocli-accountverify-proof-of-possession)

## `celocli account:authorize`

Keep your locked Gold more secure by authorizing alternative keys to be used for signing attestations, voting, or validating. By doing so, you can continue to participate in the protocol while keeping the key with access to your locked Gold in cold storage. You must include a "proof-of-possession" of the key being authorized, which can be generated with the "account:proof-of-possession" command.

```
USAGE
  $ celocli account:authorize --from <value> -r vote|validator|attestation --signature
    <value> --signer <value> [--gasCurrency <value>] [--globalHelp] [--blsKey <value>
    --blsPop <value>]

FLAGS
  -r, --role=<option>
      (required) Role to delegate
      <options: vote|validator|attestation>

  --blsKey=0x
      The BLS public key that the validator is using for consensus, should pass proof of
      possession. 96 bytes.

  --blsPop=0x
      The BLS public key proof-of-possession, which consists of a signature on the account
      address. 48 bytes.

  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d
      (required) Account Address

  --gasCurrency=0x1234567890123456789012345678901234567890
      Use a specific gas currency for transaction fees (defaults to CELO if no gas
      currency is supplied). It must be a whitelisted token.

  --globalHelp
      View all available global flags

  --signature=0x
      (required) Signature (a.k.a proof-of-possession) of the signer key

  --signer=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d
      (required) Account Address

DESCRIPTION
  Keep your locked Gold more secure by authorizing alternative keys to be used for
  signing attestations, voting, or validating. By doing so, you can continue to
  participate in the protocol while keeping the key with access to your locked Gold in
  cold storage. You must include a "proof-of-possession" of the key being authorized,
  which can be generated with the "account:proof-of-possession" command.

EXAMPLES
  authorize --from 0x5409ED021D9299bf6814279A6A1411A7e866A631 --role vote --signer 0x6ecbe1db9ef729cbe972c83fb886247691fb6beb --signature 0x1b9fca4bbb5bfb1dbe69ef1cddbd9b4202dcb6b134c5170611e1e36ecfa468d7b46c85328d504934fce6c2a1571603a50ae224d2b32685e84d4d1a1eebad8452eb

  authorize --from 0x5409ED021D9299bf6814279A6A1411A7e866A631 --role validator --signer 0x6ecbe1db9ef729cbe972c83fb886247691fb6beb --signature 0x1b9fca4bbb5bfb1dbe69ef1cddbd9b4202dcb6b134c5170611e1e36ecfa468d7b46c85328d504934fce6c2a1571603a50ae224d2b32685e84d4d1a1eebad8452eb --blsKey 0x4fa3f67fc913878b068d1fa1cdddc54913d3bf988dbe5a36a20fa888f20d4894c408a6773f3d7bde11154f2a3076b700d345a42fd25a0e5e83f4db5586ac7979ac2053cd95d8f2efd3e959571ceccaa743e02cf4be3f5d7aaddb0b06fc9aff00 --blsPop 0xcdb77255037eb68897cd487fdd85388cbda448f617f874449d4b11588b0b7ad8ddc20d9bb450b513bb35664ea3923900
```

_See code: [src/commands/account/authorize.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/authorize.ts)_

## `celocli account:balance ARG1`

View Celo Stables and CELO balances for an address

```
USAGE
  $ celocli account:balance ARG1 [--gasCurrency <value>] [--globalHelp]
    [--erc20Address <value>]

FLAGS
  --erc20Address=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d
      Address of generic ERC-20 token to also check balance for

  --gasCurrency=0x1234567890123456789012345678901234567890
      Use a specific gas currency for transaction fees (defaults to CELO if no gas
      currency is supplied). It must be a whitelisted token.

  --globalHelp
      View all available global flags

DESCRIPTION
  View Celo Stables and CELO balances for an address

EXAMPLES
  balance 0x5409ed021d9299bf6814279a6a1411a7e866a631

  balance 0x5409ed021d9299bf6814279a6a1411a7e866a631 --erc20Address 0x765DE816845861e75A25fCA122bb6898B8B1282a
```

_See code: [src/commands/account/balance.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/balance.ts)_

## `celocli account:claim-account ARG1`

Claim another account, and optionally its public key, and add the claim to a local metadata file

```
USAGE
  $ celocli account:claim-account ARG1 --from <value> --address <value> [--gasCurrency
    <value>] [--globalHelp] [--publicKey <value>]

ARGUMENTS
  ARG1  Path of the metadata file

FLAGS
  --address=<value>                                         (required) The address of
                                                            the account you want to
                                                            claim
  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d         (required) Address of the
                                                            account to set metadata for
                                                            or an authorized signer for
                                                            the address in the metadata
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --publicKey=<value>                                       The public key of the
                                                            account that others may use
                                                            to send you encrypted
                                                            messages

DESCRIPTION
  Claim another account, and optionally its public key, and add the claim to a local
  metadata file

EXAMPLES
  claim-account ~/metadata.json --address 0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d --from 0x47e172F6CfB6c7D01C1574fa3E2Be7CC73269D95
```

_See code: [src/commands/account/claim-account.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/claim-account.ts)_

## `celocli account:claim-domain ARG1`

Claim a domain and add the claim to a local metadata file

```
USAGE
  $ celocli account:claim-domain ARG1 --from <value> --domain <value> [--gasCurrency
    <value>] [--globalHelp]

ARGUMENTS
  ARG1  Path of the metadata file

FLAGS
  --domain=<value>                                          (required) The domain you
                                                            want to claim
  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d         (required) Address of the
                                                            account to set metadata for
                                                            or an authorized signer for
                                                            the address in the metadata
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags

DESCRIPTION
  Claim a domain and add the claim to a local metadata file

EXAMPLES
  claim-domain ~/metadata.json --domain example.com --from 0x47e172F6CfB6c7D01C1574fa3E2Be7CC73269D95
```

_See code: [src/commands/account/claim-domain.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/claim-domain.ts)_

## `celocli account:claim-keybase ARG1`

Claim a keybase username and add the claim to a local metadata file

```
USAGE
  $ celocli account:claim-keybase ARG1 --from <value> --username <value> [--gasCurrency
    <value>] [--globalHelp]

ARGUMENTS
  ARG1  Path of the metadata file

FLAGS
  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d         (required) Address of the
                                                            account to set metadata for
                                                            or an authorized signer for
                                                            the address in the metadata
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --username=<value>                                        (required) The keybase
                                                            username you want to claim

DESCRIPTION
  Claim a keybase username and add the claim to a local metadata file

EXAMPLES
  claim-keybase ~/metadata.json --from 0x47e172F6CfB6c7D01C1574fa3E2Be7CC73269D95 --username myusername
```

_See code: [src/commands/account/claim-keybase.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/claim-keybase.ts)_

## `celocli account:claim-name ARG1`

Claim a name and add the claim to a local metadata file

```
USAGE
  $ celocli account:claim-name ARG1 --from <value> --name <value> [--gasCurrency
    <value>] [--globalHelp]

ARGUMENTS
  ARG1  Path of the metadata file

FLAGS
  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d         (required) Address of the
                                                            account to set metadata for
                                                            or an authorized signer for
                                                            the address in the metadata
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --name=<value>                                            (required) The name you want
                                                            to claim

DESCRIPTION
  Claim a name and add the claim to a local metadata file

EXAMPLES
  claim-name ~/metadata.json --from 0x47e172F6CfB6c7D01C1574fa3E2Be7CC73269D95 --name myname
```

_See code: [src/commands/account/claim-name.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/claim-name.ts)_

## `celocli account:claim-storage ARG1`

Claim a storage root and add the claim to a local metadata file

```
USAGE
  $ celocli account:claim-storage ARG1 --from <value> --url <value> [--gasCurrency <value>]
    [--globalHelp]

ARGUMENTS
  ARG1  Path of the metadata file

FLAGS
  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d         (required) Address of the
                                                            account to set metadata for
                                                            or an authorized signer for
                                                            the address in the metadata
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --url=https://www.celo.org                                (required) The URL of the
                                                            storage root you want to
                                                            claim

DESCRIPTION
  Claim a storage root and add the claim to a local metadata file

EXAMPLES
  claim-storage ~/metadata.json --url http://example.com/myurl --from 0x47e172F6CfB6c7D01C1574fa3E2Be7CC73269D95
```

_See code: [src/commands/account/claim-storage.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/claim-storage.ts)_

## `celocli account:create-metadata ARG1`

Create an empty identity metadata file. Use this metadata file to store claims attesting to ownership of off-chain resources. Claims can be generated with the account:claim-* commands.

```
USAGE
  $ celocli account:create-metadata ARG1 --from <value> [--gasCurrency <value>]
  [--globalHelp]

ARGUMENTS
  ARG1  Path where the metadata should be saved

FLAGS
  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d         (required) Address of the
                                                            account to set metadata for
                                                            or an authorized signer for
                                                            the address in the metadata
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags

DESCRIPTION
  Create an empty identity metadata file. Use this metadata file to store claims
  attesting to ownership of off-chain resources. Claims can be generated with the
  account:claim-* commands.

EXAMPLES
  create-metadata ~/metadata.json --from 0x47e172F6CfB6c7D01C1574fa3E2Be7CC73269D95
```

_See code: [src/commands/account/create-metadata.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/create-metadata.ts)_

## `celocli account:deauthorize`

Remove an account's authorized attestation signer role.

```
USAGE
  $ celocli account:deauthorize --from <value> -r attestation --signer <value>
    [--gasCurrency <value>] [--globalHelp]

FLAGS
  -r, --role=<option>
      (required) Role to remove
      <options: attestation>

  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d
      (required) Account Address

  --gasCurrency=0x1234567890123456789012345678901234567890
      Use a specific gas currency for transaction fees (defaults to CELO if no gas
      currency is supplied). It must be a whitelisted token.

  --globalHelp
      View all available global flags

  --signer=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d
      (required) Account Address

DESCRIPTION
  Remove an account's authorized attestation signer role.

EXAMPLES
  deauthorize --from 0x5409ED021D9299bf6814279A6A1411A7e866A631 --role attestation --signer 0x6ecbe1db9ef729cbe972c83fb886247691fb6beb
```

_See code: [src/commands/account/deauthorize.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/deauthorize.ts)_

## `celocli account:delete-payment-delegation`

Removes a validator's payment delegation by setting beneficiary and fraction to 0.

```
USAGE
  $ celocli account:delete-payment-delegation --account <value> [--gasCurrency <value>]
  [--globalHelp]

FLAGS
  --account=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d      (required) Account Address
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags

DESCRIPTION
  Removes a validator's payment delegation by setting benficiary and fraction to 0.

EXAMPLES
  delete-payment-delegation --account 0x5409ED021D9299bf6814279A6A1411A7e866A631
```

_See code: [src/commands/account/delete-payment-delegation.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/delete-payment-delegation.ts)_

## `celocli account:get-metadata ARG1`

Show information about an address. Retrieves the metadata URL for an account from the on-chain, then fetches the metadata file off-chain and verifies proofs as able.

```
USAGE
  $ celocli account:get-metadata ARG1 [--gasCurrency <value>] [--globalHelp] [--columns
    <value> | -x] [--filter <value>] [--no-header | [--csv | --no-truncate]] [--output
    csv|json|yaml |  | ] [--sort <value>]

ARGUMENTS
  ARG1  Address to get metadata for

FLAGS
  -x, --extended
      show extra columns

  --columns=<value>
      only show provided columns (comma-separated)

  --csv
      output is csv format [alias: --output=csv]

  --filter=<value>
      filter property by partial string matching, ex: name=foo

  --gasCurrency=0x1234567890123456789012345678901234567890
      Use a specific gas currency for transaction fees (defaults to CELO if no gas
      currency is supplied). It must be a whitelisted token.

  --globalHelp
      View all available global flags

  --no-header
      hide table header from output

  --no-truncate
      do not truncate output to fit screen

  --output=<option>
      output in a more machine friendly format
      <options: csv|json|yaml>

  --sort=<value>
      property to sort by (prepend '-' for descending)

DESCRIPTION
  Show information about an address. Retrieves the metadata URL for an account from the
  on-chain, then fetches the metadata file off-chain and verifies proofs as able.

EXAMPLES
  get-metadata 0x97f7333c51897469E8D98E7af8653aAb468050a3
```

_See code: [src/commands/account/get-metadata.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/get-metadata.ts)_

## `celocli account:get-payment-delegation`

Get the payment delegation account beneficiary and fraction allocated from a validator's payment each epoch. The fraction cannot be greater than 1.

```
USAGE
  $ celocli account:get-payment-delegation --account <value> [--gasCurrency <value>] [--globalHelp]
    [--columns <value> | -x] [--filter <value>] [--no-header | [--csv | --no-truncate]]
    [--output csv|json|yaml |  | ] [--sort <value>]

FLAGS
  -x, --extended
      show extra columns

  --account=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d
      (required) Account Address

  --columns=<value>
      only show provided columns (comma-separated)

  --csv
      output is csv format [alias: --output=csv]

  --filter=<value>
      filter property by partial string matching, ex: name=foo

  --gasCurrency=0x1234567890123456789012345678901234567890
      Use a specific gas currency for transaction fees (defaults to CELO if no gas
      currency is supplied). It must be a whitelisted token.

  --globalHelp
      View all available global flags

  --no-header
      hide table header from output

  --no-truncate
      do not truncate output to fit screen

  --output=<option>
      output in a more machine friendly format
      <options: csv|json|yaml>

  --sort=<value>
      property to sort by (prepend '-' for descending)

DESCRIPTION
  Get the payment delegation account beneficiary and fraction allocated from a
  validator's payment each epoch. The fraction cannot be greater than 1.

EXAMPLES
  get-payment-delegation --account 0x5409ed021d9299bf6814279a6a1411a7e866a631
```

_See code: [src/commands/account/get-payment-delegation.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/get-payment-delegation.ts)_

## `celocli account:list`

List the addresses from the node and the local instance

```
USAGE
  $ celocli account:list [--gasCurrency <value>] [--globalHelp] [--local]

FLAGS
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --[no-]local                                              If set, only show local and
                                                            hardware wallet accounts.
                                                            Use no-local to only show
                                                            keystore addresses.

DESCRIPTION
  List the addresses from the node and the local instance
```

_See code: [src/commands/account/list.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/list.ts)_

## `celocli account:lock ARG1`

Lock an account which was previously unlocked

```
USAGE
  $ celocli account:lock ARG1 [--gasCurrency <value>] [--globalHelp]

ARGUMENTS
  ARG1  Account address

FLAGS
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags

DESCRIPTION
  Lock an account which was previously unlocked

EXAMPLES
  lock 0x5409ed021d9299bf6814279a6a1411a7e866a631
```

_See code: [src/commands/account/lock.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/lock.ts)_

## `celocli account:new`

Creates a new account locally using the Celo Derivation Path (m/44'/52752'/0/changeIndex/addressIndex) and print out the key information. Save this information for local transaction signing or import into a Celo node. Ledger: this command has been tested swapping mnemonics with the Ledger successfully (only supports english)

```
USAGE
  $ celocli account:new [--gasCurrency <value>] [--globalHelp] [--passphrasePath
    <value>] [--changeIndex <value>] [--addressIndex <value>] [--language chinese_simpli
    fied|chinese_traditional|english|french|italian|japanese|korean|spanish]
    [--mnemonicPath <value>] [--derivationPath <value>]

FLAGS
  --addressIndex=<value>
      Choose the address index for the derivation path

  --changeIndex=<value>
      Choose the change index for the derivation path

  --derivationPath=<value>
      Choose a different derivation Path (Celo's default is "m/44'/52752'/0'"). Use "eth"
      as an alias of the Ethereum derivation path ("m/44'/60'/0'"). Recreating the same
      account requires knowledge of the mnemonic, passphrase (if any), and the derivation
      path

  --gasCurrency=0x1234567890123456789012345678901234567890
      Use a specific gas currency for transaction fees (defaults to CELO if no gas
      currency is supplied). It must be a whitelisted token.

  --globalHelp
      View all available global flags

  --language=<option>
      [default: english] Language for the mnemonic words. **WARNING**, some hardware
      wallets don't support other languages
      <options: chinese_simplified|chinese_traditional|english|french|italian|japanese|kor
      ean|spanish>

  --mnemonicPath=<value>
      Instead of generating a new mnemonic (seed phrase), use the user-supplied mnemonic
      instead. Path to a file that contains all the mnemonic words separated by a space
      (example: "word1 word2 word3 ... word24"). If the words are a language other than
      English, the --language flag must be used. Only BIP39 mnemonics are supported

  --passphrasePath=<value>
      Path to a file that contains the BIP39 passphrase to combine with the mnemonic
      specified using the mnemonicPath flag and the index specified using the addressIndex
      flag. Every passphrase generates a different private key and wallet address.

DESCRIPTION
  Creates a new account locally using the Celo Derivation Path
  (m/44'/52752'/0/changeIndex/addressIndex) and print out the key information. Save this
  information for local transaction signing or import into a Celo node. Ledger: this
  command has been tested swapping mnemonics with the Ledger successfully (only supports
  english)

EXAMPLES
  new

  new --passphrasePath myFolder/my_passphrase_file

  new --language spanish

  new --passphrasePath some_folder/my_passphrase_file --language japanese --addressIndex 5

  new --passphrasePath some_folder/my_passphrase_file --mnemonicPath some_folder/my_mnemonic_file --addressIndex 5
```

_See code: [src/commands/account/new.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/new.ts)_

## `celocli account:offchain-read ARG1`

DEV: Reads the name from offchain storage

```
USAGE
  $ celocli account:offchain-read ARG1 [--gasCurrency <value>] [--globalHelp] [--directory
    <value>] [--bucket <value> --provider git|aws|gcp] [--from <value>] [--privateDEK
    <value>]

FLAGS
  --bucket=<value>                                          If using a GCP or AWS
                                                            storage bucket this
                                                            parameter is required
  --directory=<value>                                       [default: .] To which
                                                            directory data should be
                                                            written
  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d         Account Address
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --privateDEK=<value>
  --provider=<option>                                       If the CLI should attempt to
                                                            push to the cloud
                                                            <options: git|aws|gcp>

DESCRIPTION
  DEV: Reads the name from offchain storage

EXAMPLES
  offchain-read 0x...

  offchain-read 0x... --from 0x... --privateKey 0x...
```

_See code: [src/commands/account/offchain-read.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/offchain-read.ts)_

## `celocli account:offchain-write`

DEV: Writes a name to offchain storage

```
USAGE
  $ celocli account:offchain-write --name <value> [--gasCurrency <value>] [--globalHelp]
    [--directory <value>] [--bucket <value> --provider git|aws|gcp] (--privateDEK
    <value> --privateKey <value> --encryptTo <value>)

FLAGS
  --bucket=<value>                                          If using a GCP or AWS
                                                            storage bucket this
                                                            parameter is required
  --directory=<value>                                       [default: .] To which
                                                            directory data should be
                                                            written
  --encryptTo=<value>
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --name=<value>                                            (required)
  --privateDEK=<value>
  --privateKey=<value>                                      (required)
  --provider=<option>                                       If the CLI should attempt to
                                                            push to the cloud
                                                            <options: git|aws|gcp>

DESCRIPTION
  DEV: Writes a name to offchain storage

EXAMPLES
  offchain-write --name test-account --privateKey 0x...

  offchain-write --name test-account --privateKey 0x...  privateDEK 0x... --encryptTo 0x...
```

_See code: [src/commands/account/offchain-write.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/offchain-write.ts)_

## `celocli account:proof-of-possession`

Generate proof-of-possession to be used to authorize a signer. See the "account:authorize" command for more details.

```
USAGE
  $ celocli account:proof-of-possession --signer <value> --account <value> [--gasCurrency
    <value>] [--globalHelp]

FLAGS
  --account=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d      (required) Address of the
                                                            account that needs to prove
                                                            possession of the signer
                                                            key.
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --signer=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d       (required) Address of the
                                                            signer key to prove
                                                            possession of.

DESCRIPTION
  Generate proof-of-possession to be used to authorize a signer. See the
  "account:authorize" command for more details.

EXAMPLES
  proof-of-possession --account 0x5409ed021d9299bf6814279a6a1411a7e866a631 --signer 0x6ecbe1db9ef729cbe972c83fb886247691fb6beb
```

_See code: [src/commands/account/proof-of-possession.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/proof-of-possession.ts)_

## `celocli account:recover-old`

Recovers the Valora old account and print out the key information. The old Valora app (in a beta state) generated the user address using a seed of 32 bytes, instead of 64 bytes. As the app fixed that, some old accounts were left with some funds. This command allows the user to recover those funds.

```
USAGE
  $ celocli account:recover-old --mnemonicPath <value> [--gasCurrency <value>]
    [--globalHelp] [--passphrasePath <value>] [--changeIndex <value>] [--addressIndex
    <value>] [--language chinese_simplified|chinese_traditional|english|french|italian|j
    apanese|korean|spanish] [--derivationPath <value>]

FLAGS
  --addressIndex=<value>
      Choose the address index for the derivation path

  --changeIndex=<value>
      Choose the change index for the derivation path

  --derivationPath=<value>
      Choose a different derivation Path (Celo's default is "m/44'/52752'/0'"). Use "eth"
      as an alias of the Ethereum derivation path ("m/44'/60'/0'"). Recreating the same
      account requires knowledge of the mnemonic, passphrase (if any), and the derivation
      path

  --gasCurrency=0x1234567890123456789012345678901234567890
      Use a specific gas currency for transaction fees (defaults to CELO if no gas
      currency is supplied). It must be a whitelisted token.

  --globalHelp
      View all available global flags

  --language=<option>
      [default: english] Language for the mnemonic words. **WARNING**, some hardware
      wallets don't support other languages
      <options: chinese_simplified|chinese_traditional|english|french|italian|japanese|kor
      ean|spanish>

  --mnemonicPath=<value>
      (required) Path to a file that contains all the mnemonic words separated by a space
      (example: "word1 word2 word3 ... word24"). If the words are a language other than
      English, the --language flag must be used. Only BIP39 mnemonics are supported

  --passphrasePath=<value>
      Path to a file that contains the BIP39 passphrase to combine with the mnemonic
      specified using the mnemonicPath flag and the index specified using the addressIndex
      flag. Every passphrase generates a different private key and wallet address.

DESCRIPTION
  Recovers the Valora old account and print out the key information. The old Valora app
  (in a beta state) generated the user address using a seed of 32 bytes, instead of 64
  bytes. As the app fixed that, some old accounts were left with some funds. This
  command allows the user to recover those funds.

EXAMPLES
  recover-old --mnemonicPath some_folder/my_mnemonic_file

  recover-old --mnemonicPath some_folder/my_mnemonic_file --passphrasePath myFolder/my_passphrase_file

  recover-old --mnemonicPath some_folder/my_mnemonic_file --language spanish

  recover-old --mnemonicPath some_folder/my_mnemonic_file --passphrasePath some_folder/my_passphrase_file --language japanese --addressIndex 5

  recover-old --mnemonicPath some_folder/my_mnemonic_file --passphrasePath some_folder/my_passphrase_file --addressIndex 5
```

_See code: [src/commands/account/recover-old.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/recover-old.ts)_

## `celocli account:register`

Register an account on-chain. This allows you to lock Gold, which is a pre-requisite for registering a Validator or Group, participating in Validator elections and on-chain Governance, and earning epoch rewards.

```
USAGE
  $ celocli account:register --from <value> [--gasCurrency <value>] [--globalHelp]
    [--name <value>]

FLAGS
  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d         (required) Account Address
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --name=<value>

DESCRIPTION
  Register an account on-chain. This allows you to lock Gold, which is a pre-requisite
  for registering a Validator or Group, participating in Validator elections and
  on-chain Governance, and earning epoch rewards.

EXAMPLES
  register --from 0x5409ed021d9299bf6814279a6a1411a7e866a631

  register --from 0x5409ed021d9299bf6814279a6a1411a7e866a631 --name test-account
```

_See code: [src/commands/account/register.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/register.ts)_

## `celocli account:register-data-encryption-key`

Register a data encryption key for an account on chain. This key can be used to encrypt data to you such as offchain metadata or transaction comments

```
USAGE
  $ celocli account:register-data-encryption-key --from <value> --publicKey <value> [--gasCurrency
    <value>] [--globalHelp]

FLAGS
  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d         (required) Addess of the
                                                            account to set the data
                                                            encryption key for
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --publicKey=<value>                                       (required) The public key
                                                            you want to register

DESCRIPTION
  Register a data encryption key for an account on chain. This key can be used to
  encrypt data to you such as offchain metadata or transaction comments

EXAMPLES
  register-data-encryption-key --publicKey 0x...  --from 0x47e172F6CfB6c7D01C1574fa3E2Be7CC73269D95
```

_See code: [src/commands/account/register-data-encryption-key.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/register-data-encryption-key.ts)_

## `celocli account:register-metadata`

Register metadata URL for an account where users will be able to retieve the metadata file and verify your claims

```
USAGE
  $ celocli account:register-metadata --from <value> --url <value> [--gasCurrency <value>]
    [--globalHelp] [--force] [--columns <value> | -x] [--filter <value>] [--no-header |
    [--csv | --no-truncate]] [--output csv|json|yaml |  | ] [--sort <value>]

FLAGS
  -x, --extended
      show extra columns

  --columns=<value>
      only show provided columns (comma-separated)

  --csv
      output is csv format [alias: --output=csv]

  --filter=<value>
      filter property by partial string matching, ex: name=foo

  --force
      Ignore metadata validity checks

  --from=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d
      (required) Addess of the account to set metadata for

  --gasCurrency=0x1234567890123456789012345678901234567890
      Use a specific gas currency for transaction fees (defaults to CELO if no gas
      currency is supplied). It must be a whitelisted token.

  --globalHelp
      View all available global flags

  --no-header
      hide table header from output

  --no-truncate
      do not truncate output to fit screen

  --output=<option>
      output in a more machine friendly format
      <options: csv|json|yaml>

  --sort=<value>
      property to sort by (prepend '-' for descending)

  --url=<value>
      (required) The url to the metadata you want to register

DESCRIPTION
  Register metadata URL for an account where users will be able to retieve the metadata
  file and verify your claims

EXAMPLES
  register-metadata --url https://www.mywebsite.com/celo-metadata --from 0x47e172F6CfB6c7D01C1574fa3E2Be7CC73269D95
```

_See code: [src/commands/account/register-metadata.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/register-metadata.ts)_

## `celocli account:set-name`

Sets the name of a registered account on-chain. An account's name is an optional human readable identifier

```
USAGE
  $ celocli account:set-name --account <value> --name <value> [--gasCurrency <value>]
    [--globalHelp]

FLAGS
  --account=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d      (required) Account Address
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --name=<value>                                            (required)

DESCRIPTION
  Sets the name of a registered account on-chain. An account's name is an optional human
  readable identifier

EXAMPLES
  set-name --account 0x5409ed021d9299bf6814279a6a1411a7e866a631 --name test-account
```

_See code: [src/commands/account/set-name.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/set-name.ts)_

## `celocli account:set-payment-delegation`

Sets a payment delegation beneficiary, an account address to receive a fraction of the validator's payment every epoch. The fraction must not be greater than 1.

```
USAGE
  $ celocli account:set-payment-delegation --account <value> --beneficiary <value> --fraction
    <value> [--gasCurrency <value>] [--globalHelp]

FLAGS
  --account=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d      (required) Account Address
  --beneficiary=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d  (required) Account Address
  --fraction=<value>                                        (required)
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags

DESCRIPTION
  Sets a payment delegation beneficiary, an account address to receive a fraction of the
  validator's payment every epoch. The fraction must not be greater than 1.

EXAMPLES
  set-payment-delegation --account 0x5409ed021d9299bf6814279a6a1411a7e866a631 --beneficiary 0x6Ecbe1DB9EF729CBe972C83Fb886247691Fb6beb --fraction 0.1
```

_See code: [src/commands/account/set-payment-delegation.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/set-payment-delegation.ts)_

## `celocli account:set-wallet`

Sets the wallet of a registered account on-chain. An account's wallet is an optional wallet associated with an account. Can be set by the account or an account's signer.

```
USAGE
  $ celocli account:set-wallet --account <value> --wallet <value> [--gasCurrency
    <value>] [--globalHelp] [--signature <value>] [--signer <value>]

FLAGS
  --account=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d      (required) Account Address
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --signature=0x                                            Signature (a.k.a.
                                                            proof-of-possession) of the
                                                            signer key
  --signer=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d       Address of the signer key to
                                                            verify proof of possession.
  --wallet=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d       (required) Account Address

DESCRIPTION
  Sets the wallet of a registered account on-chain. An account's wallet is an optional
  wallet associated with an account. Can be set by the account or an account's signer.

EXAMPLES
  set-wallet --account 0x5409ed021d9299bf6814279a6a1411a7e866a631 --wallet 0x5409ed021d9299bf6814279a6a1411a7e866a631

  set-wallet --account 0x5409ed021d9299bf6814279a6a1411a7e866a631 --wallet 0x5409ed021d9299bf6814279a6a1411a7e866a631 --signer 0x0EdeDF7B1287f07db348997663EeEb283D70aBE7 --signature 0x1c5efaa1f7ca6484d49ccce76217e2fba0552c0b23462cff7ba646473bc2717ffc4ce45be89bd5be9b5d23305e87fc2896808467c4081d9524a84c01b89ec91ca3
```

_See code: [src/commands/account/set-wallet.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/set-wallet.ts)_

## `celocli account:show ARG1`

Show information for an account, including name, authorized vote, validator, and attestation signers, the URL at which account metadata is hosted, the address the account is using with the mobile wallet, and a public key that can be used to encrypt information for the account.

```
USAGE
  $ celocli account:show ARG1 [--gasCurrency <value>] [--globalHelp]

FLAGS
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags

DESCRIPTION
  Show information for an account, including name, authorized vote, validator, and
  attestation signers, the URL at which account metadata is hosted, the address the
  account is using with the mobile wallet, and a public key that can be used to encrypt
  information for the account.

EXAMPLES
  show 0x5409ed021d9299bf6814279a6a1411a7e866a631
```

_See code: [src/commands/account/show.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/show.ts)_

## `celocli account:show-claimed-accounts ARG1`

Show information about claimed accounts

```
USAGE
  $ celocli account:show-claimed-accounts ARG1 [--gasCurrency <value>] [--globalHelp]

FLAGS
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags

DESCRIPTION
  Show information about claimed accounts

EXAMPLES
  show-claimed-accounts 0x5409ed021d9299bf6814279a6a1411a7e866a631
```

_See code: [src/commands/account/show-claimed-accounts.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/show-claimed-accounts.ts)_

## `celocli account:show-metadata ARG1`

Show the data in a local metadata file

```
USAGE
  $ celocli account:show-metadata ARG1 [--gasCurrency <value>] [--globalHelp] [--columns
    <value> | -x] [--filter <value>] [--no-header | [--csv | --no-truncate]] [--output
    csv|json|yaml |  | ] [--sort <value>]

ARGUMENTS
  ARG1  Path of the metadata file

FLAGS
  -x, --extended
      show extra columns

  --columns=<value>
      only show provided columns (comma-separated)

  --csv
      output is csv format [alias: --output=csv]

  --filter=<value>
      filter property by partial string matching, ex: name=foo

  --gasCurrency=0x1234567890123456789012345678901234567890
      Use a specific gas currency for transaction fees (defaults to CELO if no gas
      currency is supplied). It must be a whitelisted token.

  --globalHelp
      View all available global flags

  --no-header
      hide table header from output

  --no-truncate
      do not truncate output to fit screen

  --output=<option>
      output in a more machine friendly format
      <options: csv|json|yaml>

  --sort=<value>
      property to sort by (prepend '-' for descending)

DESCRIPTION
  Show the data in a local metadata file

EXAMPLES
  show-metadata ~/metadata.json
```

_See code: [src/commands/account/show-metadata.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/show-metadata.ts)_

## `celocli account:unlock ARG1`

Unlock an account address to send transactions or validate blocks

```
USAGE
  $ celocli account:unlock ARG1 [--gasCurrency <value>] [--globalHelp] [--password
    <value>] [--duration <value>]

ARGUMENTS
  ARG1  Account address

FLAGS
  --duration=<value>                                        Duration in seconds to leave
                                                            the account unlocked.
                                                            Unlocks until the node exits
                                                            by default.
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --password=<value>                                        Password used to unlock the
                                                            account. If not specified,
                                                            you will be prompted for a
                                                            password.

DESCRIPTION
  Unlock an account address to send transactions or validate blocks

EXAMPLES
  unlock 0x5409ed021d9299bf6814279a6a1411a7e866a631

  unlock 0x5409ed021d9299bf6814279a6a1411a7e866a631 --duration 600
```

_See code: [src/commands/account/unlock.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/unlock.ts)_

## `celocli account:verify-proof-of-possession`

Verify a proof-of-possession. See the "account:proof-of-possession" command for more details.

```
USAGE
  $ celocli account:verify-proof-of-possession --signer <value> --account <value> --signature <value>
    [--gasCurrency <value>] [--globalHelp]

FLAGS
  --account=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d      (required) Address of the
                                                            account that needs to prove
                                                            possession of the signer
                                                            key.
  --gasCurrency=0x1234567890123456789012345678901234567890  Use a specific gas currency
                                                            for transaction fees
                                                            (defaults to CELO if no gas
                                                            currency is supplied). It
                                                            must be a whitelisted token.
  --globalHelp                                              View all available global
                                                            flags
  --signature=0x                                            (required) Signature (a.k.a.
                                                            proof-of-possession) of the
                                                            signer key
  --signer=0xc1912fEE45d61C87Cc5EA59DaE31190FFFFf232d       (required) Address of the
                                                            signer key to verify proof
                                                            of possession.

DESCRIPTION
  Verify a proof-of-possession. See the "account:proof-of-possession" command for more
  details.

EXAMPLES
  verify-proof-of-possession --account 0x199eDF79ABCa29A2Fa4014882d3C13dC191A5B58 --signer 0x0EdeDF7B1287f07db348997663EeEb283D70aBE7 --signature 0x1c5efaa1f7ca6484d49ccce76217e2fba0552c0b23462cff7ba646473bc2717ffc4ce45be89bd5be9b5d23305e87fc2896808467c4081d9524a84c01b89ec91ca3
```

_See code: [src/commands/account/verify-proof-of-possession.ts](https://github.com/celo-org/developer-tooling/tree/master/packages/cli/src/commands/account/verify-proof-of-possession.ts)_
