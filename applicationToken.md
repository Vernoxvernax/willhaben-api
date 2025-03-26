
## Creating the applicationTokenRequest payload:

An application token is used to provide access to the api.

To get one of those tokens, the willhaben app sends an applicationTokenRequest payload to the api.

It contains a signature to verify the request (`HMACSHA1`), but is generated purely locally, and thus is very easy to replicate.

```json
{
  "applicationTokenRequest": {
    "organization": "api@tailored-apps.com",
    "salt": "pepper",
    "signature": "Z3oPR7ae9zSeMRITr516PDSWfoc=",
    "timestamp": "1970-01-01T01:00:01+0100"
  }
}
```

This json body contains the following information about the `JWT`:
* `organization` - used in the android app; didn't check for limitations when modifying this
* `salt` - try: base64(a random 12-byte array) catch: "d7Z34msd8d9v34G"
* `timestamp` - this is preferrably the current timestamp in ISO8601; not strictly enforced as long as it's not in the future

**`signature` Recipe:**

1. Generate a new string like this:
  ```python
    message = salt + ";" + timestamp + ";" + organization
  ```
2. Generate the HMAC hash using *a* key and the message:
  ```python
    hmacsha1 = hmac.new(b64decode(b'JDJhJDEwJHFUd2lnSFoyclJqQ2pSS3dQLlM2Vy4='), message.encode('utf-8'), hashlib.sha1)
  ```
3. Get the signature as `base64`:
  ```python
    signature = b64encode(hmacsha1.digest().decode('utf-8'))
  ```

Here is a small proof-of-concept Willhaben api-library: https://github.com/Vernoxvernax/willhaben-api-rs
