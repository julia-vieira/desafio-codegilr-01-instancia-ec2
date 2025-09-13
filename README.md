# desafio-codegilr-01-instancia-ec2
CodeGirls - Desafio 01 - Instância EC2

🚀 Desafio de Gerenciamento de Instâncias EC2 na AWS

Este repositõrio tem como objetivo documentar o aprendisado relacionado ao gerenciamento de instancias de EC2 na AWS.

## 1. 🕰️ Histórico

- Lançada em **2006** como parte do AWS Cloud.
- Primeira solução de *infraestrutura como serviço (IaaS)* da Amazon.
- Evoluiu para oferecer diversos tipos de instâncias, suporte a escalabilidade, automação e integração com diversos serviços da AWS.

---

## 2. ⚙️ O que é uma Instância EC2

- Um servidor virtual executando em datacenters da AWS.
- Pode executar sistemas operacionais como Linux, Windows e outros.
- Possui características configuráveis de CPU, memória, armazenamento e rede.
- Utilizado para hospedar aplicações, serviços backend, bancos de dados, etc.

---

## 3. 🔁 Ciclo de Vida da Instância

1. **Pending** – Instância está sendo iniciada.
2. **Running** – Instância em execução.
3. **Stopping** – Instância está sendo desligada.
4. **Stopped** – Instância parada, pode ser reiniciada.
5. **Terminated** – Instância excluída permanentemente.

---

## 4. 🛠️ Etapas do Gerenciamento

### 4.1 Criação

- Escolha da **AMI (Amazon Machine Image)**.
- Definição do **tipo da instância** (ex: t2.micro, m5.large, etc.).
- Seleção da **rede (VPC)** e **sub-rede**.
- Configuração de **armazenamento (EBS)**.
- Associação de **chaves SSH** para acesso remoto.
- Definição de **grupos de segurança**.

### 4.2 Monitoramento

- Utilização do **Amazon CloudWatch** para:
  - CPU, disco, memória (com agente).
  - Alarmes e triggers para autoscaling.
- **Status Checks**:
  - System status.
  - Instance status.
- Coleta de logs via CloudWatch Logs ou agente de terceiros.

### 4.3 Backup e Recuperação

- Snapshots de volumes EBS.
- Criação de AMIs personalizadas.
- Políticas automatizadas de backup com AWS Backup.
- Planejamento de recuperação de desastres (DRP).

### 4.4 Segurança

- **Grupos de Segurança** (firewall de instância).
- **Network ACLs** (nível da sub-rede).
- **Chaves de acesso SSH** ou uso do **SSM Session Manager**.
- Controle de permissões via **IAM Roles** aplicados à instância.

### 4.5 Escalabilidade

- **Auto Scaling Group (ASG)**: escalar horizontalmente com base em métricas.
- **Elastic Load Balancer (ELB)**: distribuir carga entre instâncias.
- **Elastic IPs** para IPs públicos persistentes.
- **Spot Instances** para cargas não críticas com baixo custo.

---

## 6. ✅ Melhores Práticas

- 🏷️ **Taguear recursos**: para identificação, custo, ambiente, dono.
- 🔒 **Restringir acessos com IAM**.
- 📉 **Desligar instâncias ociosas**.
- ♻️ **Automatizar criação/destruição com scripts ou IaC**.
- ☁️ **Usar SSM para comandos remotos, sem abrir portas SSH**.
- 📊 **Revisar custos com AWS Cost Explorer e Trusted Advisor**.
- 📅 **Automatizar backups com políticas diárias/semanal**.

---

## 7. 🔧 Ferramentas de Suporte

| Ferramenta         | Descrição                                                                 |
|---------------------|--------------------------------------------------------------------------|
| AWS CLI / SDKs      | Automação por linha de comando ou código.                                |
| AWS CloudFormation  | Infraestrutura como código (IaC) nativo da AWS.                         |
| Terraform           | IaC independente e multi-cloud.                                         |
| AWS Systems Manager | Gerenciamento remoto, patching, inventário e execução de comandos.      |
| EC2 Image Builder   | Automatiza a criação de AMIs personalizadas.                            |

---

📌 # Resumo de estudos sobre as aulas:
 --- 
# Instâncias EC2 na AWS

