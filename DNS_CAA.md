DNS CAA

CAA is Certificate Authority Authorization

Unfortunately, sometimes publicly trusted certificate authority fails to validate the 
legitmatecy of the certificate requester. [Example](https://venturebeat.com/security/google-security-temporarily-compromised-by-fake-digital-certificates/)

DNS CAA record is a additional layer using DNS to reclare which certificate authority
should be allowed to issue certificate for the domain. 

Tool
* https://www.entrust.com/resources/certificate-solutions/tools/caa-lookup
* dig `dig caa cloudflare.com`

Example

```
; <<>> DiG 9.10.6 <<>> caa cloudflare.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 15271
;; flags: qr rd ra ad; QUERY: 1, ANSWER: 9, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 1232
;; QUESTION SECTION:
;cloudflare.com.			IN	CAA

;; ANSWER SECTION:
cloudflare.com.		300	IN	CAA	0 issue "digicert.com; cansignhttpexchanges=yes"
cloudflare.com.		300	IN	CAA	0 issuewild "digicert.com; cansignhttpexchanges=yes"
cloudflare.com.		300	IN	CAA	0 issuewild "pki.goog; cansignhttpexchanges=yes"
cloudflare.com.		300	IN	CAA	0 iodef "mailto:tls-abuse@cloudflare.com"
cloudflare.com.		300	IN	CAA	0 issue "pki.goog; cansignhttpexchanges=yes"
cloudflare.com.		300	IN	CAA	0 issue "comodoca.com"
cloudflare.com.		300	IN	CAA	0 issue "letsencrypt.org"
cloudflare.com.		300	IN	CAA	0 issuewild "comodoca.com"
cloudflare.com.		300	IN	CAA	0 issuewild "letsencrypt.org"
```
