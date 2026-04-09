# 📊 Visualizador de Extrato OFX

Aplicação web de página única (SPA) para visualização de arquivos `.ofx` (Open Financial Exchange) — o formato padrão de extratos bancários brasileiros. Carregue seu extrato e veja todas as transações de forma organizada, colorida e legível, **sem enviar nenhum dado para a internet**.

---

## ✨ Funcionalidades

- 📂 Carregamento de arquivo via **clique** ou **arrastar e soltar** (drag and drop em toda a página)
- 🏦 Identificação automática da **instituição bancária** pelo código COMPE
- 📋 Exibição de **agência** e **número de conta**
- 📅 Listagem de todas as **transações** com data, descrição e valor formatado
- 🔴🟢 Valores em **vermelho** para débitos e **verde** para créditos
- 💰 Formatação monetária em **Real Brasileiro (R$)**
- 📱 Layout **responsivo** para desktop e mobile
- 🔒 **100% client-side** — nenhum dado é enviado a servidores externos

---

## 🛠️ Tecnologias Utilizadas

| Tecnologia | Descrição |
|---|---|
| **HTML5** | Estrutura da página |
| **CSS3** | Estilos personalizados (efeito zebrado, drag-over) |
| **JavaScript (ES6+)** | Lógica de parsing e manipulação do DOM — Vanilla JS puro, sem frameworks |
| **Tailwind CSS (CDN v3)** | Estilização utilitária e responsividade |

> ⚠️ Nenhum framework JavaScript (React, Vue, Angular, etc.) foi utilizado. O projeto funciona com **JavaScript puro**.

---

## ⚙️ Como Funciona

### 1. Carregamento do Arquivo
O usuário pode carregar o arquivo `.ofx` de duas formas:
- Clicando no botão **"Carregar Arquivo"** para abrir o seletor nativo do sistema operacional
- **Arrastando e soltando** o arquivo em qualquer área da página

### 2. Leitura
O arquivo é lido pela **`FileReader` API** nativa do navegador, com encoding `ISO-8859-1` (Latin-1) — padrão utilizado pelos bancos brasileiros nos arquivos OFX.

### 3. Parsing do OFX
O conteúdo é processado com **expressões regulares (Regex)**, extraindo as seguintes tags:

| Tag OFX | Dado Extraído |
|---|---|
| `BANKID` | Código do banco (ex: `341` → Itaú) |
| `BRANCHID` | Número da agência |
| `ACCTID` | Número da conta |
| `STMTTRN` | Bloco de cada transação |
| `DTPOSTED` | Data (`YYYYMMDD` → `DD/MM/YYYY`) |
| `MEMO` / `NAME` | Descrição da transação |
| `TRNAMT` | Valor (negativo = débito, positivo = crédito) |

### 4. Exibição
- **Cards informativos** com banco, agência e conta
- **Tabela responsiva** com efeito zebrado nas linhas
- **Scroll suave** automático até os resultados após o carregamento

---

## 🏦 Bancos Suportados (Identificação Automática)

| Código | Banco |
|---|---|
| 001 | Banco do Brasil |
| 033 | Santander |
| 041 | Banrisul |
| 047 | Banese |
| 021 | Banestes |
| 070 | BRB |
| 077 | Inter |
| 104 | Caixa Econômica Federal |
| 212 | Original |
| 237 | Bradesco |
| 260 | Nubank |
| 336 | C6 Bank |
| 341 | Itaú Unibanco |
| 422 | Safra |
| 623 | Pan |
| 655 | Neon |
| 745 | Citibank |
| 748 | Sicredi |
| 756 | Sicoob |
| 0197 | Stone S/A |
| 004 | Banco do Nordeste |

---

## 📁 Estrutura do Projeto

```
/
└── index.html   # Arquivo único — contém HTML, CSS e JavaScript
```

---

## 🚀 Como Usar

### Através da internet pelo site [Ver OFX](https://verofx.pages.dev/) _(verofx.pages.dev)_

Por ser um projeto de arquivo único, **não há instalação ou dependências locais**.

1. Clone o repositório:
   ```bash
   git clone https://github.com/soumaisalex/verOFX.git
   ```
2. Abra o arquivo `index.html` diretamente no navegador
3. Carregue seu arquivo `.ofx` e visualize o extrato

> Também pode ser hospedado em qualquer serviço de páginas estáticas como **GitHub Pages**, **Netlify** ou **Vercel**.

---

## 🔒 Privacidade

Todo o processamento acontece **exclusivamente no navegador do usuário**. Nenhum dado financeiro é transmitido, armazenado ou enviado a qualquer servidor externo. O projeto não utiliza cookies, analytics ou qualquer forma de rastreamento.

---

## 👨‍💻 Autor

Desenvolvido por [Alex Passos](https://www.instagram.com/soumaisalex)

---

## 📄 Licença

Este projeto está sob a licença MIT. Sinta-se livre para usar, modificar e distribuir.
