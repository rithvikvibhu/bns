# bns

DNS library and validating recursive resolver for node.js, in pure javascript.

## Example

``` bash
$ dig.js --recursive www.ietf.org +dnssec +debug
Querying www.ietf.org./A.
Switching authority: (hints.local.)
Switching zone: [.]
Querying server: 2001:500:12::d0d (38470)
Verifying zone change to [.]
Checking signatures...
Querying server: 199.7.83.42 (14617)
Validated DNSSEC signatures.
Switching authority: (b2.org.afilias-nst.org.)
Switching zone: [.->org.]
Querying server: 199.19.54.1 (4434)
Verifying zone change to [org.]
Checking signatures...
Querying server: 199.19.54.1 (42051)
Validated DNSSEC signatures.
Looking up NS: ns1.ams1.afilias-nst.info.
Looking up IPv6 nameserver for ns1.ams1.afilias-nst.info....
Querying ns1.ams1.afilias-nst.info./AAAA.
Switching authority: (hints.local.)
Switching zone: [.]
Querying server: 192.33.4.12 (26984)
Verifying zone change to [.]
Checking signatures...
Cache hit for ./DNSKEY.
Validated DNSSEC signatures.
Switching authority: (b2.info.afilias-nst.org.)
Switching zone: [.->info.]
Querying server: 2001:500:1b::1 (19432)
Verifying zone change to [info.]
Checking signatures...
Querying server: 2001:500:1c::1 (48266)
Validated DNSSEC signatures.
Validated NSEC3 delegation.
Switching authority: (d0.dig.afilias-nst.info.)
Switching zone: [info.->afilias-nst.info.]
Trust chain broken due to zone change.
Querying server: 2a01:8840:7::1 (14155)
Traversed zones: ., info., afilias-nst.info. for ns1.ams1.afilias-nst.info./AAAA.
IPv6 nameserver lookup failed: No authority address.
Looking up IPv4 nameserver for ns1.ams1.afilias-nst.info....
Querying ns1.ams1.afilias-nst.info./A.
Switching authority: (hints.local.)
Switching zone: [.]
Querying server: 198.97.190.53 (56951)
Verifying zone change to [.]
Checking signatures...
Cache hit for ./DNSKEY.
Validated DNSSEC signatures.
Switching authority: (a0.info.afilias-nst.info.)
Switching zone: [.->info.]
Querying server: 2001:500:1b::1 (17528)
Verifying zone change to [info.]
Checking signatures...
Cache hit for info./DNSKEY.
Validated DNSSEC signatures.
Validated NSEC3 delegation.
Switching authority: (c0.dig.afilias-nst.info.)
Switching zone: [info.->afilias-nst.info.]
Trust chain broken due to zone change.
Querying server: 2a01:8840:9::1 (29803)
Traversed zones: ., info., afilias-nst.info. for ns1.ams1.afilias-nst.info./A.
Picked nameserver for: ns1.ams1.afilias-nst.info.
Switching authority: (ns1.ams1.afilias-nst.info.)
Switching zone: [org.->ietf.org.]
Querying server: 65.22.6.79 (39603)
Verifying zone change to [ietf.org.]
Checking signatures...
Querying server: 65.22.6.79 (6831)
Validated DNSSEC signatures.
Found alias to: www.ietf.org.cdn.cloudflare.net.
Alias changing zone: [ietf.org.->.]
Querying server: 192.36.148.17 (56154)
Verifying zone change to [.]
Checking signatures...
Cache hit for ./DNSKEY.
Validated DNSSEC signatures.
Switching authority: (m.gtld-servers.net.)
Switching zone: [.->net.]
Querying server: 192.35.51.30 (45165)
Verifying zone change to [net.]
Checking signatures...
Querying server: 192.48.79.30 (17999)
Validated DNSSEC signatures.
Switching authority: (ns2.cloudflare.net.)
Switching zone: [net.->cloudflare.net.]
Querying server: 2400:cb00:2049:1::adf5:3b1f (32228)
Verifying zone change to [cloudflare.net.]
Checking signatures...
Querying server: 2400:cb00:2049:1::adf5:3b1f (4323)
Validated DNSSEC signatures.
Traversed zones: ., org., ietf.org., ., net., cloudflare.net. for www.ietf.org./A.
Finishing resolving www.ietf.org./A (hops=10).

; <<>> dig.js 0.0.12 <<>> --recursive www.ietf.org +dnssec +debug
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 32228
;; flags: qr ra ad; QUERY: 1, ANSWER: 5, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags: do; udp: 512
;; QUESTION SECTION:
;www.ietf.org. IN A

;; ANSWER SECTION:
www.ietf.org. 1800 IN CNAME www.ietf.org.cdn.cloudflare.net.
www.ietf.org. 1800 IN RRSIG CNAME 5 3 1800 20190214160829 20180214150920 40452 ietf.org. OAS6hbpld1KpNJBpqg/T+0m0FpcVV933AbsDuVlgloHQfyVG4Ug5iOtK QLKGNYw+583Ba1yhFlFsYu4GNALZFpF8Tw5NcmxpmXJyzpeO0aj1rSCH oFQzYaIszrbw7TmE2pYQbh9QeklO9hILxi/Q1D7VxzrtHj0Ff8ncgFI7 6Ep+ud0Gysr0m/5MrwO69LGPV06LTuMRP3cXv7hqbjmyn2CmYR3h6+lQ +uiHSwkZYK20xhk+w1pOP9CD6fIqGYCJiKVaMY8K2lMQyi6Ppx0zOmtk MdaJjnxrzQ5TXbCcGQ48Rn4hzdug1MvkJzh1DGWZH6ZnPQTEf3+O1ehz +zSpbQ==  ; alg = RSASHA1
www.ietf.org.cdn.cloudflare.net. 300 IN A 104.20.1.85
www.ietf.org.cdn.cloudflare.net. 300 IN A 104.20.0.85
www.ietf.org.cdn.cloudflare.net. 300 IN RRSIG A 13 6 300 20180406144148 20180404124148 35273 cloudflare.net. FUGqNUw+9Jb2Z/qJGByi2vBfzuS/X0tNbhtXMsboazqbYu5C/UlGch3u Uez482xYdVbm/+YeBy5Bu2vWKVtbsw==  ; alg = ECDSAP256SHA256

;; Query time: 1168 msec
;; WHEN: Thu Apr 05 06:41:30 PDT 2018
;; MSG SIZE  rcvd: 202
```

## Usage

``` js
const bns = require('bns');
```

## Contribution and License Agreement

If you contribute code to this project, you are implicitly allowing your code
to be distributed under the MIT license. You are also implicitly verifying that
all code is your original work. `</legalese>`

## License

- Copyright (c) 2017, Christopher Jeffrey (MIT License).

See LICENSE for more info.
