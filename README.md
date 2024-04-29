# Criando uma rede segura com o Cisco Packet Tracer e um procedimento baseado nos padrões de GRC para o Programa Desenvolve do Grupo Boticário

## 1º Projeto Prático - Bootcamp em Segurança da Informação

Este repositório inclui uma **rede criada no Cisco Packet Tracer**, acompanhada de sua **documentação** correspondente e um arquivo contendo um **Procedimento de Segurança de Acesso Físico**. Esses elementos compõem o primeiro projeto prático do Bootcamp em Segurança da Informação do Programa Desenvolve. O propósito primordial deste projeto é proporcionar uma experiência prática, complementar às 8 semanas iniciais de cursos na plataforma Alura.

## Briefing do projeto

O projeto visa criar uma rede para um evento de programação na Universidade Alura, onde cada grupo de estudantes realizará provas diferentes em salas separadas. O evento contará com a presença de três categorias de pessoas: alunos, professores e funcionários.

As provas serão realizadas em computadores conectados à internet cabeada, e tanto professores quanto funcionários devem ter acesso exclusivo a servidores com informações direcionadas a eles, garantindo a realização planejada do evento. Professores terão acesso tanto a um computador quanto a um laptop, permitindo mobilidade na sala e comunicação livre com os alunos.

Os fiscais e seguranças, dois tipos de funcionários distintos, precisarão se locomover entre as salas e, portanto, devem contar com conexão de internet wireless. Além disso, o evento requer funcionários de recepção com acesso a uma rede completamente sem fio para resolver problemas com agilidade.

Outro requisito essencial é o sistema de telefonia funcionar adequadamente.

Além de políticas de segurança e procedimentos bem definidos para responder a incidentes, a Universidade Alura solicita o desenvolvimento de um Procedimento de Segurança para garantir a integridade física das pessoas, dos bens e das informações sensíveis armazenadas nas instalações.

### Requisitos

* Acesso à internet cabeada e wireless
* Servidores com políticas de acesso
* Conexão de mais de 600 computadores
* Sistema de telefonia
* Políticas de segurança lógica e física

