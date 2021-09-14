# Download the p7b format file

```bash
curl -OL https://www.example.com/security/pki/trs/ios_union.p7b
```

# extra the Trusted Root Store Signer cert

```bash
openssl pkcs7 -print_certs -in ios_union.p7b -inform DER -out Trusted_Root_Store_Signer.pem
```

# Decrypt the p7b format file

```bash
openssl cms -verify -noverify -nocerts -nodetach -signer Trusted_Root_Store_Signer.pem -inform DER -in ios_union.p7b -outform DER -out ios_union.p7b.bin
```

# convert p7b format file into pem format

```bash
openssl pkcs7 -inform DER -print_certs -outform PEM -in ios_union.p7b.bin -out ios_union.pem
```

# print all the certs content in p7b format file

```bash
openssl pkcs7 -print_certs -in ios_union.p7b.bin -inform DER -noout -text
```

# print the single cert with pem format

```bash
openssl x509 -text -inform DER -in xxx.pem
```
