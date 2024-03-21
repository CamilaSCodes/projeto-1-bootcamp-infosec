# 1º Projeto Prático - Bootcamp em Segurança da Informação

## Criando uma rede segura com o Cisco Packet Tracer para o Programa Desenvolve do Grupo Boticário

Este repositório contém uma rede criada no Cisco Packet Tracer, juntamente com sua documentação correspondente, como componente do primeiro projeto prático do Bootcamp em Segurança da Informação do Programa Desenvolve. O propósito primordial deste projeto é proporcionar uma experiência prática, complementar às 8 semanas iniciais de cursos na plataforma Alura.

### Briefing do projeto

O projeto visa criar uma rede para um evento de programação em uma universidade, onde cada grupo de estudantes realizará provas diferentes em salas separadas. O evento contará com a presença de três categorias de pessoas: alunos, professores e funcionários.

As provas serão realizadas em computadores conectados à internet cabeada, e tanto professores quanto funcionários devem ter acesso exclusivo a servidores com informações direcionadas a eles, garantindo a realização planejada do evento. Professores terão acesso tanto a um computador quanto a um laptop, permitindo mobilidade na sala e comunicação livre com os alunos.

Os fiscais e seguranças, dois tipos de funcionários distintos, precisarão se locomover entre as salas e, portanto, devem contar com conexão de internet wireless. Além disso, o evento requer funcionários de recepção com acesso a uma rede completamente sem fio para resolver problemas com agilidade.

Outro requisito essencial é um sistema de telefonia que deve funcionar adequadamente.

### Requisitos de rede

* Acesso à internet cabeada e wireless
* Servidores com políticas de acesso
* Conexão de mais de 600 computadores
* Sistema de telefonia

### Dispositivos

* 3x Ponto de Acesso Wi-Fi WRT300N
* 3x Switch 2950-24
* 2x Roteador 1841
* 6x PC
* 5x LapTop
* 2x Server
* 1x Smartphone
* 1x Impressora

### Topologia de rede
#### Topologia lógica
![topologia lógica](https://github.com/CamilaSCodes/projeto-1-bootcamp-infosec/blob/main/imagens/topologia%20logica.png?raw=true)
#### Topologia física
![topologia física](https://github.com/CamilaSCodes/projeto-1-bootcamp-infosec/blob/main/imagens/topologia%20fisica.png?raw=true)

### Vlans

| ID | VLAN | Descrição | 
| ------------- | ------------- | ------------- |
| 1 | default | Vlan Padrão (para gerenciamento do switches) |
| 10 | alunos | Rede dos alunos (comunicação entre alunos e acesso à web, sem privilégios) |
| 20 | professores | Rede dos professores (acesso à web e informações privadas para professores) |
| 30 | funcionários | Rede dos funcionários (acesso à web e informações privadas para funcionários) |

### 
