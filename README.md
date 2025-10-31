# 🚀 Desafio DIO: Implementando uma Infraestrutura Automatizada com AWS CloudFormation

## 🧩 Entendendo o Desafio

Este projeto faz parte do **Bootcamp Santander 2025 - Fundamentos de IA para Devs**, promovido pela **Digital Innovation One (DIO)**.  
O objetivo é **implementar uma infraestrutura automatizada** na AWS utilizando o **CloudFormation**, aplicando os conceitos de **Infraestrutura como Código (IaC)** para provisionar recursos de forma simples, segura e replicável.

---

## 🎯 Objetivo

- Automatizar a criação de recursos AWS através de um **template CloudFormation**;  
- Documentar o processo completo, desde a configuração até a validação;  
- Demonstrar conhecimento prático em **IaC (Infrastructure as Code)** e **AWS**;  
- Utilizar o **GitHub** como ferramenta para versionar e compartilhar o projeto.

---

## 🧰 Tecnologias e Ferramentas

- **AWS CloudFormation**  
- **Amazon EC2** (instância de máquina virtual)  
- **Security Group** (controle de acesso)  
- **YAML** (linguagem de definição da infraestrutura)  
- **Git e GitHub** (controle de versão e documentação)

---

## 🪜 Passo a Passo da Implementação

### 1️⃣ Acesso ao Console da AWS
- Entre no [AWS Management Console](https://aws.amazon.com/console/);
- Pesquise por **CloudFormation** e clique em **Create stack → With new resources (standard)**.

---

### 2️⃣ Criação do Template YAML
Crie um arquivo chamado `template.yaml` com o seguinte conteúdo:

```yaml
AWSTemplateFormatVersion: '2010-09-09'
Description: Template para criação de uma infraestrutura automatizada com EC2 e Security Group

Resources:
  MeuSecurityGroup:
    Type: AWS::EC2::SecurityGroup
    Properties:
      GroupDescription: Security Group para acesso SSH e HTTP
      SecurityGroupIngress:
        - IpProtocol: tcp
          FromPort: 22
          ToPort: 22
          CidrIp: 0.0.0.0/0
        - IpProtocol: tcp
          FromPort: 80
          ToPort: 80
          CidrIp: 0.0.0.0/0
      Tags:
        - Key: Name
          Value: SG-DIO-Larissa

  MinhaInstanciaEC2:
    Type: AWS::EC2::Instance
    Properties:
      ImageId: ami-0c55b159cbfafe1f0  # Amazon Linux 2 (região us-east-1)
      InstanceType: t2.micro
      SecurityGroupIds:
        - !Ref MeuSecurityGroup
      KeyName: nome-da-sua-chave-aws
      Tags:
        - Key: Name
          Value: EC2-DIO-Larissa
```

##⚠️ Atenção:
Substitua nome-da-sua-chave-aws pelo nome do par de chaves (Key Pair) que você já criou na sua conta AWS.
A AMI usada (ami-0c55b159cbfafe1f0) é válida para a região us-east-1.


### 3️⃣ Criação da Stack

1. Faça o upload do arquivo template.yaml;
2. Dê um nome à sua Stack (ex: InfraestruturaAutomatizadaDIO);
3. Clique em Next → Next → Create Stack;
4. Aguarde até o status mudar para CREATE_COMPLETE.

### 4️⃣ Validação

Após a criação:

- Vá até o serviço EC2 e confirme se a instância foi criada;
- Verifique o Security Group associado e suas regras;
- Acesse a instância via SSH usando o Key Pair configurado.

### 5️⃣ Registro das Evidências

Durante o processo, capture prints e salve na pasta /images, como:

- Criação da Stack;
- Template carregado;
- Status “CREATE_COMPLETE”;
- EC2 criada;
- Security Group com regras aplicadas.

### 📸 Estrutura do Repositório
📁 dio-desafio-cloudformation
 ┗ 📄 README.md

### 💡 Insights e Aprendizados

- Entendi como o AWS CloudFormation automatiza e simplifica a criação de ambientes complexos;
- Percebi a importância de definir recursos via código (IaC) para padronização e reprodutibilidade;
- Aprendi a criar e configurar Security Groups e instâncias EC2 com boas práticas;
- Comprovei o valor do GitHub como portfólio técnico e espaço de versionamento.

### 🏁 Conclusão

Com este desafio, aprendi de forma prática a utilizar o AWS CloudFormation para provisionar uma infraestrutura automatizada e segura.
Essa prática reforçou conceitos de DevOps, IaC e automação de ambientes na nuvem, essenciais para o mercado de tecnologia atual.

✅ Desafio concluído com sucesso!

### ✨ Autora

Leticia Bacellar
👩‍💻 Bootcamp Santander 2025
📚 Projeto desenvolvido na plataforma Digital Innovation One (DIO)
🔗 https://www.dio.me
