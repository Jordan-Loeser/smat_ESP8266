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
POST /test/postData HTTP/1.1\r\n Host: swms-data-service.herokuapp.com\r\n Content-Type: application/x-www-form-urlencoded\r\ nContent-Length: 12\r\n\r\n testData=800\r\n

# Another, Simpler Raw PUT Header
PUT /test/firebaseWrite HTTP/1.1\r\n Host: swms-data-service.herokuapp.com\r\n Content-Type: application/x-www-form-urlencoded\r\n Content-Length: 0\r\n
```
Without escaped characters, the raw HTTP request looks like this:
```
POST /test/postData HTTP/1.1
Host: swms-data-service.herokuapp.com
Content-Type: application/x-www-form-urlencoded
Content-Length: 12

testData=800
```
