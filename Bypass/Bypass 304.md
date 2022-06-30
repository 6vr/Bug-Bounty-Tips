# Bypass 304 (Not Modified)

1. Delete "If-None-Match" header
```
GET /admin HTTP/1.1
Host: target.com
If-None-Match: W/"32-IuK7rSIJ92ka0c92kld"
```
Try this to bypass
```
GET /admin HTTP/1.1
Host: target.com
```

2. Adding random character in the end of "If-None-Match" header
```
GET /admin HTTP/1.1
Host: target.com
If-None-Match: W/"32-IuK7rSIJ92ka0c92kld"
```
Try this to bypass
```
GET /admin HTTP/1.1
Host: target.com
Host: target.com
If-None-Match: W/"32-IuK7rSIJ92ka0c92kld" b
```

