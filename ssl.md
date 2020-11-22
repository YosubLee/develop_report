## OpenSSL
**OpenSSL**은 네트워크를 통한 데이터 통신에 쓰이는 프로토콜인 TLS와 SSL의 오픈 소스 구현판이다. 

## 유용한 명령어 
인증서 만료일 확인

````bash
openssl x509 -enddate -noout -in {경로}.crt
````

## 참조
<https://ko.wikipedia.org/wiki/OpenSSL>