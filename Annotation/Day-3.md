# LPI Essentials - LinuxTips

## Day 3

- Comandos internos e externos do shell
    - `which COMANDO` para verificar se o comando está instalado na sua máquina
    - `man bash-builtins` para verificar todos os comandos instalados no bash
    - `echo "MENSAGEM"` para printar uma mensagem na tela
    - `echo $PATH` mostra onde procurar os binários para execução
    - `alias "COMANDO"` comandos para setar um "apelido" para um determinado comando, por exemplo executar um `ls -l` com apenas `ls`

- Comandos de manipulação de diretórios
    - Opções do comando `ls`
        - `ls` para listar arquivos e diretórios
        - `ls -a` opção `-a` serve para lista todos(all) arquivos, inclusive os arquivos ocultos que iniciam com um `.` no inicio do arquivo
        - `ls -l` opção `-l` serve para trazer mais informações sobre os arquivos.
        - `ls -h` opção `-h` serve para "humanizar" as informações, para deixar mais clara de leitura.
        - `ls -B` opção `-B` serve para não visualizar arquivos terminados com `~` no final do arquivo que simbolizam arquivos de backup.
        - `ls --color=auto` serve para diferenciar tipos de arquivos com cores
        - `ls -l PASTA -d` opção `-d` para mostrar detalhes de diretório
        - `ls -f` opção `-f` sem esse atributo a listagem de arquivos segue ordem alfabética, com o atributo `f` não.
        - `ls -F` opção `-F` com esse atributo a listagem segue ordem alfabética e com um separador entre diferentes tipos de arquivos.
        - `ls -g` opção `-g` oculta a coluna de dono dos arquivos
        - `ls -n` opção `-n` converte o nome e o grupo donos do arquivo para GUID e UUID que seria sua versão númerica.
        - `ls -L` opção `-L` oculta o tipo de arquivo com link simbólico
        - `ls -o` opção `-o` oculta a coluna de grupo dos arquivos
        - `ls -p` opção `-p` oculta o tipo de arquivo executável
        - `ls -t` opção `-t` lista os arquivos por data de criação mais recentes em primeiro
        - `ls -tr` opção `-tr` lista os arquivos por data de criação mais antigos em primeiro
        - `ls -X` opção `-X` lista os arquivos por extensão
        - `ls -R` opção `-R` lista de forma recursiva os arquivos e arquivos dentro de outros diretórios
    - Usos do comandos `cd`
        - `cd` para entrar em diretórios
        - `cd /home/USUARIO` - `cd` comando para mudar de diretório
        - `cd` somente comando `cd` ele entra no diretório do usuário que está logado
        - `cd -` colocando um `-` ele entra o último diretório acessado
        - `cd ~` como explicado o `~` simboliza o diretório home do usuário, então junto com o comando "cd" ele entra no diretório home do usuário.
        - `cd ..` Diretórios `.` e `..`. O `.` simboliza o diretório atual e o `..` simboliza o diretório anterior
        - `cd /` o `/` é o diretório "raiz" do Linux de onde se originam toda a ramificação de diretórios.
        - `cd /home/USUARIO` caminho absoluto, onde é descrito o caminho completo até o diretório ou arquivo desejado a partir do `/`
        - `cd USUARIO` caminho relativo, quando entramos em um diretório a partir de um em que estamos e não da raiz `/`
    - `pwd` mostra o diretório atual
    - Usos do comandos `mkdir`
        - `mkdir NOMEDAPASTA` para criar um diretório
        - `mkdir -p PASTA1 PASTA2` para criar mais de um diretório ao mesmo tempo
        - `mkdir -p PASTA1/PASTA1_1` para criar uma estrutura de diretórios sem que a raiz esteja criada
    - Usos do comandos `tree` 
        - `tree` comando para mostrar a "arvore" de diretórios
        - `tree - A` muda o formato apresentado pelo terminal
    - Usos do comandos `rmdir`
        - `rmdir` comando para apagar diretório vazios
        - `rmdir -p` comando para apagar arvore de diretórios vazios.
    - Usos do comandos `cat` e suas váriaveis
        - `cat NOMEARQUIVO` comando para visualizar conteúdo de um arquivo
        - `cat -n NOMEARQUIVO` comando para mostrar o número na frente de cada linha do conteúdo
        - `cat -s NOMEARQUIVO` junta e omite a apresentação de linhas em branco no arquivo
        - `cat -b NOMEARQUIVO` comando para mostrar o número na frente de cada linha do conteúdo somente em linhas que tenham conteúdo.
        - `cat -E NOMEARQUIVO` coloca um `$` ao final de cada linha para mostrar onde é seu final.
        - `cat -T NOMEARQUIVO` coloca um `ctrl+i` no lugar do tab.
        - `zcat NOMEARQUIVO.gz` para ver conteúdo de arquivos compactados com extensão `.gz`
        - `bzcat NOMEARQUIVO.bz2` para ver conteúdo de arquivos compactados com extensão `.bz2`
        - `xzcat NOMEARQUIVO.xz` para ver conteúdo de arquivos compactados com extensão `.xz`
        - `tac NOMEARQUIVO` mostra o conteúdo do arquivo do fim para o começo
        - `tac -s a NOMEARQUIVO` coloca uma letra "a" sempre que houver uma quebra de linha
    - Usos do comandos `rm`
        - `rm` comando sem atributos para excluir arquivos
        - `rm -r DIRETORIO` comando para excluir diretórios
        - `rm -rf` excluir arquivos e diretórios sem perguntar se tem certeza da exclusão
        - `rm -rf ARQUIVO1 ARQUIVO2` apagar vários arquivos ao mesmo tempo, sem perguntar.
        - `rm -rf *` apaga todos os arquivos e diretórios dentro do diretório onde está, menos arquivos ocultos
        - `rm -rf a*` apaga todos os arquivos iniciados com a letra "a"
    - Usos do comando `cp`
        - `cp` comando para copiar arquivos de lugar para o outro
            - `cp -l` copia arquivos criando hard links, espaço em disco continua o mesmo.
    - Usos do coamando `mv`
        - `mv` comando para mover arquivos de um lugar para outro

