le-tls-sni
==========

Module for use with node-letsencrypt to generate certificates to satisfy
tls-sni-01 and tls-sni-02 ACME challenges.

Install
-------

```bash
npm install --save le-tls-sni
```

Usage
-----

The API is the same as for the node-letsencrypt v2 challenge set method:

* `require('le-tls-sni').generate(opts, domain, key, val, done)`

The `done` callback will be called like:

```javascript
done(null, {
, privkey: '<<privkey.pem>>'
, cert: '<<cert.pem>>'
, subject: 'x.y.invalid.acme'
, altnames: [ 'x.y.token.invalid.acme', 'x.y.ka.invalid.acme' ]
, issuedAt: 1470975565000
, expiresAt: 1478751565000
});
```

It will use `opts.challengeType` to distinguish between tls-sni-01 and
tls-sni-02.

