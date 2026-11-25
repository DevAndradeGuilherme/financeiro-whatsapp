# financeiro-whatsapp

Base local da API de contas a pagar operada pelo WhatsApp. Esta etapa inclui
somente a API NestJS, PostgreSQL local e Prisma; integrações com WhatsApp, IA,
cadastro de contas e lembretes ainda não fazem parte do projeto.

## Requisitos

- Node.js 22 ou superior
- npm 10 ou superior
- Docker com Docker Compose

## Configuração

```bash
cp .env.example .env
npm install
```

O arquivo `.env` contém valores locais de desenvolvimento e não é versionado.

## Banco de dados local

```bash
docker compose up -d
docker compose ps
```

O PostgreSQL usa um volume nomeado (`postgres_data`) para persistir os dados.
O Prisma está configurado para PostgreSQL, mas ainda não há modelos ou
migrations nesta etapa.

## API

```bash
npm run start:dev
```

A API inicia em `http://localhost:3000` por padrão. Para validar que o processo
está respondendo:

```bash
curl --fail --silent http://localhost:3000/health
```

Resposta esperada:

```json
{"status":"ok"}
```

## Validação

```bash
npm run prisma:validate
docker compose config --quiet
npm run build
npm test
npm run test:e2e
```