### Tecnologias
![Cisco](https://img.shields.io/badge/cisco-%23049fd9.svg?style=for-the-badge&logo=cisco&logoColor=black)

## Infraestrutura e rede

### Dispositivos

* 6x PC
* 5x Laptop
* 3x Ponto de Acesso Wi-Fi 
* 3x Switch 
* 2x Roteador 
* 2x Servidor
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
    <td>F0/0.4</td>
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

#### Servidores

<table>
<thead>
  <tr>
    <th rowspan="2">Nome</th>
    <th rowspan="2">Modelo</th>
    <th rowspan="2">Interface</th>
    <th rowspan="2">IP / Máscara de Sub-rede</th>
    <th colspan="2">Dispositivo conectado</th>
  </tr>
  <tr>
    <th>Nome</th>
    <th>Interface</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>Servidor_professores</td>
    <td>Server_PT</td>
    <td>Fa0</td>
    <td>172.16.6.2/23</td>
    <td>Switch_C</td>
    <td>Fa0/4</td>
  </tr>
  <tr>
    <td>Servidor_funcionarios</td>
    <td>Server_PT</td>
    <td>Fa0</td>
    <td>172.16.6.3/23</td>
    <td>Switch_C</td>
    <td>Fa/05</td>
  </tr>
</tbody>
</table>

#### Pontos de acesso Wi-fi (AP)

<table>
<thead>
  <tr>
    <th rowspan="2">Nome</th>
    <th rowspan="2">Modelo</th>
    <th rowspan="2">Interface</th>
    <th rowspan="2">IP / Máscara de Sub-rede</th>
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
    <td rowspan="3">AP A</td>
    <td rowspan="3">Linksys-WRT300N</td>
    <td>0/1</td>
    <td>172.16.0.251/24</td>
    <td>Switch_A</td>
    <td>Fa0/6</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>Wireless</td>
    <td>N/A</td>
    <td>Fiscal</td>
    <td>Wireless0</td>
    <td>172.16.4.7/23</td>
  </tr>
  <tr>
    <td>Wireless</td>
    <td>N/A</td>
    <td>Segurança</td>
    <td>Wireless0</td>
    <td>172.16.4.8/23</td>
  </tr>
  <tr>
    <td rowspan="3">AP B</td>
    <td rowspan="3">Linksys-WRT300N</td>
    <td>0/1</td>
    <td>172.16.0.252/24</td>
    <td>Switch_B</td>
    <td>Fa0/6</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>Wireless</td>
    <td>N/A</td>
    <td>Laptop_ProfA</td>
    <td>Wireless0</td>
    <td>172.16.2.6/23</td>
  </tr>
  <tr>
    <td>Wireless</td>
    <td>N/A</td>
    <td>Laptop_ProfB</td>
    <td>Wireless0</td>
    <td>172.16.2.5/23</td>
  </tr>
  <tr>
    <td rowspan="4">AP_Recepção</td>
    <td rowspan="4">Linksys-WRT300N</td>
    <td>0/1</td>
    <td>172.16.0.253/24</td>
    <td>Switch_C</td>
    <td>Fa0/6</td>
    <td>N/A</td>
  </tr>
  <tr>
    <td>Wireless</td>
    <td>N/A</td>
    <td>Laptop_Recep</td>
    <td>Wireless0</td>
    <td>172.16.4.9/23</td>
  </tr>
  <tr>
    <td>Wireless</td>
    <td>N/A</td>
    <td>Cel_Recep</td>
    <td>Wireless0</td>
    <td>172.16.4.10/23</td>
  </tr>
  <tr>
    <td>Wireless</td>
    <td>N/A</td>
    <td>Printer0</td>
    <td>Wireless0</td>
    <td>172.16.4.10/23</td>
  </tr>
</tbody>
</table>

### Políticas de segurança de rede

* Controle de Acesso baseado em ACLs para restringir tráfego entre as redes de professores e funcionários
* Redundância de links com STP
* Segregação de redes utilizando VLANs
* Autenticação WPA2-PSK
* Criptografia AES

## Políticas e procedimentos

### Procedimentos de resposta a incidentes

![processo de resposta a incidentes](https://github.com/CamilaSCodes/projeto-1-bootcamp-infosec/blob/main/imagens/Procedimento%20de%20resposta%20a%20incidentes.png)

1. Detecção de Incidentes:
    * Monitoramento contínuo dos logs de segurança dos dispositivos de rede.

2. Classificação do Incidente:
    * Avaliação da gravidade do incidente com base na sua natureza e impacto potencial.

3. Isolamento do Incidente:
    * Isolar imediatamente o ponto de acesso comprometido para evitar a propagação do incidente.

4. Investigação do Incidente:
    * Coletar informações detalhadas sobre o incidente e analisar a causa raiz.

5. Contenção e Recuperação:
    * Implementar medidas corretivas para resolver as vulnerabilidades identificadas;
    * Restaurar os sistemas afetados para um estado seguro e funcional.

6. Notificação e Comunicação:
    * Notificar as partes interessadas relevantes sobre o incidente e suas resoluções.

7. Documentação e Análise Pós-Incidente:
    * Documentar o incidente, incluindo todas as etapas da resposta e lições aprendidas;
    * Realizar análise pós-incidente para identificar áreas de melhoria nos processos de segurança.

### Procedimento de Segurança de Acesso Físico

O acesso físico às instalações da empresa é um aspecto crítico do gerenciamento de segurança para a Alura. Este [procedimento](https://github.com/CamilaSCodes/projeto-1-bootcamp-infosec/blob/main/Procedimento%20de%20Segurança%20de%20Acesso%20Físico.pdf) descreve as etapas e diretrizes para controlar e gerenciar o acesso físico para garantir a segurança das pessoas, dos ativos e das informações confidenciais em conformidade com os padrões de governança, risco e conformidade (GRC). As orientações contidas nesse documento devem ser entendidas e seguidas em todos os níveis hierárquicos da instituição.  

## Conclusão

Ao longo do projeto, foram integrados diversos dispositivos e tecnologias para atender aos [requisitos](#requisitos) específicos do evento de programação na Universidade Alura, garantindo não apenas conectividade confiável, mas também segurança tanto física quanto lógica.

A criação de VLANs, a aplicação de políticas de acesso baseadas em ACLs e a implementação de criptografia AES e autenticação WPA2-PSK são exemplos de medidas adotadas para fortalecer a segurança da rede. Além disso, a elaboração de procedimentos de resposta a incidentes e um Procedimento de Segurança de Acesso Físico evidenciam o compromisso com a gestão abrangente da segurança da informação.

Este projeto não apenas consolida o conhecimento adquirido nas primeiras semanas de curso, mas também representa um passo importante para preparar os alunos para enfrentar desafios reais no campo da segurança da informação. Ao mesmo tempo, fomenta a parceria entre academia e indústria para promover práticas de segurança sólidas e eficazes.

