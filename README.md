# 🚀 QR Code Generator

Aplicação criada com **Java 21**, **Spring Boot**, **Docker** e integração com **AWS S3**, capaz de **gerar QR Codes** a partir de textos e salvar essas imagens automaticamente na nuvem.

## Tecnologias Usadas

- Java 21
- Spring Boot
- Maven
- Docker
- AWS SDK
- Biblioteca ZXing (QR Code)
- Amazon S3

---

## O que esse projeto faz?

> Ele gera um QR Code baseado em um texto que você envia. Depois disso, salva a imagem em PNG lá no seu bucket S3 e te devolve a URL da imagem gerada. Simples, prático e funcional.

---


## ⚙️ Como rodar

### Pré-requisitos

- Java 21 instalado
- Maven
- Docker
- Conta na AWS com bucket configurado
- AWS CLI com as credenciais salvas

### 1. Configurar variáveis de ambiente

Crie um arquivo `.env` na raiz do projeto:

```env
AWS_ACCESS_KEY_ID=SUAS_CREDENCIAIS
AWS_SECRET_ACCESS_KEY=SUA_SENHA
AWS_REGION=sua-regiao
AWS_BUCKET_NAME=nome-do-seu-bucket
```

### 2. Rodar localmente
```bash
mvn clean package
mvn spring-boot:run
```

### 3. Rodar com Docker
```bash
docker build -t qrcode-generator .
docker run --env-file .env -p 8080:8080 qrcode-generator
```

Endpoint da API
POST /qrcode
Gera o QR Code e retorna a URL da imagem no S3.

Corpo da Requisição (JSON)
```json
{
  "text": "https://meusite.com"
}
```

Resposta
```json
{
  "url": "https://meu-bucket.s3.amazonaws.com/uuid-imagem.png"
}
```
