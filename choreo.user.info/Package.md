Retrieve user information in [Choreo](https://wso2.com/choreo/).

# Package Overview

The Ballerina package "choreo.user.info" offers access to user information within Choreo. These details can be utilized to develop B2C and B2B applications effectively.

# How to use the Package

In order to use this package, follow the following steps.

1. Add the following import to your Ballerina program.

    ```
    import pubudu538/choreo.user.info as choreoUserInfo;
    ```

2. Add the following to the Ballerina.toml when building your program.

    ```
    [[dependency]]
    org = "pubudu538"
    name = "choreo.user.info"
    version = "0.1.1"
    ```

3. Create a Service and enable `Pass Security Context To Backend` in Choreo. 

4. Ensure that the `x-jwt-assertion` header is passed to the service, which should contain the relevant security context information, as demonstrated below.

```
{
  "sub": "testsub-e3d2-4d21-bbd4-e107922d2098",
  "http://wso2.org/claims/apiname": "testapi",
  "user_organization": "testorg-6e15-43be-abe8-2fdb6b999917",
  "http://wso2.org/claims/applicationtier": "10PerMin",
  "http://wso2.org/claims/version": "1.0.0",
  "http://wso2.org/claims/keytype": "PRODUCTION",
  "iss": "wso2.org/products/am",
  "http://wso2.org/claims/applicationname": "local-app",
  "http://wso2.org/claims/enduserTenantId": "0",
  "http://wso2.org/claims/applicationUUId": "testapp-c80d-4a10-918f-0b5074838d88",
  "client_id": "testclientid-xxx1-xx1",
  "http://wso2.org/claims/subscriber": "testsub1-366f-45df-a8cd-7af169a67ff2",
  "azp": "testclientid-xxx1-xx1",
  "http://wso2.org/claims/tier": "Bronze",
  "scope": "email groups openid profile",
  "exp": 1684391985,
  "http://wso2.org/claims/applicationid": "testapp-c80d-4a10-918f-0b5074838d88",
  "http://wso2.org/claims/usertype": "Application_User",
  "iat": 1684388385,
  "email": "testuser@test.com",
  "groups": [
    "doctor","admin"
  ],
  "jti": "a5c374fc-8768-496d-dddd-97f5d4c677be",
  "http://wso2.org/claims/apicontext": "/testorg-ecc2-jkjkk-97e9-f804d09c35ac/testdd/testvwe/1.0.0"
}
```