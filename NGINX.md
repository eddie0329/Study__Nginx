## What is Nginx?

`Nginx`는 차세대 웹서버로써 `Apache`를 대응 하는 관계이다. 더 적은 자원으로 더 빠르게 데이터를 서비스 할 수 있다는 장점이 있다.

## Nginx Commands

```
// stop
// -s means send signal
nginx -s stop

// start
nginx

// reload
nginx -s reload

// test
nginx -t
```

If `nginx -s stop` cannot kill the pid, then follow as:

```
sudo nginx -c /usr/local/etc/nginx/nginx.conf
sudo nginx -s stop
```

## Basic Syntax of Nginx

There will be bolier plate for Nginx in localhost:80

```nginx
http {
  server {
    listen 80
  }
}
```

If you want to serve `html` file, follow as:

```nginx
http {
  server {
    listen 80
    # index.html file path
    root /Users/choejongsun/nginxcourse/;
  }
}
```

If the root directory as follow:

```
root
--index.html
--site1
|__index.html
--site2
|__index.html
```

You can load site 1 and 2 by `/size1` or `/site2`.

### Different location

```
root
--index.html
--site1
|__index.html
--site2
|__index.html
```

```
images
--trees.png
```

Nginx Syntax:

```nginx
http {
  server {
    listen 80;
    root /Users/choejongsun/nginxcourse/;
    location /images {
      root /Users/choejongsun/;
    }
  }
}
```
`localhost:80/images` will show an error page.

However!!! `localhost:80/images/trees.png` will show image.


### Forbid location

``` nginx
# anything match end of `jpg` (ex> hello.jpg)
location ~ .jpg$ {
  return 403;
}
```

// TODO: NEED TO START https://www.youtube.com/watch?v=WC2-hNNBWII&t=1098s at 30:30;