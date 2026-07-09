# pully-canary-secret

Pure-Python canary HTTP service that binds a **unix socket** and answers
`GET /health`. It reads `DRACON_SECRET` from the environment, which is injected
by systemd via an `EnvironmentFile` pointing at the warden-decrypted
`/var/lib/pully-fleet/secrets/canary.env`. The service reports healthy only
when the secret is present, proving the warden-encrypted secret is decrypted on
the node and available to the running service at runtime.
