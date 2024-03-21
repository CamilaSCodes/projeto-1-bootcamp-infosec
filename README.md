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

* 3x Ponto de Acesso Wi-Fi 
* 3x Switch 
* 2x Roteador 
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

### Ativos de rede, esquemas de endereçamento e conexões
#### Roteadores

<table>
<thead>
  <tr>
    <th rowspan="2">Nome</th>
    <th rowspan="2">Modelo</th>
    <th rowspan="2">Interface</th>
    <th rowspan="2">IP / Máscara de sub-rede</th>
    <th colspan="2">Dispositivo conectado</th>
  </tr>
  <tr>
    <th>Nome</th>
    <th>Interface</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Provedor de serviços</td>
    <td>1841</td>
    <td>S0/1/0</td>
    <td>150.1.1.1/30</td>
    <td>Router0</td>
    <td>S0/1/0</td>
  </tr>
  <tr>
    <td rowspan="6">Router0</td>
    <td rowspan="6">1841</td>
    <td>S0/1/0</td>
    <td>150.1.1.2/30</td>
    <td>Prestador de serviços</td>
    <td>S0/1/0</td>
  </tr>
  <tr>
    <td>F0/0</td>
    <td>N/A</td>
    <td>Switch_C</td>
    <td>Fa0/0</td>
  </tr>
  <tr>
    <td>F0/0.1</td>
    <td>172.16.0.1/23</td>
    <td>N/A</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>F0/0.2</td>
    <td>172.16.2.1/23</td>
    <td>N/A</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>F0/0.3</td>
    <td>172.16.4.1/23</td>
    <td>N/A</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>F0/4.4</td>
    <td>172.16.6.1/23</td>
    <td>N/A</td>
    <td>N/A</td>
  </tr>
</tbody>
</table>

#### Switches

<table>
<thead>
  <tr>
    <th rowspan="2">Nome</th>
    <th rowspan="2">Modelo</th>
    <th rowspan="2">Interface</th>
    <th colspan="3">Dispositivo conectado</th>
  </tr>
  <tr>
    <th>Nome</th>
    <th>Interface</th>
    <th>IP / Máscara de Sub-rede</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td rowspan="6">Switch_A</td>
    <td rowspan="6">2950-24</td>
    <td>Fa0/1</td>
    <td>Aluno_A</td>
    <td>Fa0</td>
    <td>172.16.0.2/23</td>
  </tr>
  <tr>
    <td>Fa0/2</td>
    <td>Professor_A</td>
    <td>Fa0</td>
    <td>172.16.2.3/23</td>
  </tr>
  <tr>
    <td>Fa0/3</td>
    <td>Funcionario_A</td>
    <td>Fa0</td>
    <td>172.16.4.3/23</td>
  </tr>
  <tr>
    <td>Fa0/4</td>
    <td>Switch_B</td>
    <td>Fa0/4</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>Fa0/5</td>
    <td>Switch_C</td>
    <td>Fa0/1</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>Fa0/6</td>
    <td>AP A</td>
    <td>0/1</td>
    <td>172.16.0.252/24</td>
  </tr>
  <tr>
    <td rowspan="6">Switch_B</td>
    <td rowspan="6">2950-24</td>
    <td>Fa0/1</td>
    <td>Aluno_B</td>
    <td>Fa0</td>
    <td>172.16.0.3/23</td>
  </tr>
  <tr>
    <td>Fa0/2</td>
    <td>Professor_B</td>
    <td>Fa0</td>
    <td>172.16.2.2/23</td>
  </tr>
  <tr>
    <td>Fa0/3</td>
    <td>Funcionario_B</td>
    <td>Fa0</td>
    <td>172.16.4.2/23</td>
  </tr>
  <tr>
    <td>Fa0/4</td>
    <td>Switch_A</td>
    <td>Fa0/4</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>Fa0/5</td>
    <td>Switch_C</td>
    <td>Fa0/2</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>Fa0/6</td>
    <td>AP B</td>
    <td>0/1</td>
    <td>172.16.0.251/24</td>
  </tr>
  <tr>
    <td rowspan="6">Switch_C</td>
    <td rowspan="6">2950-24</td>
    <td>Fa0/1</td>
    <td>Switch_A</td>
    <td>Fa0/5</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>Fa0/2</td>
    <td>Switch_B</td>
    <td>Fa0/5</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>Fa0/3</td>
    <td>Router0</td>
    <td>Fa0/0</td>
    <td>150.1.1.2/30</td>
  </tr>
  <tr>
    <td>Fa0/4</td>
    <td>Servidor_professores</td>
    <td>Fa0</td>
    <td>172.16.6.2/23</td>
  </tr>
  <tr>
    <td>Fa0/5</td>
    <td>Servidor_funcionarios</td>
    <td>Fa0</td>
    <td>172.16.6.3/23</td>
  </tr>
  <tr>
    <td>Fa0/6</td>
    <td>AP_Recepção</td>
    <td>0/1</td>
    <td>172.16.0.253/24</td>
  </tr>
</tbody>
</table>




