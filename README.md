# ssh-agent-proxy

Transparently create a proxy to SSH agent socket.

## Usage

Start ssh-agent and have environment variable `SSH_AUTH_SOCK` defined.

Then run a command (typically docker run) that requires a SSH agent socket.

```
ssh-auth-proxy -- docker run --rm -it \
    -v $SSH_AUTH_SOCK:$SSH_AUTH_SOCK \
    -e SSH_AUTH_SOCK=$SSH_AUTH_SOCK \
    --user ubuntu:ubuntu \
      ubuntu bash
```

## Options

- `-u`: UID of the proxy socket owner (default: 1000)
- `-s`: File path of the proxy socket (default: `$SSH_AUTH_SOCK.uid-$UID`)
