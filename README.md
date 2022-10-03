# upload-maven-packages

Add the following environment variables:

```
GITHUB_USERNAME
GITHUB_TOKEN
```

If you are attempting to use github actions runner to upload, the GITHUB_TOKEN will be generated by actions
make sure that the token has the right permissions, please refer to:

https://docs.github.com/en/actions/security-guides/automatic-token-authentication

Publish the artifact with
```
./gradlew publish
```

## Running behind corporate proxy

If your proxy does a malware check, it might unpack the cert and repack with its own CA.
On macbook, go to keychain and identify the CA cert of the proxy, and export it to your device, and then run the following

```
echo yes | keytool -importcert -alias <alias> -trustcacerts -storepass changeit -file <pathToCertificate> -keystore cacerts
```

Confrim that its added by running the following:

```
keytool -keystore cacerts -storepass changeit -list | grep <alias>
```

The first line of the gradle properties file is commented, uncomment it and then proceed to test gradle publish.

