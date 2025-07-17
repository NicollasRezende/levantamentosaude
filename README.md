## 📦 **API Headless Liferay – Coleta de Conteúdos, Páginas e Documentos**

Documentação de endpoints úteis para coleta de dados estruturados, páginas e documentos via API Headless do Liferay.

---

### 🔹 **1. Conteúdos Estruturados**

Obtenha todos os conteúdos estruturados (estruturas e templates) criados em um site específico.

#### ✅ Endpoint:

```
GET /v1.0/sites/{siteId}/structured-contents
```

#### 📘 Exemplo com paginação:

```bash
curl -X 'GET' \
  'https://www.saude.df.gov.br/o/headless-delivery/v1.0/sites/37101/structured-contents?page=1&pageSize=20' \
  -H 'accept: application/json' \
  -H 'x-csrf-token: bQb3T90P'
```

#### 📊 Dados de exemplo:

* `totalCount`: **8.268 conteúdos**
* `lastPage`: 414
* `pageSize`: 20

---

### 🗂️ **2. Pastas de Conteúdo (Agrupamentos)**

Liste as pastas usadas para organizar os conteúdos estruturados.

#### ✅ Endpoint:

```
GET /v1.0/sites/{siteId}/structured-content-folders
```

#### 📘 Exemplo com paginação:

```bash
curl -X 'GET' \
  'https://www.saude.df.gov.br/o/headless-delivery/v1.0/sites/37101/structured-content-folders?page=1&pageSize=20' \
  -H 'accept: application/json' \
  -H 'x-csrf-token: bQb3T90P'
```

#### 📊 Dados de exemplo:

* `totalCount`: **1.487 pastas**
* `lastPage`: 149
* `pageSize`: 10

---

### 📄 **3. Páginas do Site (Site Pages)**

Obtenha a estrutura de navegação das páginas do site.

> ⚠️ **Atenção:** Em alguns casos esse endpoint pode apresentar problemas ou retornos vazios.

#### ✅ Endpoint principal:

```
GET /v1.0/sites/{siteId}/site-pages
```

#### 📘 Exemplo com paginação:

```bash
curl -X 'GET' \
  'https://www.saude.df.gov.br/o/headless-delivery/v1.0/sites/37101/site-pages?page=1&pageSize=10' \
  -H 'accept: application/json' \
  -H 'x-csrf-token: bQb3T90P'
```

#### ➕ Endpoint para páginas filhas (via `friendlyUrlPath`):

```
GET /v1.0/sites/{siteId}/site-pages/{friendlyUrlPath}
```

---

### 📁 **4. Documentos (Arquivos por Pasta)**

Para coletar documentos do repositório do site, é necessário:

1. **Listar as pastas de documentos**.
2. **Buscar os documentos dentro de cada pasta**.

---

#### ✅ Listar pastas de documentos:

```
GET /v1.0/sites/{siteId}/document-folders
```

#### 📘 Exemplo com paginação:

```bash
curl -X 'GET' \
  'https://www.saude.df.gov.br/o/headless-delivery/v1.0/sites/37101/document-folders?page=1&pageSize=20' \
  -H 'accept: application/json' \
  -H 'x-csrf-token: bQb3T90P'
```

---

#### ✅ Listar documentos de uma pasta específica:

```
GET /v1.0/document-folders/{documentFolderId}/documents
```

#### 📘 Exemplo com paginação:

```bash
curl -X 'GET' \
  'https://www.saude.df.gov.br/o/headless-delivery/v1.0/document-folders/142727/documents?page=1&pageSize=20' \
  -H 'accept: application/json' \
  -H 'x-csrf-token: bQb3T90P'
```

#### 📊 Dados de exemplo:

* `totalCount`: **12.008 documentos**
* `lastPage`: 601
* `pageSize`: 20

---

### ✅ **Resumo Geral de Volumes**

| Tipo de Dado              | Total de Registros | Páginas | Page Size |
| ------------------------- | ------------------ | ------- | --------- |
| Conteúdos Estruturados    | 8.268              | 414     | 20        |
| Pastas de Conteúdo        | 1.487              | 149     | 10        |
| Documentos em Repositório | 12.008             | 601     | 20        |
