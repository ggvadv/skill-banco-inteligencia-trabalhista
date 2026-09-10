# Instalar a skill Banco de Inteligência Trabalhista — passo a passo

Seis passos. Uns 10 minutos. Uma vez só, no seu computador.

**Você não vai abrir terminal, não vai digitar comando, não vai instalar nada na mão.**
Em cada passo você cola uma mensagem no Claude e ele faz o serviço. Você só clica em "sim"
quando ele pedir permissão.

Depois disso, o Claude passa a raciocinar como parecerista trabalhista — pede documento,
desconfia de tese fácil, refaz cálculo — sem você ter que explicar nada em cada conversa.

---

## Antes: duas janelas que vão aparecer

Vão surgir caixas pedindo confirmação. Não tem susto nenhum, é assim mesmo:

1. **O próprio Claude pedindo permissão** para mexer em arquivos ou instalar coisa →
   clique em **sim**, sempre.
2. **Uma janela azul do Windows**, "Deseja permitir que este aplicativo faça alterações?"
   → **Sim**.

---

## Passo 1 — Abrir o Claude Code

Abra o Claude Code normalmente, com a conta do escritório.

Se ele perguntar qual pasta você quer abrir, escolha **Documentos**. Tanto faz qual seja —
é só pra ele ter onde trabalhar.

---

## Passo 2 — Pedir pro Claude instalar o Git

O Git é o programa que busca a skill. Provavelmente sua máquina não tem. Cole:

```
Estou no Windows e não sei se tenho o Git instalado. Verifique, e se não tiver, instale
pra mim usando o winget. Se o winget não funcionar, me diga em português simples o que eu
preciso fazer. No final, confirme qual versão do Git ficou instalada.
```

Pode demorar um ou dois minutos. Ele vai pedir permissão e o Windows também. Diga sim para
os dois.

**Acabou quando** ele disser um número de versão, tipo `git version 2.47.1`.

---

## Passo 3 — Pedir pro Claude criar a pasta

Cole:

```
Crie uma pasta chamada claude-skills dentro da minha pasta de usuário do Windows, e me
diga o caminho completo dela quando terminar.
```

**Acabou quando** ele responder um caminho tipo `C:\Users\seu-nome\claude-skills`.

> Repare que **não é** na Área de Trabalho. É de propósito: a Área de Trabalho aqui do
> escritório é sincronizada com o OneDrive, e o OneDrive muda o lugar dos arquivos
> sozinho — o que quebra a skill meses depois, do nada.

---

## Passo 4 — Pedir pro Claude baixar a skill

Cole:

```
Dentro da pasta claude-skills que você acabou de criar, baixe este repositório usando
git clone: https://github.com/ggvadv/skill-banco-inteligencia-trabalhista.git
```

**Acabou quando** ele disser que o download terminou.

---

## Passo 5 — Pedir pro Claude instalar a skill

Cole:

```
Agora instale a skill: copie o arquivo SKILL.md que está dentro da pasta que você acabou
de baixar para a minha pasta de skills pessoais do Claude Code, em
.claude\skills\banco-inteligencia-trabalhista\SKILL.md, sem alterar uma vírgula do
conteúdo. No final me diga se deu certo.
```

**Acabou quando** ele disser que copiou.

---

## Passo 6 — Fechar o Claude Code e abrir de novo

O Claude só enxerga uma skill nova na hora em que abre. Enquanto você não fechar e abrir,
não adianta nada.

Feche o programa **por inteiro**. Não é minimizar. Não é fechar a conversa. É fechar o
Claude Code mesmo — e abrir de novo.

Esse é, de longe, o motivo número um de "não funcionou".

---

## Passo 7 — Testar

Cole:

```
Vou analisar um processo trabalhista contra a Alpitel. Por onde a gente começa?
```

**Deu certo:** ele pergunta quais documentos você tem, fala em cartão de ponto, holerite e
CCT, e avisa que trabalha como se não houvesse testemunha.

**Não deu:** ele responde genérico, tipo "posso ajudar a resumir o processo". Volte ao
passo 6 — quase sempre é o Claude que não foi fechado direito.

---

## Pronto

A skill é sua e funciona **em qualquer pasta**, em qualquer processo. Não precisa ligar,
não precisa chamar por nome, não precisa nem lembrar dela: o Claude reconhece sozinho
quando o assunto é trabalhista.

---

## Quando o método for atualizado

Abra o Claude Code e cole:

```
Entre na pasta claude-skills\skill-banco-inteligencia-trabalhista, rode git pull para
baixar a versão nova, e depois copie de novo o SKILL.md por cima da minha skill pessoal
em .claude\skills\banco-inteligencia-trabalhista\SKILL.md.
```

Depois feche e abra o Claude Code. Sem isso, ele continua lendo a versão velha.

---

## Se travar

| O que acontece | O que fazer |
|---|---|
| Você clicou "não" numa permissão | Cole a mensagem do passo de novo e clique em **sim** |
| Ele diz que o `winget` não existe | Print da tela no grupo. A máquina precisa de atualização do Windows |
| No passo 7 ele responde genérico | Feche o Claude Code por inteiro e abra de novo |
| Ele diz que não achou o `SKILL.md` | Volte ao passo 4: o download não terminou |
| Qualquer outra coisa | Print da tela **inteira** no grupo. Não fique tentando adivinhar |

---

## Nota para quem distribui (não é para o advogado)

Esta skill é independente e funciona sozinha. O banco de dossiês do escritório —
`/modo-juridico`, `/estudo-empresa`, `/inicial`, `/replica` — é outra instalação, com
repositório e identidade por advogado, descrita no `IMPLANTACAO-MAQUINA.md`. Advogado
nenhum precisa fazer aquilo sozinho.

O repositório `ggvadv/skill-banco-inteligencia-trabalhista` é público: o download não pede
login. Não coloque nele nada de cliente — só o método.
