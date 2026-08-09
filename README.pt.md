# Keep Improving

[🇺🇸 Read in English](README.md)

Skill do Claude Code pra melhoria contínua de produto. Aponte pra um projeto e ela fica nele: corrige bug, escreve teste que falta, arruma UI e UX, e propõe feature que faça sentido.

---

## O que faz

Cada ciclo: pesquisa o domínio do produto, lê o código, acha o que está quebrado ou faltando, aplica o que pode com segurança, fila o resto pra revisão.

**Mudança segura vai direto, sem commit:** teste faltando pra código já em produção, bug com causa única e clara, polish pequeno de UI/UX, alt text ou aria label faltando, código morto confirmado.

**Mudança sensível vai pro `TODO IMPROVEMENTS.md`** com categoria, fonte, arquivos exatos, motivo e risco. Feature nova, mudança de layout, refactor que cruza mais de um arquivo, troca de dependência: tudo enfileirado, nada aplicado sozinho.

A skill para quando você pedir, ou quando realmente não sobrar mais nada pra melhorar. Se o contexto acabar no meio do ciclo, ela atualiza o `TODO IMPROVEMENTS.md` pra uma sessão nova continuar de onde parou.

---

## A regra que importa

Essa skill nunca roda `git commit` nem `git push`. Ela edita arquivo e deixa o diff parado na sua working tree. Você revisa, você decide o que sobe, você roda o commit, não importa quão pequena ou óbvia a mudança pareça.

---

## Ferramentas de pesquisa

- **[last30days](https://github.com/mvanhorn/last30days-skill)** pro ângulo de sentimento: o que as pessoas falam de verdade no Reddit, Hacker News, X e GitHub sobre o domínio do produto ou a stack usada.
- **[Scrapling](https://github.com/D4Vinci/Scrapling)** pra puxar página inteira quando um trecho de busca não basta: doc, changelog, produto concorrente.
- Busca web comum pro resto.

Instalar o keep-improving como plugin já instala o `last30days` junto. Sem ele, a skill ainda funciona e pula direto pra busca web nessa parte. `scrapling` é uma lib Python (`pip install scrapling`); a skill usa se estiver instalada e cai pra busca web comum se não estiver.

---

## Como usar

**Sem instalar:**
> "Leia https://github.com/obrenoalvim/keep-improving e siga a skill Keep Improving."

**Como plugin (disponível em todas as sessões):**
```
/plugin marketplace add obrenoalvim/keep-improving
/plugin install keep-improving@keep-improving
```

Depois invoque: "Rode a Keep Improving neste projeto."

**Copiando o arquivo da skill:**
Copie `skills/keep-improving/SKILL.md` pro diretório de skills do seu sistema e invoque por lá.

---

## Funciona com

Qualquer codebase com working tree pra editar: web app, CLI, lib, mobile, backend. Precisa de git pra deixar a mudança sem commit e diffável.
