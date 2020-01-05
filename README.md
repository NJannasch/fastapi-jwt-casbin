# fastapi-jwt-casbin
Casbin support for FastAPI using JWT


**Work in progress. Not production ready yet.**


## JWT Spec
This middleware expects an `Authorization` HTTP Header with the format `Bearer <JWT_TOKEN>`.
The Paylout must contain:
- `sub`: The Subject used in Casbin - might be a Username, ID or anything else

## Usage
```
from CasbinMiddleware import CasbinMiddleware
import casbin

....

settings = {
    'JWT_SECRET_KEY': '123',
    'JWT_ALGORITHM': '123'
}
      
enforcer = casbin.Enforcer("authz_model.conf", "authz_policy.csv")

app.add_middleware(
    CasbinMiddleware,
    settings=settings,
    enforcer=enforcer
)

```
