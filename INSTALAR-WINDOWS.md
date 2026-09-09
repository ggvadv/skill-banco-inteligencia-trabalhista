# Instalar a skill Banco de Inteligência Trabalhista — Windows

Para o advogado. Não precisa saber nada de programação: são seis passos, uns 10 minutos,
e só se faz uma vez por computador.

**No fim disso, o Claude passa a raciocinar como parecerista trabalhista** — pede documento,
desconfia de tese fácil, refaz cálculo — sem você precisar explicar nada em cada conversa.

---

## Antes de começar

- **Claude Code instalado e com a conta do escritório logada.** Se ainda não estiver,
  pare aqui e fale com o Dr. Glauco: a instalação do Claude Code é outro roteiro.
- **Nada de senha na sua mão.** O download pede login do GitHub uma única vez, na conta
  `ggvadv`. Quem digita é quem implanta, não você.
- **Onde tudo acontece:** no PowerShell. Para abrir, tecla `Windows` → digite `powershell`
  → `Enter`. Não precisa ser "como administrador".

---

## Passo 1 — Instalar o Git

O Git é o programa que baixa a skill. Duas maneiras; a primeira é mais rápida.

**Jeito rápido.** No PowerShell:

```
winget install --id Git.Git -e --source winget
```

Se o Windows pedir confirmação, aceite. Ao terminar, **feche o PowerShell e abra de novo** —
sem isso o Windows não enxerga o programa novo.

**Jeito manual**, se o comando acima não existir na sua máquina:

1. Abra `https://git-scm.com/download/win` e baixe o **64-bit Git for Windows Setup**.
2. Execute o arquivo baixado e vá clicando **Next**. Os padrões estão certos.
3. Duas telas merecem atenção:
   - *"Choosing the default editor"* → troque o **Vim** por **Notepad**. O Vim trava gente
     experiente; não vale o risco.
   - *"Adjusting your PATH environment"* → mantenha a opção do **meio**, a recomendada
     (*Git from the command line and also from 3rd-party software*). É ela que faz o
     passo seguinte funcionar.
4. **Finish**, feche o PowerShell e abra de novo.

**Conferir:**

```
git --version
```

Tem de responder algo como `git version 2.47.1`. Qualquer número serve. Se disser que o
comando não é reconhecido, veja *Problemas comuns* no fim.

---

## Passo 2 — Criar a pasta

```
cd $HOME
```

```
mkdir claude-skills
```

```
cd claude-skills
```

`$HOME` é a sua pasta de usuário, `C:\Users\seu-nome`. A pasta fica em
`C:\Users\seu-nome\claude-skills`.

**Não use a Área de Trabalho.** Na maioria das máquinas do escritório ela está sincronizada
com o OneDrive, e o OneDrive muda o caminho dos arquivos sozinho — o que quebra a
atualização da skill meses depois, do nada.

Se o `mkdir` reclamar que a pasta já existe, ignore e siga para o `cd`.

---

## Passo 3 — Baixar a skill

```
git clone https://github.com/ggvadv/skill-banco-inteligencia-trabalhista.git
```

**Na primeira vez, e só nela, abre uma janela do GitHub pedindo login.** Escolha
*Sign in with your browser* e entre com a conta `ggvadv`. O Windows guarda esse acesso;
nas próximas vezes não pergunta mais.

**Conferir:**

```
dir .\skill-banco-inteligencia-trabalhista
```

Tem de aparecer o arquivo `SKILL.md`. Ele é a skill inteira — um arquivo de texto com o
método de trabalho escrito por extenso.

> **Não abra o `SKILL.md` no Word.** O Word reescreve aspas, acentos e quebra o cabeçalho
> do arquivo, e a skill some da lista sem dar erro. Se quiser ler, abra no Bloco de Notas
> — ou peça pro Claude te explicar.

---

## Passo 4 — Pedir pro Claude instalar

1. Abra o **Claude Code**.
2. Abra a pasta `C:\Users\seu-nome\claude-skills\skill-banco-inteligencia-trabalhista`.
3. Cole exatamente este pedido:

