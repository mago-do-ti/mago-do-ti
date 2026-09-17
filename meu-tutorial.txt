FIZ ESTE PASSO A PASSO PARA A CRIAÇÃO DE UM SNAKEGAME NO PERFIL DO GITHUB

#####################################################
### Caminho para criar o repositório corretamente ###
#####################################################
> foto de perfil > Repositories > New > seu mesmo nome de usuário (ex.: mago-do-ti) > em Add readme clique no botão off para ficar on > role para baixo > Create repository

#################################################################################
### Caminho para criar as pastas e o arquivo yml dentro do repositório criado ###
#################################################################################
> Botão + ou Add File (do lado do botão verde com o nome Code) > Create new file > no campo Name your file copie e cole isso: .github/workflows/snake.yml

##################################################################
### Caminho para criar, salvar e executar o código da cobrinha ###
##################################################################
+--------------------------------------------------------------------------------------------+
| Copie o código abaixo e cole no editor de texto do arquivo snake.yml e substitua onde está |
| escrito seu-nome-de-usuario pelo seu nome de usuário do GitHub (ex.: mago-do-ti):          |
+--------------------------------------------------------------------------------------------+

name: Generate Snake

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:
  push:
    branches:
    - main

jobs:
  generate:
    permissions:
      contents: write
    runs-on: ubuntu-latest
    timeout-minutes: 5

    steps:
        - name: generate-github-user-contribution-grid-snake-animation
          uses: Platane/snk/svg-only@v3
          with:
            github_user_name: mago-do-ti
            outputs: |
              dist/github-contribution-grid-snake.svg?color_snake=#00FF66&color_dots=#161B22,#0E4429,#006D32,#26A641,#39D353
    
        - name: push github-contribution-grid-snake.svg to the output branch
          uses: crazy-max/ghaction-github-pages@v4
          with:
            target_branch: output
            build_dir: dist
          env:
            GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

+--------------------------------------------+
| Observações do código a cima a considerar: |
+--------------------------------------------+
Essa é a tabulação correta de cada linha em relação ao marco zero da linha caso precise:
01: 0 tab
03: linha vazia
03: 0 tab
04: 1 tab
05: 2 tab
06: 1 tab
07: 1 tab
08: 2 tab
09: 2 tab
10: linha vazia
11: 0 tab
12: 1 tab
13: 2 tab
14: 3 tab
15: 2 tab
16: 2 tab
17: linha vazia
18: 2 tab
19: 4 tab
20: 5 tab
21: 5 tab
22: 6 tab
23: 6 tab
24: 7 tab
25: linha vazia
26: 4 tab
27: 5 tab
28: 5 tab
29: 6 tab
30: 6 tab
31: 5 tab
32: 6 tab

+-------------------------------------------------------------------------------------------------------+
| Após copiar e colar o código a cima corretamente, prossiga com este caminho para salvar as alterações |
+-------------------------------------------------------------------------------------------------------+
> Botão verde Commit changes (não altere nada) > Commit changes (novamente)

+-----------------------------------------------------------------------------+
| Agora execute este código dentro da aba Actions seguindo o seguinte caminho |
+-----------------------------------------------------------------------------+
> Actions (lá em cima)> .github/workoverflows/snake.yml > Run workflow > Run workflow (aguarde até a bolinha amarela ficar verde)

+----------------------------------------------------------------------------+
| Agora você deve linkar este código ao Readme.md seguindo seguinte caminho |
+----------------------------------------------------------------------------+
> Code > Readme.md > [Ícone de lápis] > Adicione o código a seguir substituindo onde esta escrito seu-nome-de-usuario pelo seu nome de usuário 

![Snake animation](https://raw.githubusercontent.com/seu-nome-de-usuario/output/github-contribution-grid-snake.svg)

> Commit changes

- E para ver o resultado, clique na sua foto de perfil, clique em profile e espere uns 2 ou 3 minutos para apertar F5 e recarregar a página .

######################################################################################
### Caso queira editar as cores é só editar o arquivo snake.yml da seguinte forma: ###
######################################################################################
Na aba Code de seu repositório siga o seguinte caminho para editar o arquivo snake.yml
> .github/workflows > snake.yml > [Ícone de lápis] > agora edite os valores da linha de código depois de onde está escrito outputs: |

Aqui está a linha de código citado a cima:

outputs: |
dist/github-contribution-grid-snake.svg?color_snake=#00FF66&color_dots=#161B22,#0E4429,#006D32,#26A641,#39D353

No parâmetro color_dots, a lista de cores hexadecimal segue estritamente a ordem de intensidade das contribuições do seu gráfico do GitHub, indo do dia sem nenhuma atividade até o dia com maior número de commits.

E aqui está o explicado o que cada um dos valores em hexadecimal das duas linhas a cima representam:

O código é dividido em duas variáveis principais em cada linha: color_snake (a cor da cobrinha) e color_dots (a sequência de 5 cores para os quadros de contribuição do menor para o maior nível).

linha de código: dist/github-contribution-grid-snake.svg?color_snake=#00FF66&color_dots=#161B22,#0E4429,#006D32,#26A641,#39D353

color_snake=#00FF66: Verde Neon (a cor do corpo da cobrinha).

color_dots=:

#161B22: Cinza muito escuro (fundo/dias sem nenhuma contribuição).

#0E4429: Verde bem escuro (nível 1 — poucas contribuições).

#006D32: Verde médio (nível 2 — contribuições moderadas).

#26A641: Verde claro (nível 3 — muitas contribuições).

#39D353: Verde brilhante (nível 4 — máximo de contribuições no dia).

- Dica de Design: Para um efeito visual bonito, a primeira cor de color_dots deve ser bem escura (ou neutra), pois ela cobre quase todo o gráfico representando os dias em que você não codificou.
