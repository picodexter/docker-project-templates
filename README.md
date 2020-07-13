# Docker Project Templates

## Overview

This is a personal collection of opinionated templates for different kinds of Docker Compose setups to facilitate
local development.

## Additional Notes

### Inconsistent Connections to GPG Key Servers

When trying to receive a key from a GPG key server, sometimes it will fail with the following error:

```
gpg: keyserver receive failed: Cannot assign requested address
```

As this is something that happens due to the availability / reliability of the key servers themselves, I opted for a
workaround that keeps the key as a file and imports it from there:

1.  Receive key manually.

1.  Export key via
    ```shell script
    gpg --armor --export 0xKEYID > key.gpg
    ```
    with `0xKEYID` being the key ID of the key you received. 

1.  Move the key file into the Docker context of the image (Dockerfile directory or subdirectory).

1.  Change Dockerfile to get those file contents and import key from there instead:

    ```dockerfile
    COPY key.gpg /tmp/key.gpg
    
    RUN gpg --import /tmp/key.gpg \
        && rm /tmp/key.gpg
    ```

## Author

*   picodexter | [GitHub](https://github.com/picodexter) | [picodexter.io](https://picodexter.io/)
