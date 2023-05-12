# connect-ssh

Tunnel the runner's local SSH daemon to the actuated SSH gateway, with only the current user's public keys installed as they are configured on GitHub.

```yaml
    steps:
      - uses: self-actuated/connect-ssh@master
```