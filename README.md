# smat_ESP8266
Show Me a Thing files for the ESP8266 WiFi Module

## Making a POST Request Using AT Commands

```bash
# softAP+station mode
AT+CWMODE=3

# SSID and password of router
AT+CWJAP="SSID","password"

# Connect to Heroku Server
AT+CIPSTART: "TCP","swms-data-service.herokuapp.com",80

# Send data to test Port
AT+CIPSEND=4				# Length of Data

# Raw Header, treat as string with escaped characters
POST /test/postData HTTP/1.1\r\nHost: swms-data-service.herokuapp.com\r\nContent-Type: application/x-www-form-urlencoded\r\nContent-Length: 12\r\n\r\ntestData=800\r\n\r\n

# PUT requests to /test/firebaseWrite
PUT /test/firebaseWrite HTTP/1.1\r\nHost: swms-data-service.herokuapp.com\r\nContent-Type: application/x-www-form-urlencoded\r\nContent-Length: 0\r\n\r\n

# GET request to /test
GET /test HTTP/1.1\r\nHost: swms-data-service.herokuapp.com\r\n\r\n

# POST request to /test
POST /test HTTP/1.1\r\nHost: swms-data-service.herokuapp.com\r\nContent-Type: application/json\r\nContent-Length: 0\r\n\r\n
```
Without escaped characters, the raw HTTP request looks like this:
```
POST /test/postData HTTP/1.1
Host: swms-data-service.herokuapp.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 12

testData=800
```

I used [this tool to test and format the HTTP requests](https://reqbin.com/). The response should be another raw HTTP request. For example, the GET request to /test looks like:
```
HTTP/1.1 200 OK
Server: Cowboy
Connection: keep-alive
X-Powered-By: Express
Access-Control-Allow-Origin: *
Content-Type: text/html; charset=utf-8
Content-Length: 22
Etag: W/"16-rwolR9z+YSTpVSa3ck2MG2sSlRs"
Date: Wed, 22 Apr 2020 20:32:01 GMT
Via: 1.1 vegur

GET request to /test
```
