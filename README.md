<a name="module_mali-toobject"></a>

### mali-toobject
Mali <code>toObject</code> middleware. If the response object has a <code>toObject</code> function it's executed
upon payload. Only applies for <code>UNARY</code> and <code>REQUEST_STREAM</code> call types.

**Example**  

```js
const toObject = require('mali-toobject')

function handler(ctx) {
  const obj = {
    email: 'bob@gmail.com',
    password: 'mysecret'
  }

  obj.toObject = function() {
    return {
      email: this.email
    }
  }

  ctx.res = obj // password will not be in the payload to client
}

app.use('fn', toObject, handler)
```

