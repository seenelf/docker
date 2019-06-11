## About the image
This image is based on alpine:3.8 then install `openssl`, `curl`, `zip` and `rsync`.

## How to use
- Add before_script into your gitlab-ci.yml (your deploy job)
- Add private_key that can use to access to server into gitlab project variable calls SSH_PRIVATE_KEY
- Add ssh-keyscan result into gitlab project variable calls SSH_KNOWN_HOSTS

```
before_script:
    - eval $(ssh-agent -s)
    - echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add - > /dev/null
    - echo "$SSH_KNOWN_HOSTS" > ~/.ssh/known_hosts
```

```
// Use the domain name
ssh-keyscan example.com

// Or use an IP
ssh-keyscan 1.2.3.4
```

## Example
```
 before_script:
    - eval $(ssh-agent -s)
    - echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add - > /dev/null
    - echo "$SSH_KNOWN_HOSTS" > ~/.ssh/known_hosts
  script:
    - ssh deploy@{{ SERVER_DOMAIN_NAME }} "cd {{ PROJECT_PATH }} && git checkout . && git pull && exit"
```

more information see https://docs.gitlab.com/ee/ci/ssh_keys/#ssh-keys-when-using-the-docker-executor
