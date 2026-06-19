# 🥩 Robinho · Motor de Triagem Inteligente · Minerva Foods

Sistema de triagem de candidatos com análise multidimensional, banco de dados persistente e suporte a 3 idiomas.

---

## 🚀 Stack

| Camada | Tecnologia |
|--------|-----------|
| Frontend | React 18 + TypeScript + Vite |
| Banco de dados | Supabase (PostgreSQL) |
| Deploy | Vercel (CI/CD automático) |
| i18n | i18next — PT 🇧🇷 / EN 🇺🇸 / ES 🇪🇸 |
| Parsers | PapaParse (CSV) + SheetJS (XLSX) |

---

## 📋 Pré-requisitos

- Node.js 18+
- Conta no [Supabase](https://supabase.com) (grátis)
- Conta na [Vercel](https://vercel.com) (grátis)
- Conta no [GitHub](https://github.com)

---

## 1️⃣ Configurar Supabase

1. Acesse [supabase.com](https://supabase.com) → **New Project**
2. Anote a **URL** e **anon key** (Settings → API)
3. No SQL Editor, copie e execute o arquivo:
   ```
   supabase/migrations/001_schema.sql
   ```
4. Isso criará as tabelas: `processos`, `triagens`, `candidatos`, `configs_globais`

---

## 2️⃣ Configurar variáveis de ambiente

Copie o arquivo de exemplo:
```bash
cp .env.example .env
```

Preencha com suas credenciais do Supabase:
```env
VITE_SUPABASE_URL=https://xxxxxxxxxxx.supabase.co
VITE_SUPABASE_ANON_KEY=eyJhxxxxxxxxxxxxxxxxxxxxxxxx
```

---

## 3️⃣ Rodar localmente

```bash
npm install
npm run dev
```

Acesse: `http://localhost:5173`

---

## 4️⃣ Deploy no GitHub + Vercel (automático)

### GitHub
```bash
git init
git add .
git commit -m "feat: Robinho v1.7 — production ready"
git remote add origin https://github.com/SEU_USUARIO/robinho-minerva.git
git push -u origin main
```

### Vercel
1. Acesse [vercel.com](https://vercel.com) → **Add New Project**
2. Importe o repositório do GitHub
3. Em **Environment Variables**, adicione:
   - `VITE_SUPABASE_URL` → sua URL do Supabase
   - `VITE_SUPABASE_ANON_KEY` → sua chave anon
4. Clique em **Deploy**

✅ **A partir daqui, qualquer `git push` na branch `main` dispara deploy automático na Vercel.**

---

## 🧠 Engine de Triagem — Dimensões

| ID | Dimensão | Peso Padrão |
|----|----------|-------------|
| D1 | Aderência ao Descritivo | 20 pts |
| D2 | Perfil LinkedIn | 10 pts |
| D3 | Tempo na Posição | 15 pts |
| D4 | Experiência em Liderança | 10 pts |
| D5 | Formação Acadêmica | 10 pts |
| D8 | Indústria de Carne | 15 pts |
| D9 | Idiomas | 10 pts |
| D10 | Localização / Cidade | 10 pts |

**Total: 100 pts**

### Classificação
- ✅ **Aprovado**: Score ≥ 70 pts (configurável)
- ⚡ **Potencial**: Score ≥ 40 pts (configurável)
- ❌ **Reprovado**: Score < 40 pts

---

## 🌐 Idiomas Suportados

- 🇧🇷 Português (padrão)
- 🇺🇸 English
- 🇪🇸 Español

Selecionável por recrutador via header ou aba Configurações.

---

## 📊 Banco de Dados — Tabelas

```
processos      → Cada processo seletivo configurado
triagens       → Cada execução de triagem
candidatos     → Candidatos avaliados com scores por dimensão
configs_globais → Configurações persistidas globalmente
```

---

## 🔜 Próximos Passos (Roadmap)

- [ ] Integração com API da Gupy (aguardando autorização)
- [ ] Autenticação por equipe (Supabase Auth)
- [ ] Dashboard executivo com filtros por período
- [ ] Exportação para Excel com formatação
- [ ] Envio WhatsApp via API oficial

---

## 📁 Estrutura do Projeto

```
robinho/
├── src/
│   ├── App.tsx              # Aplicação principal
│   ├── main.tsx             # Entry point React
│   ├── styles.css           # Glassmorphism + Skeuomorphism
│   ├── i18n/
│   │   ├── index.ts         # Configuração i18next
│   │   ├── pt.ts            # Português
│   │   ├── en.ts            # English
│   │   └── es.ts            # Español
│   └── lib/
│       ├── engine.ts        # Motor de triagem (scoring)
│       ├── parser.ts        # Parser CSV/XLSX
│       ├── supabase.ts      # Cliente Supabase + tipos
│       └── db.ts            # Operações de banco de dados
├── supabase/
│   └── migrations/
│       └── 001_schema.sql   # Schema completo do banco
├── .env.example             # Variáveis de ambiente
├── vercel.json              # Configuração Vercel
├── vite.config.ts           # Build config
└── README.md
```

---

**Minerva Foods · Coordenação Global de Atração e Seleção**
