## About the image
This image is based on ubuntu 16.04 then install `openssl` and `curl`.

## How to use
- Add this script into your gitlab-ci.yml

```
before_script:
    - eval $(ssh-agent -s)
    - echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add - > /dev/null
    - echo "$SSH_KNOWN_HOSTS" > ~/.ssh/known_hosts
```

- Create variable in your gitlab project calls `SSH_PRIVATE_KEY` this will contains your runner's private key.
- Add your runner's public key into `~/.ssh/authorized_keys` on your staging/production server.
- Use this command to get the host data on your runner

```
// Use the domain name
ssh-keyscan example.com

// Or use an IP
ssh-keyscan 1.2.3.4
```

- Create variable in your gitlab project calls `SSH_KNOWN_HOSTS` use value you get from above and save.
- Then you can use your lovely custom ssh to connect to your deployment server and deploy all the stuff.
- That's about it. I hope it work, because it works on my machine. 

more information see https://docs.gitlab.com/ee/ci/ssh_keys/#ssh-keys-when-using-the-docker-executor
