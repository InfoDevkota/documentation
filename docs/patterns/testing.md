# Testing
Creating a unit test in Elysia is easy.

You can use `bun:test` to create a unit test with Elysia.

Elysia instance has a `handle` method that accepts `Request` and will return a `Response`, the same as creating an HTTP request.

```typescript
import { describe, expect, it } from 'bun:test'

describe('Elysia', () => {
    it('return a response', async () => {
        const app = new Elysia()
              .get('/', () => 'hi')

        const response = await app.handle(
            new Request('http://localhost/')
        ).then(res => res.text())

        expect(response).toBe('hi')
    })
})
```

You can also use other testing library like Jest to create a unit test for Elysia, but we recommended to use `bun:test` over others.

::: tip
When creating a Request to Elysia server, Elysia expect an entire valid URL **NOT** a part of an URL. 

For instance, "http://localhost/" is valid but "/user" is not.
:::