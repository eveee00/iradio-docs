---
title: (TCM) Ports
layout: default
parent: TCM Radio
nav_order: 2
---

## 80
  - Identifies itself as "magic iradio"
  - Runs the API to control the device through the app. API uses [basic auth](https://github.com/edberoi/python-airmusicapi?tab=readme-ov-file#authentication) and the password should be the same on every device.
  - Apparently, on some older models, [no auth was required](https://github.com/edberoi/python-airmusicapi?tab=readme-ov-file#authentication) to use the API. This isn't the case for my device though.

## 8080
  - Uses the same authentication as port 80
  - Webserver serving /UIData
  - Data stored in .bin files (most likely bitmaps)
  - cURL errors out:
    
    ```bash
    $ curl -H 'Authorization: Basic c3UzZzRnbzZzazc6amkzOTQ1NHh1L14=' http://192.168.178.95:8080
    curl: (1) Received HTTP/0.9 when not allowed
    ```
  - You can actually view this in the browser, though it will error out:

    ```html
    can't open 'index.html'
    HTTP/1.0 404 Not Found
    Content-type: text/html
    Date: Sat, 23 Aug 2025 00:04:51 GMT
    Connection: close

    <HTML><HEAD><TITLE>404 Not Found</TITLE></HEAD>
    <BODY><H1>404 Not Found</H1>
    The requested URL was not found
    </BODY></HTML>
    ```
