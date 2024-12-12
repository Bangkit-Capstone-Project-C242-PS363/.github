# Auth Services

## Register
```http
POST https://signmaster-auth-kji5w4ybbq-et.a.run.app/auth/register
Content-Type: application/json

{
    "username": "test",
    "email": "test@test.com",
    "password": "123456789",
    "confirmPassword": "123456789"
}
```

## Login
```http
POST https://signmaster-auth-kji5w4ybbq-et.a.run.app/auth/login
Content-Type: application/json

{
    "email": "test@test.com",
    "password": "123456789"
}
```
