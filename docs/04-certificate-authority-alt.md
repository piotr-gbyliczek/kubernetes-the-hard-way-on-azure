# Provisioning a CA and Generating TLS Certificates

In this lab you will provision a [PKI Infrastructure](https://en.wikipedia.org/wiki/Public_key_infrastructure) using [OpenSSL](https://www.openssl.org/), then use it to bootstrap a Certificate Authority, and generate TLS certificates for the following components: etcd, kube-apiserver, kubelet, and kube-proxy.

# Prerequisites

Create a directory to store all certificates locally, and change to it: 

```shell
mkdir /path/to/kubernetes-the-hard-way
cd /path/to/kubernetes-the-hard-way
```

create the directory structure and start CA by generating key and signing certificate:

```shell
mkdir db private newcerts

openssl genrsa -out certs/ca.key 4096
openssl req -new -key certs/ca.key -subj "/CN=KUBERNETES-CA" -out certs/ca.csr
openssl x509 -req -in certs/ca.csr -signkey certs/ca.key -CAcreateserial -out certs/ca.crt -days 1000
```
