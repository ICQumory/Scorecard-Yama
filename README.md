# Scorecard · Yamá Cosméticos
 
Sistema web de avaliação trimestral de Representantes Comerciais Autônomos (RCAs) da Yamá Cosméticos.
 
**URL de produção:** `https://icqumory.github.io/Scorecard-Yama/`
 
---
 
## O que é
 
Formulário de avaliação com 10 critérios ponderados (5 quantitativos, peso 70% — 5 qualitativos, peso 30%), cálculo automático de score final, persistência em Supabase, e painel administrativo para consulta, edição, exclusão e exportação CSV das avaliações.
 
## Modelo de avaliação
 
| Bloco | Peso | Critérios |
|---|---|---|
| Quantitativo | 70% | Crescimento, Faturamento, Positivação, MIX, Faseamento |
| Qualitativo | 30% | Participação em Reuniões, Boas Práticas, Ações de Sell Out, Conhecimento de Chão de Loja, Acompanhamento de Sell-out |
 
```
Score Final = (Média Ponderada Quantitativa × 0,7) + (Média Ponderada Qualitativa × 0,3)
```
 
## Stack
 
- HTML + JavaScript puro (sem build step, sem framework)
- Supabase (PostgreSQL) como backend — tabela `scorecard_evaluations`
- Hospedagem: GitHub Pages
## Estrutura
 
Arquivo único: `index.html` — contém HTML, CSS e JavaScript inline.
 
## Configuração
 
As credenciais do Supabase e a senha do painel administrativo estão definidas na função `init()`, dentro do `index.html`:
 
```javascript
SUPABASE_URL = 'https://kwvfypsakqkzxlggrcrp.supabase.co';
SUPABASE_KEY = 'sb_publishable_...';
ADMIN_PASS   = '...';
```
 
> ⚠️ **Atenção:** essas credenciais ficam visíveis no código-fonte público. A chave do Supabase é a chave `anon/public` (uso client-side esperado), protegida por Row Level Security (RLS) no banco — não é uma chave secreta. A senha do painel admin, no entanto, é apenas obscurecimento: qualquer pessoa com acesso ao repositório consegue lê-la. Trocar periodicamente é recomendado.
 
## Banco de dados
 
A tabela `scorecard_evaluations` e as políticas de RLS devem ser criadas no SQL Editor do Supabase. O script de criação está documentado em comentário no final do `index.html`.
 
## Deploy
 
Push para a branch `main` atualiza o site automaticamente via GitHub Pages (Settings → Pages → Source: `main` / root).
 
## Histórico
 
- **v1.0** (Jun/2026) — MVP original, desenvolvido na conta `caiomancuso/scorecard`
- Migração para conta corporativa `ICQumory` — projeto Supabase recriado, credenciais rotacionadas
## Identidade visual
 
Projeto segue o Guia de Identidade Visual Yamá v1.0 — paleta vermelho institucional `#C8102E`, tipografia Inter/Segoe UI, componentes padronizados (ver documentação interna).
