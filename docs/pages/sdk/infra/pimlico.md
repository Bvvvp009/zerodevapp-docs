# Pimlico

[Pimlico](https://www.pimlico.io/) is a leading AA infra provider with a wide coverage of networks.

Note that ZeroDev is built on top of Pimlico's [Permissionless](https://docs.pimlico.io/permissionless/reference) SDK, so if you were already using Permissionless, it's easy to switch to ZeroDev to take full advantage of the power of [Kernel](https://github.com/zerodevapp/kernel).

## Using Pimlico bundler

Simply specify Pimlico's bundler RPC when [constructing a Kernel client](/sdk/core-api/create-account#standard-api):

```typescript
import { createKernelAccountClient } from "@zerodev/sdk"
import { http } from "viem"

const kernelClient = createKernelAccountClient({
  // other options...

  transport: http('PIMLICO_BUNDLER_RPC'),
})
```

## Using Pimlico paymaster

Construct the Kernel client with Pimlico's paymaster client:

```typescript
import { http } from "viem"
import { polygonMumbai } from 'viem/chains'
import { createKernelAccountClient } from "@zerodev/sdk"
import { createPaymasterClient } from 'viem/account-abstraction'

const paymaster = createPaymasterClient({
  chain: polygonMumbai,
  transport: http('PIMLICO_PAYMASTER_RPC'),
})

const kernelClient = createKernelAccountClient({
  account,
  chain: polygonMumbai,
  bundlerTransport: http('PIMLICO_BUNDLER_RPC'),
  paymaster
})
```