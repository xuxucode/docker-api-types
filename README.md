# Docker/Moby API types

This package only contains TypeScript declaration files.
In case you do not want to introduce `effect-ts` in your project, only need the TypeScript types for API parameters and return types.

See https://github.com/leonitousconforti/the-moby-effect for full functional REST API.

## Examples

```ts
import type { MobyEndpoints, MobySchemas } from 'docker-api-types'
import { toURLSearchParams } from './utils'

export type ContainerListOptions = NonNullable<Parameters<MobyEndpoints.Containers['list']>[0]>

export async function listContainers(params?: ContainerListOptions): Promise<MobySchemas.ContainerSummary[] | undefined> {
  const queryParams = toURLSearchParams(params)
  const response = await fetch(`/containers/json?${queryParams}`)
  if (response.ok) {
    return await response.json() as MobySchemas.ContainerSummary[]
  }
}
```

## Credits
Huge thanks to [Leo Conforti](https://github.com/leonitousconforti) 👍
