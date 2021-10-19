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
mkdir db private certs
```

Now we can start generating keys and certificates:

```shell
CA_NAME='ca'
CA_SUBJ='/CN=KUBERNETES-CA'


openssl genrsa -out private/$CA_NAME.key 4096
openssl req -new -key private/$CA_NAME.key -subj "CA_SUBJ" -out certs/$CA_NAME.csr
openssl x509 -req -in certs/$CA_NAME.csr -signkey private/$CA_NAME.key -CAcreateserial -out certs/$CA_NAME.crt -days 1000
```
