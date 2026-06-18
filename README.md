# API REST de Gestão de Biblioteca

API REST para gerenciar uma biblioteca: livros, membros e empréstimos, com controle de disponibilidade.

> 📦 **Template de trabalho em grupo da WebForge.** Clique em **Use this template** (botão verde acima) para criar o repositório do seu grupo.

## 🚀 Como rodar

```bash
npm install
npm start        # inicia em http://localhost:3000
```

O projeto já sobe com uma rota raiz `GET /`. Todo o resto é com o grupo.

## 📋 Requisitos

- **Livros** — CRUD completo (`POST/GET/GET:id/PUT/DELETE /livros`) com título, autor, ano, ISBN e quantidade.
- **Membros** — CRUD completo (`/membros`) com nome, email e telefone.
- **Empréstimos** — `POST /emprestimos` (livroId + membroId + devolução), `PUT /emprestimos/:id/devolver`, `GET /emprestimos/ativos` e `GET /membros/:id/historico`.
- Verificar disponibilidade antes de emprestar (não emprestar livro sem estoque).
- **Estatísticas** — `GET /stats` com livros mais emprestados e membros mais ativos.

> Persistam os dados (arquivo JSON ou SQLite) — os testes podem reiniciar o servidor entre etapas.

## ✅ O que os testes de correção validam

Os testes automáticos sobem o **seu** servidor e fazem requisições HTTP reais contra a API. Eles verificam **comportamento** (status HTTP e corpo das respostas), não a estrutura interna do código — organizem os arquivos como preferirem. Para ser aprovado, a API precisa:

- [ ] `GET /` responde **200** (servidor sobe corretamente).
- [ ] `POST /livros` cria e responde **201**; o livro aparece em `GET /livros`.
- [ ] `GET /livros/:id` responde **404** para um id inexistente.
- [ ] `PUT /livros/:id` atualiza e `DELETE /livros/:id` remove o registro.
- [ ] `POST /emprestimos` registra um empréstimo válido e marca o livro como indisponível.
- [ ] Emprestar um livro sem exemplares disponíveis responde **409**.
- [ ] `PUT /emprestimos/:id/devolver` repõe a disponibilidade do livro.
- [ ] `GET /emprestimos/ativos` lista apenas empréstimos não devolvidos.
- [ ] `GET /stats` retorna os livros mais emprestados.
- [ ] Dados inválidos (campos faltando) respondem **400**.

## 👥 Trabalho em equipe (obrigatório)

Este é um ambiente o mais próximo possível do mercado:

- O repositório deve pertencer a **um** dos membros do grupo. Os **demais membros entram como colaboradores** em `Settings → Collaborators → Add people`.
- Cada membro trabalha em sua **própria branch** e abre **Pull Request** para a `main`, pedindo revisão de outro colega.
- A WebForge mede as **contribuições individuais** de cada membro (commits, linhas adicionadas e removidas) direto do histórico do GitHub. Distribuam bem o trabalho.

## 🧱 Stack

- Node.js + Express (CommonJS)
