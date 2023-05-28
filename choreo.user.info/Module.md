## Overview

The Ballerina package "choreo.user.info" offers access to user information within Choreo. These details can be utilized to develop B2C and B2B applications effectively.

## Quickstart

To use the Ballerina package "choreo.user.info" in your Ballerina application, update the .bal file as follows:

### Step 1: Import package

1. Import the `pubudu538/choreo.user.info` module into the Ballerina project.
    ```ballerina
    import pubudu538/choreo.user.info as choreoUserInfo;
    ```

2. Add the following to the Ballerina.toml.

    ```
    [[dependency]]
    org = "pubudu538"
    name = "choreo.user.info"
    version = "0.1.1"
    ```

### Step 2: Create a new module instance

Initialize the module instance as follows.
```ballerina
choreoUserInfo:UserInfoResolver userInfoResolver = new;
```

### Step 3: Invoke the Module

1. Now you can use the operations available within the module as follows.

    ```ballerina
    service / on new http:Listener(9090) {

        # Get all doctors
        # + return - List of doctors or error
        resource function get doctors(http:Headers headers) returns Doctor[]|error? {

            choreoUserInfo:UserInfo|error userInfo = userInfoResolver.retrieveUserInfo(headers);

            if userInfo is error {
                return userInfo;
            }

            ...
        }

    }
    ```

2. Use `bal run` command to compile and run the Ballerina program.

3. Ensure that the `x-jwt-assertion` header is passed to the service, which should contain the relevant security context information, as demonstrated below.

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