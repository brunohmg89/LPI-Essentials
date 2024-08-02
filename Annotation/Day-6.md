# LPI Essentials - LinuxTips

## Day 6

- Discos e partições
    - `/dev` Dispositivos do sistema
        - sda: primeiro disco fisico
            - sda1: primeira partição primária
            - sda2: segunda partição primária (no máximo 4)
            - sda5: partição lógica, subdivisões de uma partição primária que desse caso seria do sda1. E assim por diante. 
        - sdb - segundo disco fisico e assim por diante
    - `fdisk` comando de particionador do sistema
        - `fdisk -l` lista os discos e partições do sistema
        - `fdisk /dev/sdb` para formatar e particionar um novo disco
            - `m` para mostrar todas as opções do `fdisk`
            - `p` para "printar" as informações do disco
            - `o` rótulo padrão (DOS), tem as opções `g` (GPT), `G` (SGI) e `s` (SUN)
            - `n` para criar uma partição
                - `p` para criar uma partição primária
                - `1-4` escolher entre 1 e 4 para o número da partição
                - `Enter` para escolher o primeiro bloco da partição, valor padrão
                - `+500M` escolher a quantidade em Mega que terá a nova partição
            - `t` para alterar o tipo da partição criada
                - `2` escolher o número da partição (1-4)
                - `L` lista todos os tipos de formatos que a partição pode ser alterada
                - `82` código para formatação de partição para o tipo SWAP
            - `w` para gravar as alterações feitas no disco
    - `mkfs.ext4 /dev/sb1` comando para formatar uma partição para o tipo EXT4
    - `mkswap /dev/sb2` comando para formatar uma partição para o tipo SWAP
    - `wipefs -a /dev/sdb` comando para apagar toda formatação realizada no disco
    - `gdisk /dev/sdb` comando para formatar um disco no rótulo GPT
        - `?` para listas as opções disponivel pelo comando `gdisk`
        - `o` criar uma nova partição do tipo GPT
        - `i` para listar partições caso existam
        - `n` para criar uma nova partição
            - `1-128` escolher entre 1 e 128 para o número da partição
            - `Enter` para escolher o primeiro bloco da partição, valor padrão
            - `+500M` escolher a quantidade em Mega que terá a nova partição
            - `L` para listar os tipos de formatação para formatar a nova partição
        - `w` para gravar as alterações feitas no disco
        - `b` para criar um backup das configurações das partições
        - `v` para verificar se existem problemas nas partições
        - `x` modo avançado de configurações
    - `parted /dev/sdb` outro comando de particionamento de disco
        - `p` para "printar" as informações do disco
        - `help` para ver as opções que podemos utilizar
        - `mklabel msdos` para criar um rótulo MSDOS
        - `mkpart` para criar partições
            - `primary` para criar uma partição primária
            - `ext4` formato da partição
            - `1` inicio da partição em Mega
            - `500` final da partição em Mega
        - `set 1 boot on` para informar que a primeira partição (1) será responsável pelo boot do sistema
        - `unit mB` para alterar a visualização do tamanho das partições para Mega 
        - `rm` para remover partições, primeiro as lógicas
    - `cfdisk /dev/sdb` outro comando de particionamento de disco
        - O `cfdisk` é um comando mais interativo podendo utilizar as setas entre as opções disponiveis

- Planejamento de partições
    - Melhores práticas e recomendações para inicializar um disco. Planejar as partições dependendo da utilização do Desktop ou Servidor

- Migração para partição
    - `/etc/fstab` arquivo com as configurações de montagem das partições
        - Campos do arquivo `fstab`
            - `file system` partição que será montada (sda2, sdb5)
            - `mount point` qual diretório será montado (var, home)
            - `type` tipo de formatação do disco (ext3, ext4)
            - `options`
                - `defautls` opções padrão
                - `noatime` para não atualizar o "access time" dos arquivos
                - `nodiratime` para não atualizar o "access time" dos diretórios
                - `norelatime` para não atualizar o "access time" dos inodes
                - `noexec` não permite execução de binários dentro da partição montada
                - `nodev` não permite execução de dispositivos dentro da partição montada
                - `rw` montar partição como leitura e escrita
            - `dump` (0-1) se a partição fará dumps (bkps)
            - `pass` (0-1) se a partição fará checagem em toda inicialização 
    - `mklost+found` para criar uma pasta "lost+found" em um diretório
    - `mount` comando para montar dispositivos
        - `mount -o remount /var` remonta a partição `/var` relendo as configurações contidas no arquivo fstab
        - `mount -o remount,rw /var` remonta a partição como leitura e escrita
    - `umount` para desmontar dispositivos
        - `umount /var` desmonta a partição "/var"
    - `lsof` lista arquivos que estão em uso pelo sistema
        - `lsof -t /var` lista somente os arquivos em uso pelo diretório informado
    
### Questões

1. Qual dos sistemas de arquivos abaixo possui a verificação por erros mais rápida?

:black_large_square: ext2 - Porque não possui journaling, o que deixa a gravação mais lenta quando encontra erros

:black_large_square: ext3 - Porque possui journaling e o tamanho é limitado a 32Tb

:white_check_mark: ext4 - Porque possui journaling e extents, e possui mapeamento de blocos usado no fim de cada grupo de tabela de inodes

:black_large_square: /dev/null

---

2. Qual o tamanho recomendado para a partição 'Bios Inicialização' que será a primeira criada em um disco GPT em sistemas utilizando UEFI?

:black_large_square: 1Gb

:white_check_mark: 1Mb

:black_large_square: 10Mb

:black_large_square: 100Mb

:black_large_square: 10Gb

---

3. Para onde são copiados arquivos enviados para /dev/null?

:black_large_square: Ele cria o arquivo de cache /dev/null que pode ser usado para recuperação após o reboot

:white_check_mark: Para nenhum lugar, é semelhante ao enviar dados para um buraco negro, onde tudo desaparece

:black_large_square: Ele cria um arquivo /dev/null que é persistente entre reboots

:black_large_square: /dev/null é um dispositivo onde pode ser usado links simbólicos e copiam o conteúdo para o arquivo alvo

---

4. Qual o tamanho máximo de um volume ext4

:white_check_mark: 1Eb

:black_large_square: 2Tb

:black_large_square: 16Tb

:black_large_square: 32Tb