+++
date = "2017-03-17T10:33:30Z"
title = "Life Cycle of Cryptographic Material"
draft = true
+++

Everything which communicates securely will typically maintain some sensitive data. It may be a passphrase or a cryptographic key. How long does this need to remain in existence? What are the risks of public exposure? This post will attempt to discuss and answer these questions.

A typical life cycle of cryptographic material follows this structure:

1. Generate
2. Exchange
3. Use
4. Renew
5. Expire
6. Dispose

The amount of time a key is in use depends on the cryptographic protocol, and what it is used for. GPG keys can last for years, where as LetsEncrypt's TLS keys will last for a maximum on 90 days. One reason for this is that GPG resides on your laptop and TLS on a public server. Your laptop should be physically guarded by you and less likely to be compromised compared to a server. A server which you do not have physical access to and is hosted on shared multitenented hardware. To combat this, TLS and others support [forward secrecy](https://en.wikipedia.org/wiki/Forward_secrecy), which is designed to prevent decryption of passed communication if the private key is comprised. 

### So what do you do with long lived keys which do not support forward secrecy?

Perhaps treating them like passwords are the answer. Frequently renewing and using unique keys for each service. Yes and no. If possible you might want to renew keys if you believe they have been compromised, this might not be easy. With GPG you'd have to re-enforce your web of trust. Making sure you contacts are aware of the change and will update their systems. Typically, you'd want to do this if you are 80%~ sure they have been compromised. What you do want to do is use unique keys for each service, but again this will only be advantageous if the keys are stored on remote on less 'secured' machines. This will allow you to revoke and renew only keys select keys and to reduce the scope of a single key used everywhere. 

- Why does it matter/Is it important?
	- All depends on your threat model. 
	- Don't care, I use something better!
		- TPM
		- YubiKey

- What has been done before?
	- <https://www.cryptomathic.com/news-events/blog/key-management-the-life-cycles-of-a-cryptographic-key>
	- "Towards Understanding the Lifetime of Cryptographic Keys: the Case of Apache" May 2005

## Applied applications

- Quick review of the life cycle of key material by these protocols:
	- OTR
	- Double Ratchet Algorithm (Variations of it; Signal Protocol, OMEMO)
		- <https://en.wikipedia.org/wiki/Double_Ratchet_Algorithm>
	- GPG
	- TLS
	- SSH
		- [Uber's SSH Certificate Authority](https://medium.com/uber-security-privacy/introducing-the-uber-ssh-certificate-authority-4f840839c5cc)

## Follow up reading

- DNSSEC KSK Ceremony 22
- <https://en.wikipedia.org/wiki/Public_key_infrastructure>