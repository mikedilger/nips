NIP-NN
======

Available for Private Direct Messaging
--------------------------------------

`draft` `optional` `author:michaeldilger`

NIP-04 provides a mechanism for encrypted direct messaging. However there are several shortcomings:

* Metadata about who is talking to whom is publicly available.
* The encrypted message remains on the relays forever unless the author explicitly deletes it.

This NIP introduces a mechanism by which a client can invite direct peer-to-peer messaging by
publishing information about where they can be contacted.  Such an invite does not expose who
they may which to contact them, and any actual encrypted messaging would be out of scope for
relays.

A special event with kind `N`, meaning "available for private direct messaging". It MUST have
the following attributes

**`content`** MUST be a JSON string containing connection information where the author is
    available for messaging.

  **`ip`** IP address, REQUIRED field where the author is available for messaging
  **`port`** IP port, REQUIRED field
  **`protocol`** REQUIRED FIELD
  **`protocol_version`** OPTIONAL
  **`handle`** OPTIONAL



This NIP does not specify the peer-to-peer messaging protocol. But it is expected that such
a protocol would utilize secp256k1 public and private keys and Diffie-Hellman key agreement (ECDH)
to establish a shared secret.

FIXME: we should probably define that protocol or else this NIP could not be put into
practical use.  Should we use nostr Message types for client-to-client?



FIXME - timestamp when availability deemed to cease
      - key agreement protocol scheme specified, we start off with one
