# connect-ssh

Tunnel the runner's local SSH daemon to the actuated SSH gateway, with only the current user's public keys installed as they are configured on GitHub.

This action will block until you attach to the tmux session and release it by running quit, or by terminating the tmux session.

```yaml
    steps:
      - uses: self-actuated/connect-ssh@master
```

If you don't want to block until you connect, but to connect mid-way through a build, you can do with `block: false`

```yaml
    steps:
      - uses: self-actuated/connect-ssh@master
        with:
          block: false
```

If you are unable to connect with SSH in time, you could also add a short sleep:

```yaml
jobs:
  connect:
    name: connect
    runs-on: [actuated-8cpu-8gb]
    steps:
      - uses: self-actuated/connect-ssh@master
        with:
          block: false
      - run: |
          echo "Sleep for 5 minutes, since connect-ssh isn't going to block"
          sleep 500
```

