# Fulu -- Builder Specification

## Table of Contents

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->

- [Introduction](#introduction)
- [Containers](#containers)
  - [Extended containers](#extended-containers)
    - [`BlobsBundle`](#blobsbundle)
    - [`ExecutionPayloadHeader`](#executionpayloadheader)
    - [`ExecutionPayloadAndBlobsBundle`](#executionpayloadandblobsbundle)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Introduction

This is the modification of the builder specification accompanying the Fulu upgrade.

## Containers

### Extended containers

#### `BlobsBundle`

```python
class BlobsBundle(Container):
    commitments: List[KZGCommitment, MAX_BLOB_COMMITMENTS_PER_BLOCK]
    # [Modified in Fulu:EIP7594]
    proofs: List[KZGProof, FIELD_ELEMENTS_PER_EXT_BLOB * MAX_BLOB_COMMITMENTS_PER_BLOCK]
    blobs: List[Blob, MAX_BLOB_COMMITMENTS_PER_BLOCK]
```

### `ExecutionPayloadHeader`

See [`ExecutionPayloadHeader`](https://github.com/ethereum/consensus-specs/blob/dev/specs/deneb/beacon-chain.md#executionpayloadheader) in Deneb consensus specs.

#### `ExecutionPayloadAndBlobsBundle`

```python
class ExecutionPayloadAndBlobsBundle(Container):
    execution_payload: ExecutionPayload
    blobs_bundle: BlobsBundle  # [Modified in Fulu:EIP7594]
```