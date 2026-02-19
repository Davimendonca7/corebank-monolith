# 💳 CoreBank Monolith

MVP monolítico do **CoreBank**, um projeto de estudo inspirado em bancos digitais como o Nubank.

Esta primeira versão foca em:

* Modelagem de domínio financeiro
* Boas práticas de arquitetura
* Design de API com OpenAPI (contract-first)
* Base sólida para futura migração para microsserviços com Kafka

---

## 🎯 Objetivo do Projeto

Construir um banco digital simplificado com:

* Criação de contas
* Consulta de saldo
* Transferências entre usuários
* Extrato de transações
* Ledger imutável como fonte da verdade

Essa versão é **monolítica**, mas já estruturada pensando em:

* Separação por domínio
* Camadas bem definidas
* Evolução futura para arquitetura distribuída

---

## 🧱 Arquitetura

Arquitetura em camadas com princípios de Clean Architecture:

```
controller → service → domain → repository
```

### Camadas

* **Controller**

    * Exposição da API REST
    * Validação de entrada
    * Mapeamento DTO ↔ domínio

* **Service (Application Layer)**

    * Regras de negócio
    * Orquestração de casos de uso

* **Domain**

    * Entidades
    * Regras financeiras
    * Lógica de saldo e transferência

* **Repository**

    * Persistência com JPA

---

## 📄 API Design (OpenAPI-first)

As APIs são documentadas utilizando **OpenAPI 3**, garantindo:

* Contrato formal de request/response
* Códigos HTTP padronizados
* Schemas reutilizáveis
* Documentação via Swagger UI

Objetivo: simular padrão enterprise de design de APIs financeiras.

---

## 🔁 Regras Financeiras Implementadas

* Transferências só ocorrem se houver saldo suficiente
* Operações são atômicas (transação de banco)
* Ledger imutável (não há edição de transações)
* Idempotência preparada para evolução futura

---

## ⚙️ Stack

* Java 17
* Spring Boot
* PostgreSQL
* Spring Data JPA
* Docker
* OpenAPI 3 (Swagger)

---

## 📂 Estrutura do Projeto

```
corebank-monolith
 ├── account
 ├── transaction
 ├── ledger
 ├── config
 ├── controller
 ├── service
 ├── repository
 └── domain
```

Organização pensada para facilitar a futura extração de serviços.

---

## 🚀 Como Executar

### 1️⃣ Subir banco com Docker

```bash
docker-compose up -d
```

### 2️⃣ Rodar aplicação

```bash
./mvnw spring-boot:run
```

### 3️⃣ Acessar documentação

```
http://localhost:8080/swagger-ui.html
```

---

## 📌 Endpoints Principais

### Criar Conta

```
POST /api/v1/accounts
```

### Consultar Saldo

```
GET /api/v1/accounts/{id}/balance
```

### Transferir

```
POST /api/v1/transactions
```

### Extrato

```
GET /api/v1/accounts/{id}/statement
```

---

## 🪜 Próxima Evolução

Este monolito será evoluído para:

* Separação em microsserviços
* Event-driven architecture
* Mensageria com Apache Kafka
* Consistência eventual
* Observabilidade
* Deploy em Kubernetes

---

## 🧠 Objetivo Técnico

Demonstrar domínio em:

* Modelagem de domínio financeiro
* Arquitetura limpa
* API design profissional
* Engenharia backend escalável
* Transição de monolito para microsserviços

---

## 📖 Status

🚧 Em desenvolvimento — Fase 1 (MVP Monolítico)

---
