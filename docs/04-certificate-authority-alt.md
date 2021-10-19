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
CA_DAYS=1000


openssl genrsa -out private/$CA_NAME.key 4096
openssl req -new -key private/$CA_NAME.key -subj "$CA_SUBJ" -out certs/$CA_NAME.csr
openssl x509 -req -in certs/$CA_NAME.csr -signkey private/$CA_NAME.key -CAcreateserial -out certs/$CA_NAME.crt -days $CA_DAYS
```

```shell
ADMIN_NAME='admin'
ADMIN_SUBJ='/CN=admin/O=system:masters'


openssl genrsa -out private/$ADMIN_NAME.key 4096
openssl req -new -key private/$ADMIN_NAME.key -subj "$ADMIN_SUBJ" -out certs/$ADMIN_NAME.csr
openssl x509 -req -in certs/$ADMIN_NAME.csr -signkey private/$CA_NAME.key -CAcreateserial -out certs/$ADMIN_NAME.crt -days $CA_DAYS
```

```shell
KS_NAME='kube-scheduler'
KS_SUBJ='/CN=system:kube-scheduler'


openssl genrsa -out private/$KS_NAME.key 4096
openssl req -new -key private/$KS_NAME.key -subj "$KS_SUBJ" -out certs/$KS_NAME.csr
openssl x509 -req -in certs/$KS_NAME.csr -signkey private/$CA_NAME.key -CAcreateserial -out certs/$KS_NAME.crt -days $CA_DAYS
```

```shell
KCM_NAME='kube-controller-manager'
KCM_SUBJ='/CN=system:kube-controller-manager'


openssl genrsa -out private/$KCM_NAME.key 4096
openssl req -new -key private/$KCM_NAME.key -subj "$KCM_SUBJ" -out certs/$KCM_NAME.csr
openssl x509 -req -in certs/$KCM_NAME.csr -signkey private/$CA_NAME.key -CAcreateserial -out certs/$KCM_NAME.crt -days $CA_DAYS
```

```shell
SA_NAME='service-account'
SA_SUBJ='/CN=service-accounts'

openssl genrsa -out private/$SA_NAME.key 4096
openssl req -new -key private/$SA_NAME.key -subj "$SA_SUBJ" -out certs/$SA_NAME.csr
openssl x509 -req -in certs/$SA_NAME.csr -signkey private/$CA_NAME.key -CAcreateserial -out certs/$SA_NAME.crt -days $CA_DAYS
```
