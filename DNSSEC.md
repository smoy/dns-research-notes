DNSSEC

Typical DNS UDP query doesn't have a signature mechanims. DNSSEC is a protocol to allow
recursive resolver to verify DNS record has not been tampered using a chain of trust. 

Meaning, from the root, to TLD, to your domain, there is a chain of asymmetric crytography
to verify the contents of the DNS record. I recommend you deploy DNSSEC early to avoid
headache later on.

[Slack’s DNSSEC Rollout: Third Time’s the Outage](https://www.youtube.com/watch?v=zU8hTL55-8I)
is a tale on Slack run into difficult to deploy DNSSEC when they already have a large online
prescence. 

Other secure DNS techniques (like DNS CAA) require DNSSEC; otherwise, recursive resolver
is subject to poison (since regular DNS has no signature mechanism to prove the contents
has not been tampered with). 

Tools
* https://dnssec-analyzer.verisignlabs.com