- Editores de texto no Linux
    - Nano
    - mcedit
    - vi (mais complexo)
    - vim (versão do vi com menos complexidade na edição de arquivos)

### Questões

1. Como remover um arquivo '-'?

:white_check_mark: rm '-'

:black_large_square: rm -f *dash*

:black_large_square: rm - --

:white_check_mark: rm -- -

---

2. Considerando a estrutura de Diretórios: _Diretorio17/Diretorio_17_1/Diretorio17_2/Diretorio_17_3/Arquivo.txt_, quando executar o comando `rmdir -p Diretorio17`, ele removerá com sucesso?

:black_large_square: Verdadeiro

:white_check_mark: Falso

---

3. Como tornar a cópia repetitiva de um diretório origem e destino mais rápida?

:black_large_square: Largar o Linux e instalar Windows, pois ele tem barra de progresso

:black_large_square: Upgrade de link de internet

:black_large_square: usar cp -f

:black_large_square: Trocar o HD por SSD

:white_check_mark: usar cp -u

---

4. Se voce precisa remover diretórios que contenham arquivos dentro, você usaria o rmdir?

:black_large_square: Verdadeiro

:white_check_mark: Falso

---

5. O comando 'rm -rf / data/arquivo.txt' é considerado um comando perigoso?

:black_large_square: O comando ignorarará / e removerá apenas o arquivo.txt

:white_check_mark: Sim, pois acidentalmente o usuário digitou um espaço entre o / e data, fazendo o rm -rf interpretar o argumento como 2 parametros (apagando o sistema de arquivos raíz). Felizmente distribuções novas pedem confirmação --no-preserve-root!

:white_check_mark: Sim, e vai apagar tudo em distribuições mais antigas que 2005

:black_large_square: O comando não é perigoso, vai deixar a máquina mais leve e com menos arquivos no disco