# LPI Essentials - LinuxTips

## Day 1

- Linus Benedict Torvalds: Em 1988, Linus foi admitido na Universidade de Helsinki. No mesmo ano, Andy Tanenbaum traz a público o SO MINIX, um derivativo do Unix para fins didáticos que rodava em computadores pessoais (PCs). No fim dos anos 1980, Linus toma contato com os PCs. Em 1990, Torvalds começa a aprender a linguagem de programação C em seus estudos. Em 1991, Linus compra um PC com um processador Intel 80386. Em 5 de janeiro de 1991, ele compra um Intel 80386-IBM PC antes de receber sua cópia MINIX, que, por sua vez, lhe permitiu começar a trabalhar no que se tornaria o Linux.

- Distribuições Linux
    - Debian
        - Ubuntu
        - Linux Mint
    - Redhat
        - CentOS
        - Suze

- Licenças: Definem os direitos e responsabilidades do uso de ferramentas
    - GPL v2 e v3
    - BSD
    - Apache
    - MIT
    - Creative Commons

- DFSG
    - Redistribuição livre
    - Inclusão de código fonte
    - Permitindo modificações e trabalhos derivados
    - Integridade do código fonte do autor (como um compromisso)
    - Sem discriminação contra pessoas ou grupos
    - Sem discriminação contra campos de atuação, como o uso comercial
    - A licença deve aplicar-se a todos aqueles para quem o programa é redistribuído
    - Licença não deve ser específico para um produto
    - Licença não deve restringir outro software

## Day 2

- Acessando uma máquina com Linux usando SSH
    - `ssh USUARIO@IP-OU-NOME-MAQUINA`
    - Verificando que você realmente está acessando outra máquina `cat /etc/debian_version` esse comando mostra a versão do Debian que está instalado
    - `USUARIO@SERVIDOR:~$` - `~` simboliza o diretório home do usuário `/home/USUARIO`
    - `USUARIO@SERVIDOR:~$` - `$` simboliza que quem está logado não é administrador do sistema, usuário comum.
    - `su - ` "su" significa "super user" para se tornar root/administrador do sistema
    - `root@SERVIDOR:~#` - diretório do usuário root `/root`
    - `root@SERVIDOR:~#` - `#` simboliza que quem está logado é root/administrador do sistema.
    - `cd /home/USUARIO` - `cd` comando para mudar de diretório

- 
