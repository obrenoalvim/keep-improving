# keep-improving

Skill do Claude Code pra melhoria contínua e autônoma de produto.

Read this in [English](README.md).

## Sobre

Você aponta essa skill pra um projeto e ela fica nele. Pesquisa o que usuários reais falam sobre o domínio do produto, lê o código, corrige bugs, escreve teste que falta, arruma UI e UX capenga, e propõe feature nova que faça sentido. Fica rodando em ciclo até você mandar parar.

Duas ferramentas de pesquisa puxam o processo. `last30days` traz sentimento real de Reddit, Hacker News, X e GitHub, então a skill sabe do que as pessoas reclamam de verdade, não só o que uma busca genérica devolve. `scrapling` puxa a página inteira quando um trecho de busca não basta, útil pra doc, changelog e produto concorrente.

Toda mudança cai em dois grupos. Mudança segura, teste faltando, bug pequeno, polish leve, é aplicada direto na working tree. Decisão maior, feature nova, mudança de layout, troca de dependência, vai pro `TODO IMPROVEMENTS.md` pra você decidir.

Uma regra fica acima de todas as outras: essa skill nunca commita nem dá push sozinha. Ela edita arquivo e deixa o diff lá parado. Você revisa, você decide o que sobe, você roda o commit. Sem exceção, não importa quão pequena ou óbvia a mudança pareça.

## Tags

`claude-code` `agent-skill` `autonomous-agent` `code-review` `automation` `ai-agent` `developer-tools` `testing` `ux` `product-improvement`

## Arquivos

- `SKILL.md`: a spec que o Claude lê quando a skill roda
- `README.md`: versão em inglês
- `README.pt-BR.md`: este arquivo

## Uso

Invoca a skill, aponta pra um projeto, deixa rodar. Ela para quando você mandar, ou quando realmente não sobrar mais nada pra melhorar.
