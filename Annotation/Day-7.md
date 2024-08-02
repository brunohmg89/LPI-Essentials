# LPI Essentials - LinuxTips

## Day 7

- Hardware e dispositivos de expansão
    - `/proc/interrupts` sinais de interrupção, para configuração de periféricos
    - `/proc/ioports` sinais de periféricos, por exemplo como teclado
    - `irqtop` comando para verificar as interrupções de CPU em tempo real

- Listando e identificando dispositivos
    - `lspci` comando para listar todos os periféricos instalado no computador
        - `lspci -vv` lista mais detalhes dos dispositivos conectados
    - `lsusb` comando para listar dispositivos USB
    - `lshw` comando para listar hardware do computador

- Firmwares Binárias
    - `/lib/firmware` diretórios onde ficam os firmwares instaladas do sistema
    - `/etc/apt/sources.list` arquivos que contém os servidores nos quais o sistema operacinal irá procurar atualizações e aplicativos a serem instalados no sistema
        - `deb http://deb.debian.org/debian/ buster main contrib non-free` conteúdo do arquivo `sources.list` adicionando as palavras "contrib" e "non-free" ele autoriza a pesquisa e a instalação de pacotes desses pontos que não são "padrões" de distruibuição 
        - `apt-get update` atualiza os pacotes do sistema usando como padrão a lista de servidores do arquivo `sources.list`
        - `apt-cache search firmware-linux-nonfree` comando para pesquisar pacotes nos servidores do sistema

- ACPI e teclas de gerencia de energia
    - `acpid` comando para gerenciamento de energia de um computador, por exemplo configurar o desligamento de um server apertando o botão "power".
    - `/etc/acpi/` diretório onde se encontra as configurações de desligamento "apertando" o botão power de uma máquina
    - `/etc/systemd/logind.conf` arquivo utilizado pelo `systemd` onde pode ser alterado a forma de desligamento do servidor.

### Questões

1. O que a IRQ faz?

:black_large_square: Envia dados para o disco

:black_large_square: Envia dados para a memória

:white_check_mark: Faz a CPU parar o que estiver fazendo para requisitar atenção de um dispositivo

:black_large_square: Faz a CPU acelerar a performance de I/O

---

2. O que é uma porta de I/O

:white_check_mark: Faz a comunicação entre a CPU e dispositivos

:black_large_square: Interrompe a entrada e saída da CPU para envio de dados

:black_large_square: Permite conectar periféricos ao computador

:black_large_square: Permite expandir a capacidade do computador para até 127 dispositivos USB

---

3. Onde você pode visualizar as portas de I/O no Linux?

:black_large_square: /proc/devices

:black_large_square: /proc/iops

:white_check_mark: /proc/ioports

:black_large_square: /proc/iodevices

---

4. Como você pode visualizar irqs no Linux

:white_check_mark: /proc/interrupts

:black_large_square: /proc/irqs

:black_large_square: /proc/irqports

:black_large_square: /sys/interrupts

---

5. A ferramenta top pode ser usada para visualizar IRQs

:white_check_mark: Verdadeiro

:black_large_square: Falso

---

6. Caso possua um notebook em que a placa WIFI e bluetooth não funcionam, será necessário pesquisar por firmwares adicionais

:white_check_mark: Verdadeiro

:black_large_square: Falso

---

7. Existem conflitos de IRQ em placas PCI e sistemas APIC

:black_large_square: Verdadeiro

:white_check_mark: Falso

---

8. IRQs são infinitas e não afetam a performance da máquina

:black_large_square: Verdadeiro

:white_check_mark: Falso

---

9. 0x170 é um exemplo de:

:black_large_square: IRQ

:black_large_square: DMA

:white_check_mark: ioport

:black_large_square: dispositivo de disco