# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

## Changed
- Embedd `func` compiler to package

## [0.8.7] - 2023-01-13

## Added
- `beginTailString` and `beginStringFromBuilder` for starting a `StringBuilder`
- `Slice.asString` for converting slice to a `String` (without checks of contents)

## [0.8.6] - 2023-01-10

## Fixed
- Fixing passing non-nullable type as second argument to map's `set` operation

## Changed
- New `2022.v12` func compiler

## [0.8.5] - 2023-01-09

## Changed
- Improve gas usage in `storeBool`

## [0.8.4] - 2023-01-09

## Added
-`newAddress` function to create a new address from chain and hash
-`getConfigParam` to get system configuration

## [0.8.3] - 2023-01-09

## Fixed
- Deep contract dependencies

## [0.8.2] - 2023-01-08

## Added
- `loadAddress` in `Slice`

## [0.8.1] - 2023-01-07

Fixing missing NPM release

## [0.8.0] - 2023-01-07

## Changed
- Changed message id algorithm to the one based on type signatures instead of tlb

## Added
- Dictionaries in typescript bindings
- Introduced packaging compilation step that packages a contract to a single package that can be deployed in predictable way.
- `tact-bindings` to build bindings to non-tact contracts

## [0.7.1] - 2023-01-04

## Fixed
- Assignability type checks

## [0.7.0] - 2023-01-04

## Added
- `toCell` to all structs and messages
- restored disassembler as part of a compilation flow
- `typescript` bindings parser of structs and messages

## Removed
- `abi.pack_cell` and `abi.pack_slice`

## Changed
- Updated codegen to prefix function names with a `$` to avoid clashing with system functions
- `random` and `randomInt` that are correctly initialized on first use unlike native one 
- Changed the way get and init methods expect their arguments and return values to match func-like primitives

## Fixed
- non-nullable value could break the nullable variable memory representation

## [0.6.0] - 2023-01-03

## Changed
- Large bindings generator refactoring to match new `ton-core` and `ton-emulator` packages

## Added
- `Deployable` trait in `@stdlib/deploy`

## [0.5.0] - 2022-12-23

## Added

- Constants in contracts
- Global constants
- Added `SendRemainingBalance`, `SendRemainingValue`, `SendIgnoreErrors`, `SendPayGasSeparately`, `SendDestroyIfZero` constants in stdlib
- Added `emptyCell` and `emptySlice` helpers
- Added jettons example

## Changed

- `require` now accepts two arguments, second one must be a string literal that has error message. This error message then will be exported to ABI
- Optional `Address` fields are not encoded using native representation

## [0.4.0] - 2022-12-22

### Changed
- Renamed Map's `get2` to `get` and removing `get` from keywords list.

### Fixed
- Fixed missing call arguments verification

## [0.3.0] - 2022-12-22

### Added 

- `String` literals and variables
- `Int.toString()` and `Int.toFloatString()`
- `StringBuilder` for gas-efficient string building
- Global compile-time `ton` function that conversts string to Int during compile time.
- `checkDataSignature` similar to func `check_data_signature`
- `String.asComment` for conversion text to a comment payload
- `Resumable` trait, allows to resume contract operations once it was stopped
- Comment receiver that allows to receive arbitrary comment
- `String.asSlice` cast string to a slice for parsing
- Binary shift operators `>>` and `<<`
- `Slice.fromBase64` that converts text slice that has base64 to binary representation (both classic and url)
- `Slice.asCell`, `Builder.asCell`, `Cell.asSlice`, `Builder.asCell` convenience functions
- `Slice.loadCoins` that reads coins from slice
- `myBalance` that returns current balance of a contract before execution phase

### Changed
- `contractAddress` now accepts single argument of type `StateInit` and always produces address for workchain. Old method is renamed to `contractAddressExt`.
- `hashCell` and `hashSlice` are now extension function `hash` on `Slice` and `Cell`
- Removed some keywords such as `message`, `contract`, `init` to allow use this names as variable names
- Renamed `receiveBounced` to `bounced`

### Fixed

- Fixing importing tact with providing extension, now `import "./lib";` and `import "./lib.tact";` are equivalent.
- Fixing extension function generation
- Fixing clashing of variable names with func primitives and global functions
- Fix fallback and bounce argument type resolving
- Fixed `loadUint`/`preloadUint`
- Fixed invalid generation of `>=` and `>` operators

## [0.2.0]

# Added
- `supported_interfaces` TEP support. TACT now automatically builds a list of supported interfaces of a contract
- `IPFS`-based ABI reporting. TACT now automatically calculates and embeds ABI hash into smart contract and prepares a file to upload to IPFS.
