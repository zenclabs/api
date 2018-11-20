Spot
===

**Spot** (*"Single Point Of Truth"*) is a concise, developer-friendly way to describe your API contract.

Leveraging the TypeScript syntax, it lets you describe your API and generate any other API contract formats you need (OpenAPI, Swagger, JSON Schema, Pact, API Blueprint), client SDKs (TypeScript, Swift, Kotlin) or even server boilerplate (e.g. Express).

You don't need to use TypeScript in your codebase to benefit from using Spot.

Example of an API definition file `api.ts` which defines a single `POST` endpoint to create a user:
```typescript
import { api, endpoint, request } from "@zenclabs/spot";

@api()
class Api {
  @endpoint({
    method: "POST",
    path: "/users"
  })
  createUser(@request req: CreateUserRequest): CreateUserResponse {
    throw "contract";
  }
}

interface CreateUserRequest {
  firstName: string;
  lastName: string;
}

interface CreateUserResponse {
  success: boolean;
}
```

You can pass the definition above to a generator by simply running:
```sh
npx @zenclabs/spot generate --api api.ts
```

This is work in progress as of 14 Nov 2018:
- [x] Functional TypeScript DSL
- [x] Support for multiple files (using import statements)
- [x] OpenAPI 3 generator
- [x] OpenAPI 2 generator
- [x] JSON Schema generator
- [ ] Pact generator
- [ ] API Blueprint generator
- [x] TypeScript axios-based client generator
- [x] TypeScript express-based server boilerplate generator

[![oclif](https://img.shields.io/badge/cli-oclif-brightgreen.svg)](https://oclif.io)
[![Version](https://img.shields.io/npm/v/@zenclabs/spot.svg)](https://npmjs.org/package/@zenclabs/spot)
[![CircleCI](https://circleci.com/gh/zenclabs/spot/tree/master.svg?style=shield)](https://circleci.com/gh/zenclabs/spot/tree/master)
[![Downloads/week](https://img.shields.io/npm/dw/@zenclabs/spot.svg)](https://npmjs.org/package/@zenclabs/spot)
[![License](https://img.shields.io/npm/l/@zenclabs/spot.svg)](https://github.com/zenclabs/spot/blob/master/package.json)

<!-- toc -->
* [Usage](#usage)
* [Commands](#commands)
<!-- tocstop -->
# Usage

To get started and set up an API declaration in the current directory, run:
```
npx @zenclabs/spot init
```

You can then run a generator with:
```
npx @zenclabs/spot generate --api api.ts
```

# Commands
<!-- commands -->
* [`spot help [COMMAND]`](#spot-help-command)

## `spot help [COMMAND]`

display help for spot

```
USAGE
  $ spot help [COMMAND]

ARGUMENTS
  COMMAND  command to show help for

OPTIONS
  --all  see all commands in CLI
```

_See code: [@oclif/plugin-help](https://github.com/oclif/plugin-help/blob/v2.1.3/src/commands/help.ts)_
<!-- commandsstop -->