```
Instale a skill desta pasta como skill pessoal do Claude Code: crie a pasta
.claude\skills\banco-inteligencia-trabalhista dentro do meu perfil de usuário e copie
o SKILL.md daqui para lá, sem alterar uma vírgula do conteúdo. No final, me mostre o
caminho completo do arquivo copiado.
```

4. O Claude vai pedir permissão para rodar os comandos. Autorize.

**Conferir:** o caminho que ele mostrar no fim tem de ser, com o seu nome no lugar de
`seu-nome`:

```
C:\Users\seu-nome\.claude\skills\banco-inteligencia-trabalhista\SKILL.md
```

Duas coisas nesse caminho não podem mudar: a pasta começa com **ponto** (`.claude`) e o
arquivo se chama **SKILL.md**, em maiúsculas. Fora disso, o Claude não acha.

---

## Passo 5 — Reiniciar o Claude Code

O Claude lê as skills **uma vez, ao abrir**. Enquanto você não reiniciar, ele não sabe que
a skill existe — e esse é, de longe, o motivo número um de "não funcionou".

Feche o Claude Code por inteiro (não só a janela ou a aba; se estiver no terminal, digite
`/exit`). Abra de novo.

---

## Passo 6 — Testar

Pergunte, na pasta que você quiser:

```
Quais skills você tem disponíveis?
```

`banco-inteligencia-trabalhista` tem de aparecer na resposta. Se não aparecer, o problema
está no passo 4 ou no 5.

Agora o teste que vale: peça uma análise real.

```
Vou analisar um processo trabalhista contra a Alpitel. Por onde a gente começa?
```

**Certo:** ele pergunta quais documentos você tem, fala em cartão de ponto, holerite, CCT,
avisa que trabalha como se não houvesse testemunha.
**Errado:** ele responde genérico, tipo "posso ajudar a resumir o processo". Aí a skill não
carregou — volte ao passo 5.

---

## Atualizar depois

Quando o método for revisado, cada máquina roda:

```
cd $HOME\claude-skills\skill-banco-inteligencia-trabalhista
```

```
git pull
```

E repete os passos 4 e 5 — copiar por cima e reiniciar. O `git pull` sozinho não atualiza
a skill: ele atualiza a cópia baixada, não a que o Claude lê.

---

## Problemas comuns

| O que aparece | Por quê | O que fazer |
|---|---|---|
| `git : O termo 'git' não é reconhecido` | O PowerShell foi aberto antes do Git terminar de instalar | Feche e abra o PowerShell. Se persistir, reinstale mantendo a opção do meio na tela do PATH |
| `winget : O termo 'winget' não é reconhecido` | Windows desatualizado | Use o jeito manual do passo 1 |
| O clone pede usuário e senha e recusa a senha | O GitHub não aceita mais senha de conta no terminal | Feche, rode o comando de novo e escolha *Sign in with your browser* |
| `repository not found` | Está logado numa conta sem acesso ao repositório | Chame quem implantou: precisa entrar com a conta `ggvadv` |
| A skill não aparece na lista | Não reiniciou o Claude Code | Passo 5. Se já reiniciou, confira o caminho do passo 4 letra por letra |
| A skill aparece na lista mas o Claude ignora | O `SKILL.md` foi aberto e salvo no Word | Apague a pasta `.claude\skills\banco-inteligencia-trabalhista` e refaça os passos 4 e 5 |
| O antivírus bloqueia a instalação do Git | Política da máquina | TI. Não contorne |

---

## O que este roteiro **não** faz

Ele instala **só a skill de inteligência trabalhista**, que funciona em qualquer pasta e
não depende de mais nada.

O banco de dossiês do escritório — `/modo-juridico`, `/estudo-empresa`, `/inicial`,
`/replica` — é outra instalação, com repositório e identidade por advogado. O roteiro dela
é o `IMPLANTACAO-MAQUINA.md`, neste mesmo repositório, e quem executa é o Dr. Glauco ou o TI.
