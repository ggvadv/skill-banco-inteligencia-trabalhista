# Skill — Banco de Inteligência Trabalhista

Skill do Claude Code usada pela GGV Advogados na análise trabalhista pelo lado do
reclamante: dossiês cumulativos por empresa, prova documental, cálculo, CCT/ACT,
jurisprudência e defesa esperada.

A skill inteira é o arquivo [`SKILL.md`](SKILL.md).

## Instalar

Windows: [`INSTALAR-WINDOWS.md`](INSTALAR-WINDOWS.md) — 6 passos, ~10 minutos, uma vez por máquina.

Resumo, para quem já tem Git e Claude Code:

```
git clone https://github.com/ggvadv/skill-banco-inteligencia-trabalhista.git
```

Copie o `SKILL.md` para `~/.claude/skills/banco-inteligencia-trabalhista/SKILL.md`
(no Windows, `C:\Users\seu-nome\.claude\skills\...`) e reinicie o Claude Code.

## Atualizar

`git pull`, copie por cima e reinicie o Claude Code. O `git pull` sozinho não muda a
skill que o Claude lê.

Uso interno.
