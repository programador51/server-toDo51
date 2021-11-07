A simple To-Do RESTful API.

## Installation

```bash
$ npm install
```

## Running the app

```bash
# development
$ npm run start

# watch mode
$ npm run start:dev

# production mode
$ npm run start:prod
```

## Test

```bash
# unit tests
$ npm run test

# e2e tests
$ npm run test:e2e

# test coverage
$ npm run test:cov
```

---

## Notes

Ignore this, are just notes of what i practiced on this project (which was learn nestjs once know express.js) to remember it on the future. (For the `programador51` of the future). Small pieces of code and concepts.

---

**Installation**
Easy, the [docs](https://docs.nestjs.com/first-steps) tell very clearly how to create the structure of the project.

---

**Controllers**
They manage the request in order to return `something` on the response, but the logic of the service and that are managed separetly. Concepts are [here](https://docs.nestjs.com/controllers).

Instance, a method `GET` **EXECUTES** services in order to do `something` and return the desire date.

```typescript
@Controller('cats')
export class CatsController {
  @Get()
  findAll(): string {
    return 'This action returns all cats';
  }
}
```

Other things as

- headers
- status code
- redirection
- query params
- params query
- body
- etc...

Are managed here

---

**Providers**
Services, repositories, factories, helpers.

**Services**
Re-usable code for any part of my aplication, for instance, retrieve data from database

```typescript
import { Injectable } from '@nestjs/common';
import { Cat } from './interfaces/cat.interface';

@Injectable()
export class CatsService {
  private readonly cats: Cat[] = [];

  create(cat: Cat) {
    this.cats.push(cat);
  }

  findAll(): Cat[] {
    return this.cats;
  }
}
```

---

**Create folder structure**

This it's an example of how must be structured the folder

```
-- src
    |-- cats
    |   |-- dto
    |   |   `-- create-cat.dto.ts
    |   |-- interfaces
    |   |   `-- cat.interface.ts
    |   |-- cats.controller.ts
    |   `-- cats.service.ts
    |-- app.module.ts
    `-- main.ts
```

Can be generated manually creating the folders and files (using the same guideline of nestjs) or with cli. The commands are [here](https://docs.nestjs.com/cli/usages#nest-generate)

---

**Modules**
It's a set of providers, controllers , imports and exports of related code. For instance, a feature `chat` will contain only the necessary to make `work` a chat functionality, nothing related to `login`, `stamp invoices` , etc.

More info [here](https://docs.nestjs.com/modules)

---

**Middleware**
Code that execute before the `Controller` executes. Works to validate for example, a JWT.

---

**Exception filters**
The erros can be handled with this concept. The nice thing it's that they're pre-build errors to handle this.
**[List of HTTP Exceptions](https://docs.nestjs.com/exception-filters#built-in-http-exceptions)**

---

**Pipes**
They validate de DTO before execute the services and transforms the data before they execute on any part of the module. For instance,
when you receive the data before arrives to the controller or before the service sends the information, you probably add something else before controller response the request.
More info [here](https://docs.nestjs.com/pipes#built-in-pipes)

---

**Guards**
They determine what request can be handled or rejected according the circustances.

Authentication , roles , etc.

More info [here](https://docs.nestjs.com/guards)