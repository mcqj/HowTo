# HowTo
This is just a collection of notes on How to do some infrequent tasks

## Set up Certificates
Generate a 2048 bit RSA private key  
`openssl genrsa -out jmq-key.pem 2048`

generate a Certificate Signing Request (CSR) for the private key  
`openssl req -new -sha256 -key jmq-key.pem -out jmq-csr.pem`

Either, send this to a CA or *Generate a self-signed certificate*  
`openssl x509 -req -in jmq-csr.pem -signkey jmq-key.pem -out jmq-cert.pem`

Generate a pfx or p12 file  
`openssl pkcs12 -export -in jmq-cert.pem -inkey jmq-key.pem -certfile ca-cert.pem -out jmq.pfx`

