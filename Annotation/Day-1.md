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
        - A licença de código aberto mais tradicional é a GPL: GNU General Public License. Como o nome implica, essa licença está diretamente relacionada ao projeto GNU, mas pode ser utilizada por qualquer projeto de código aberto. A GPL gira em torno de quatro liberdades principais:
            - A liberdade de utilizar o programa para qualquer fim.
            - A liberdade de modificar o programa para atender suas necessidades.
            - A liberdade de compartilhar o programa com amigos e vizinhos.
            - A liberdade de compartilhar as modificações realizadas.
            - Modificações do software devem ser lançadas sob a mesma licença.
    - BSD
        - A Licença BSD, também conhecida como Licença de Distribuição de Software Berkeley, é um tipo de licença de código aberto que permite a livre utilização, modificação e distribuição de software.
            - O software pode ser utilizado para qualquer fim, incluindo o uso comercial.
            - O software pode ser modificado e distribuído sem qualquer restrição.
            - O código fonte deve ser incluído em qualquer distribuição do software.
            - Uma cópia da licença deve ser incluída em qualquer distribuição do software.
            - Uma exoneração de responsabilidade deve ser incluída em qualquer distribuição do software.
    - Apache
        - Esta licença já oferece bem mais flexibilidade aos usuários. Isso porque:
            - O código-fonte não precisa ser necessariamente público quando a distribuição do software é feita.
            - Modificações podem ser lançadas sob qualquer licença.
            - Mudanças feitas no código-fonte precisam ser documentadas.
            - Oferece a mesma proteção de uso de patente da GPLv3 que vimos acima.
            - Proíbe explicitamente o uso de nomes de marcas registradas encontrados no projeto.
    - MIT
        - Por fim, a licença MIT. Dentre todas as que listamos, ela é a mais permissiva de todas, além de ser a mais famosa. Comparado às demais, ela oferece pouquíssima proteção aos autores do software. Vamos dar uma olhada nas principais cláusulas:
            - O código-fonte não precisa ser necessariamente público quando a distribuição do software é feita.
            - Modificações podem ser lançadas sob qualquer licença.
            - Mudanças feitas no código-fonte não precisam ser documentadas.
            - Não tem nenhuma posição em relação ao uso de patentes.
    - Creative Commons
        - As licenças Creative Commons são licenças públicas que permitem distribuição gratuita de obras protegidas por direitos autorais. Ou seja, os direitos continuam existindo, mas você trafega por uma área cinzenta sem quebrar leis de proteção à propriedade intelectual.
            - CC0 (Domínio Público)
                - Esta é a casa da mãe Joana. Por meio dela, autores renunciam a qualquer direito reservado. Assim, você pode usar o conteúdo da maneira que quiser – e sem precisar dar créditos aos autores. Isso porque não há restrições sob legislação autoral ou banco de dados nesta licença. Ou seja, pode reproduzir, adaptar, criar em cima do conteúdo.
            - CC BY (Atribuição)
                - Já nesta, você precisa creditar a autoria. Feito isso, pode reproduzir, adaptar e/ou criar em cima do conteúdo à vontade. Por isso, esta é a mais flexível entre as licenças Creative Commons. É, também, a responsável por permitir uso dos conteúdos licenciados para fins comerciais.
            - CC BY-SA (Atribuição-CompartilhaIgual)
                - Por sua vez, esta licença exige créditos e licenciamento das novas criações sob termos idênticos. Ou seja, seja lá o que você fizer com o conteúdo, precisará disponibilizá-lo sob esta licença também. Assim como a anterior, está liberado distribuir, remixar, adaptar e/ou criar em cima do conteúdo à vontade – inclusive, para fins comerciais.
            - CC BY-ND (Atribuição-SemDerivações)
                - Se o conteúdo estiver sob esta licença, você só pode reproduzí-lo. Isto é, adaptações, remixes, criações em cima etc não podem rolar. Além disso, lembre-se de dar os créditos, porque, nesta licença, são obrigatórios.
            - CC BY-NC (Atribuição-NãoComercial)
                - Esta é, basicamente, a CC BY. Mas com uma condição: você não pode usar o conteúdo para fins comerciais. Fora isso, está liberado: reproduzir, adaptar e criar em cima, desde que você dê créditos ao(s) autor(es). E não precisa licenciar o que você fizer sob termos iguais.
            - CC BY-NC-SA (AtribuiçãoNãoComercial-CompartilhaIgual)
                - Por outro lado, esta é a CC BY com duas condições. Para começar, não pode usar o conteúdo para fins comerciais. Depois, precisa licenciá-lo sob os mesmos termos. E, claro, tem que creditar a autoria. Respeitando tudo isso, você pode adaptar, remixar e criar em cima do trabalho original.
            - CC BY-NC-ND (Atribuição-SemDerivações-SemDerivados)
                - Por fim, a mais restritiva entre as licenças Creative Commons, porque barra praticamente tudo. Nesta, você só pode reproduzir o conteúdo – ou seja, sem adaptações, remixes e criação em cima – com créditos e para fins não comerciais.
                
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