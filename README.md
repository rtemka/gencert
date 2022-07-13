### Утилита **gencert**

Создает пару публичный-приватный ключ в формате **_.pem_**

#### Пример использования

```bash
go install github.com/rtemka/gencert@latest
```
```bash
gencert -host <host-name> -cert <public-key-filename> -key <private-key-filename> -org <org-name> -days <NUM-days>
```

#### Описание

Работает аналогично утилите ``generate_cert.go`` из пакета стандартной библиотеки golang [``crypto/tls``](https://pkg.go.dev/crypto/tls).

Основная разница в том, что эта утилита создает пару ключей, которые могут использоваться и клиентом, для создания так называемого [``mutual TLS authentication (mTLS)``](https://www.cloudflare.com/learning/access-management/what-is-mutual-tls/).

Другие изменения: 
 1. Можно менять название организации в сертификате через ключ ``-org``, 
 2. Ключ ``-duration`` заменен на ключ ``-days``, соответственно нужно ввести просто к примеру ``-days 365``, вместо ``-duration 8760h0m0s``
 3. Используется только ``-ecdsa-curve P256``