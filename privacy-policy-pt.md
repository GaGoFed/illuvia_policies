# Illuvia — Política de privacidade

**Última atualização: 6 de agosto de 2026 · Aplica-se ao Illuvia 1.0.0 para Windows**

## Em resumo

O Illuvia não recolhe nada. Não tem servidores, nem contas, nem ferramentas de
análise, e não abre qualquer ligação de rede por iniciativa própria. Tudo o que
escreve fica em ficheiros no seu PC, sob a sua conta do Windows.

## O que o Illuvia guarda, e onde

Tudo o que introduz — tarefas, listas, transações, contas, planos de pagamento,
desejos, veículos, definições — é escrito em ficheiros dentro da sua pasta de
utilizador:

```
%APPDATA%\Gagofed\Illuvia\database\
```

É essa a pasta, quer o Illuvia venha da Microsoft Store quer seja executado a
partir de uma compilação normal: os dados não vivem dentro do pacote instalado.

Esses ficheiros estão **encriptados em disco** com AES-256. A chave é gerada no
seu PC no primeiro arranque e guardada no Gestor de Credenciais do Windows,
protegida para a sua conta do Windows (DPAPI). Nunca deriva do seu PIN ou
palavra-passe, e nunca sai da máquina. Quem copiasse os ficheiros para outro PC,
ou tentasse lê-los a partir de outra conta do Windows, não conseguiria
desencriptá-los.

O Illuvia escreve também um registo de diagnóstico em texto simples:

```
%APPDATA%\Gagofed\Illuvia\logs\illuvia.log
```

Regista o que a aplicação fez — que módulo carregou, quantos registos leu, o que
dizia um erro — para que um problema possa ser compreendido mais tarde. Está
limitado a 5 MB com até três ficheiros rodados, não é enviado para lado nenhum e
pode apagá-lo quando quiser. Não está encriptado: se o enviar para pedir apoio,
leia-o primeiro.

## O que o Illuvia não faz

- **Nenhuma recolha de dados.** Sem estatísticas de utilização, sem relatórios
  de falhas, sem análise, sem publicidade, sem definição de perfis, sem
  identificadores de qualquer tipo.
- **Nenhuma conta.** Não há nada para registar, e não é preciso um endereço de
  e-mail para usar a aplicação.
- **Nenhuma rede.** O pacote da aplicação não declara qualquer capacidade de
  ligação à Internet e a aplicação não faz pedidos. Funciona com o cabo de rede
  desligado.
- **Nenhum terceiro.** Nada do que introduz é partilhado com quem quer que seja,
  porque não há ninguém com quem partilhar.

## As duas vezes em que algo sai da aplicação

**Abrir uma ligação.** Se guardar a ligação de uma loja num desejo, ou usar a
ligação de donativo, ao tocar nela o endereço passa para o seu navegador
predefinido. A partir daí está nesse site, sob a política de privacidade dele,
não sob esta. O Illuvia não descarrega a página.

**Fazer uma cópia de segurança.** Uma cópia é um único ficheiro com tudo lá
dentro, guardado onde escolher. Como sai do computador é consigo:

- **Exportar sem palavra-passe** (predefinição). O ficheiro é escrito como JSON legível. É
  a única forma de inspecionar uma cópia ou de a abrir com algo que não seja o
  Illuvia, e é tão privado quanto o sítio onde o puser. Se guardou as credenciais
  de um serviço num plano de pagamento (ver abaixo), o Illuvia avisa antes de
  escrever: ali estão em claro.
- **Exportar com palavra-passe.** O ficheiro é selado com AES-256, com uma chave
  derivada da sua palavra-passe (Argon2id). Pode ser restaurado em qualquer
  máquina, e sem essa palavra-passe não abre: ninguém a pode recuperar por si.

As cópias que o Illuvia escreve para si próprio — as automáticas, e a cópia de
segurança feita antes de um restauro ou de uma importação — estão sempre seladas
com a chave deste PC. Ficam na pasta do Illuvia, e desinstalar a aplicação
deixa-as lá com tudo o resto.

## As palavras-passe que guarda para outros serviços

Um plano de pagamento pode conter o nome de utilizador e a palavra-passe do
serviço que paga — a sua conta da luz, uma subscrição — porque é aí que os
procura. São guardados como qualquer outro campo: na base de dados, cifrados em
repouso, só neste PC. Nunca são enviados para lado nenhum, e o Illuvia não tem
forma de os usar.

Daqui seguem duas coisas. Viajam dentro de uma cópia de segurança, e é isso que
permite que um restauro reponha os seus dados como estavam; e por isso uma
**exportação sem palavra-passe** contém-nos em claro, razão pela qual o Illuvia avisa
antes de escrever uma.

## O bloqueio da aplicação

O PIN ou a palavra-passe que abrem o Illuvia são outra coisa, e nunca são
guardados. O que é guardado é
um hash Argon2id, com um sal aleatório, no Gestor de Credenciais do Windows,
junto à chave de encriptação. O Windows Hello, se o ativar, é gerido
inteiramente pelo Windows: o Illuvia recebe apenas um sim ou um não e nunca vê
dados biométricos.

## Apagar os seus dados

Definições → Segurança → *Esvaziar todos os módulos* elimina tudo o que introduziu.
Ao lado, *Apagar todos os dados* remove também a chave de encriptação e a credencial: é o
que faz o percurso «esqueci-me do PIN».

**Desinstalar o Illuvia não apaga os seus dados.** O Windows remove a aplicação e
deixa as pastas indicadas acima onde estão, de modo que ao reinstalar encontra
tudo como deixou. Se quiser que os dados desapareçam também, use primeiro um dos
dois comandos, ou apague a pasta `%APPDATA%\Gagofed\Illuvia\`: lá dentro estão a base de
dados, o registo e as cópias automáticas.

As cópias de segurança que exportou não são tocadas por nenhuma destas
operações: só o utilizador sabe onde estão.

## Menores

O Illuvia é um organizador pessoal de uso geral. Não se dirige a crianças e não
recolhe informação de ninguém, de nenhuma idade.

## Alterações a esta política

Se uma versão futura do Illuvia vier a mudar o que faz com os seus dados, esta
página será atualizada antes de essa versão ser publicada, e a alteração será
descrita nas notas de lançamento.

## Contacto

Questões sobre esta política: **illuvia.dev@gmail.com**