* EC2 (Elastic Compute Cloud): são máquinas virtuais na nuvem AWS, podendo rodar Linux ou Windows.
* Componentes principais: CPU, memória, disco, rede e sistema operacional.
* Modelo de serviço: IaaS (Infraestrutura como Serviço).
* Responsabilidade do usuário: aplicativos, dados e conexões.
* Escolha da instância: depende das necessidades da aplicação (desempenho, escalabilidade e custo).
* Segurança: uso de grupos de segurança (firewall), definindo portas, protocolos e IPs permitidos.
* Terminologia importante:
   * AMI (Amazon Machine Image) – imagem usada para criar a instância.
   * Security Groups – controle de acesso (entrada e saída).
   * Elasticidade – capacidade de escalar de acordo com a demanda.

---
# Otimização de Recursos na AWS
Otimizar = Reduzir custos: otimizar recursos na AWS significa usar melhor a infraestrutura para economizar e ganhar desempenho.

Boas práticas:

* Desligar instâncias não utilizadas (principalmente em ambientes de desenvolvimento e teste).
* Remover recursos ociosos (evitar pagar por algo sem uso).
* Escalonamento (Scale): ajustar os recursos de acordo com a demanda.

* Escala Vertical: aumentar/reduzir capacidade em um único nó (CPU, memória, storage).
* Escala Horizontal: adicionar/remover instâncias ou discos extras.
* Modelos de Compra de Instâncias:

* Sob Demanda: paga por hora, ideal para cargas irregulares e curtas (teste/desenvolvimento).
* Reservadas: mais baratas, mas exigem compromisso de longo prazo (1 ano ou mais).
* Spot: até 90% mais baratas, mas podem ser encerradas pela AWS com aviso prévio de 2 minutos.

---
# Amazon EBS (Elastic Block Store)

* O que é: serviço de armazenamento em blocos da AWS, altamente confiável, que pode ser anexado a qualquer instância EC2.
** Características principais:
* Toda instância EC2 tem um volume de armazenamento.
* O EBS permite expansão rápida, com apenas alguns cliques.
Funciona como anexar um HD externo à instância.
* Casos de uso:
Armazenamento de bancos de dados (MySQL, PostgreSQL, Oracle).
Armazenamento de dados para aplicativos web.
Armazenamento de logs do sistema.

---
# Amazon S3 (Simple Storage Service)

* O que é: serviço de armazenamento de objetos da AWS, altamente escalável e seguro.
 * Principais usos: armazenar, organizar e recuperar grandes volumes de dados.
 * Classes de armazenamento (Storage Classes): permitem otimizar custos de acordo com a frequência de acesso aos dados.
* Exemplo: exames de hospital → dados acessados com frequência ficam em classes mais rápidas, e exames antigos podem ir para classes mais baratas como Glacier.
* Regras de ciclo de vida (Lifecycle Rules): automatizam a transição de objetos entre classes, garantindo economia e eficiência no longo prazo.

---
# 📁  Diagrama da Arquitetura

<img width="721" height="582" alt="image" src="https://github.com/user-attachments/assets/d81a8acf-3279-4097-8923-2ad880b84503" />

*Link:* https://drive.google.com/file/d/1_-x203BeONUSGMnog12QVHZaKoVKFUoL/view?usp=drive_link

## 📌 Descrição

Este diagrama implementa uma arquitetura em nuvem utilizando serviços da **AWS (Amazon Web Services)** para receber, armazenar e processar arquivos enviados por usuários. A aplicação é hospedada em uma instância EC2, com armazenamento persistente em volumes EBS e banco de dados relacional gerenciado via RDS.

---

## 🧱 Arquitetura

### Componentes principais:

- **EC2 (Elastic Compute Cloud)**: Instância que hospeda a aplicação e gerencia o recebimento e processamento dos arquivos.
- **EBS (Elastic Block Store)**:
  - `D - EBS`: Volume principal para armazenar os arquivos enviados.
  - `E - EBS`: Volume adicional (logs, cache ou backups).
- **RDS (Relational Database Service)**: Banco de dados relacional (MySQL/PostgreSQL) para armazenar metadados dos arquivos e informações de usuários.
- **Usuário (Actor)**: Interage com a aplicação via interface gráfica e realiza uploads de arquivos.

---

## 📂 Fluxo de Funcionamento

1. O usuário acessa a aplicação via navegador.
2. Realiza o upload de um arquivo.
3. A aplicação na instância EC2 processa o arquivo.
4. O arquivo é salvo no volume EBS (`D - EBS`).
5. Informações associadas ao arquivo (ex: nome, data de upload, usuário) são salvas no banco de dados RDS.
6. Logs ou dados temporários são armazenados no volume EBS (`E - EBS`).



📌 Desafio do Bootcamp Santander Coders Girls - DIO

---






