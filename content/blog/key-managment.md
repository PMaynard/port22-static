+++
date = "2017-03-17T10:33:30Z"
title = "Key Management"
draft = true
+++

[Key management](https://en.wikipedia.org/wiki/Key_management) is critical to the security of a cryptosystem. This typically involves generating, exchanging, storing and day to day use of keys. It is often defined within the cryptographic protocol itself. 

Keys must be generated on a secure platform, if this is not the case then it is impossible to achieve any form of private communication. For sure this will depend on you your threat model. It might be fit well within your model to generate and store your keys on a multi tenant machine, with which you have no access. Either way, keys will need to maintain secret at least from some parties. So should be stored in a secure location after and during generation.
this
Before secured communication is established, key exchange has to be accomplished. Depending on the type of cryptographic system used (symmetric or asymmetric keys[^1]), the --security-- of the key exchange process can be varied. For example, GPG and SSH allows you to exchange public keys which anyone can view. It is down to the end user to verify that they have the correct public key. This is normally done via a web of trust, where you check with many trusted persons that the public key in question is identical.

Once the exchange is complete, and optionally the identity of the other end verified, it is time for secure communication.

- Explain a bit about key revocation.
        - GPG, SSL CA's
        - LetsEncrypt will regenerate every 90 days, why, is it a pain or a good thing?
                - <https://letsencrypt.org/2015/11/09/why-90-days.html>