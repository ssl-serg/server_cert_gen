# Server test certificate generator (Windows Batch Script)

## Description

It creates server certificate: 
<pre>CA -> Server Cert</pre>

**openssl.exe** tool required to launch script !

## Settings

Look at **create_server_cert.cmd** for configuration details:
<pre>
  set CRT_CA_DAYS=3650

  set CRT_CA_SUBJ="/CN=My CA"
  set CRT_SUBJ="/C=My/ST=My St/L=My Loc/O=My Org/OU=My OU/CN=myhost.local"

  set CRT_PKCS12_PWD=1234
</pre>

## Result

As result, the server certificate will be created at "pub" directory:

- **server_cert.key** - server certificate's unencrypted key

- **server_cert.p12** - pkcs#12 server certificate's container with full root chain (CA) included

- **server_cert.pem** - server certificate in PEM form

- **server_cert_full_chain_with_key.pem** - server certificate in PEM form with private key and full root chain (CA) included
<pre>
  -----BEGIN CERTIFICATE-----
    Server Certificate's public key
  -----END CERTIFICATE-----
  -----BEGIN PRIVATE KEY-----
    Unencrypted Server Certificate's private key
  -----END PRIVATE KEY-----
  -----BEGIN CERTIFICATE-----
    CA's public key
  -----END CERTIFICATE-----
</pre>
- **server_cert_full_chain_without_key.pem** - server certificate in PEM form with full root chain (CA) included
<pre>
  -----BEGIN CERTIFICATE-----
    Server Certificate's public key
  -----END CERTIFICATE-----
  -----BEGIN CERTIFICATE-----
    CA's public key
  -----END CERTIFICATE-----
</pre>
- **server_cert_roots_only.pem** - server certificate's full root chain (CA) only
<pre>
  -----BEGIN CERTIFICATE-----
    CA's public key
  -----END CERTIFICATE-----
</pre>
