# Configure dev environment

> Doc WIP

## Install puma-dev

Follow puma-dev guide on [https://github.com/puma/puma-dev](github.com/puma/puma-dev)

```sh
# Zerologin instance
echo 3333 > ~/.puma-dev/zerologin
# Webpack server
echo 8081 > ~/.puma-dev/webpack.zerologin

# Optional
# Client
echo 3000 > ~/.puma-dev/zl-client 
# Client zerologin domain
echo 3333 > ~/.puma-dev/login.zl-client
# Client zerologin webpack server domain
echo 8081 > ~/.puma-dev/webpack.login.zl-client
```

Every sites are available under `https://*.test` domain. Certificate must be trusted (self signed by puma-dev)