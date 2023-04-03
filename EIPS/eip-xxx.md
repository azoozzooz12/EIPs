---
eip: tbd
title: Support ENS Name for Web3 URL
description: A mapping from an ENS name to the contract address in web3://
author: Qi Zhou (@qizhou), Qiang Zhu (@qzhodl)
discussions-to: tbd
status: Draft
type: Standards Track
category: ERC
created: 2023-04-02
requires: 137, 4804
---

## Abstract

This standard defines the mapping from an name of an Ethereum name service (ENS) to an Ethereum address for EIP-4804.

## Motivation

EIP-4804 defines a `web3://`-scheme RFC 2396 URI to call a smart contract either by its address or a **name** from name service.  If a **name** is specified, the standard specifies a way to resolve the contract address from the name.

## Specification

Given **contractName** in the form of `[name "." [ subDomain0 "." ... ]] "eth"]`, the protocol will find the address of the contract using the following steps:
1. Find the `web3` text record on ENS resolver.  Return error if the record is an invalid ETH address.
2. If the `web3` text record does not exist, the protocol will use ETH address of **name**.

Note that `web3` text record may return an Ethereum address or an EIP-3770 chain-specific address.  If the address is an EIP-3770 chain-specific address, then the chainid to call the message will be overridden by the chainid specified by the EIP-3770 address.

## Security Considerations

No security considerations were found.

## Copyright

Copyright and related rights waived via [CC0](../LICENSE.md).