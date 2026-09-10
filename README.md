# Skill — Banco de Inteligência Trabalhista

Skill do Claude Code usada pela GGV Advogados na análise trabalhista pelo lado do
reclamante: dossiês cumulativos por empresa, prova documental, cálculo, CCT/ACT,
jurisprudência e defesa esperada.

A skill inteira é o arquivo [`SKILL.md`](SKILL.md). **Esta é a cópia oficial**: toda
máquina do escritório baixa daqui, e toda mudança no método é feita aqui.

## Instalar (advogado)

Ninguém abre terminal. O advogado cola mensagens no Claude Code e ele faz o resto.

- Passo a passo em Word, para mandar ao pessoal: `Instalar skill trabalhista - passo a passo.docx`
- Mesmo conteúdo em texto: [`INSTALAR-WINDOWS.md`](INSTALAR-WINDOWS.md)

O repositório é **público**: o download não pede login. Por isso mesmo, **nada de dado de
cliente aqui** — nem nome, nem CPF, nem número de processo. Só o método.

## Mudar o método

1. Edite o `SKILL.md` aqui e faça commit + push.
2. Avise no grupo. Cada advogado cola a mensagem "Quando o método for atualizado" do
   passo a passo e reinicia o Claude Code.

O `git pull` sozinho não muda a skill que o Claude lê — ele atualiza a cópia baixada,
e a mensagem de atualização copia por cima da instalada.

Uso interno.
