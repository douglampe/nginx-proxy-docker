A fork of [jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy) to enable the new docker networking interface.
Used bits from [schmunk's](https://github.com/schmunk42) comment [here](https://github.com/jwilder/nginx-proxy/issues/304#issuecomment-161437752).

### Usage

To run it:

    $ docker run -d -p 80:80 -v /var/run/docker.sock:/tmp/docker.sock:ro vassilvk/nginx-proxy

Then start any containers you want proxied with an env var `VIRTUAL_HOST=subdomain.youdomain.com` and `VIRTUAL_NETWORK=true`

    $ docker run -e VIRTUAL_HOST=foo.bar.com -e VIRTUAL_NETWORK=true ...

Note that the rest of the functionality covered by [jwilder/nginx-proxy](https://github.com/jwilder/nginx-proxy) is the same including the ability to pin to specific `VIRTUAL_PORT`s.