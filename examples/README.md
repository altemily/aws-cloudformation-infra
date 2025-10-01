# 📂 Examples – AWS CloudFormation

Esta pasta contém **exemplos práticos de templates CloudFormation** em YAML, criados para demonstrar diferentes cenários de uso de **Infraestrutura como Código (IaC)**.

Cada arquivo é independente e pode ser usado como base para estudos ou para provisionar recursos reais na AWS.

---

## 📑 Estrutura dos arquivos

```
examples/
├── vpc_stack.yaml   # exemplo com rede (VPC, Subnets, Internet Gateway)
├── s3_lambda.yaml   # exemplo simples com bucket + lambda
└── ec2_stack.yaml   # exemplo com instância EC2
```

---

## 📘 Exemplos disponíveis

### 1️⃣ VPC Stack (`vpc_stack.yaml`)
Cria uma **VPC personalizada**, com:
- Uma VPC dedicada.
- Subnet pública.
- Internet Gateway associado.

📌 **Quando usar:**  
Ideal para laboratórios de **rede AWS**, ou como base para aplicações que precisam de isolamento e controle de tráfego.

---

### 2️⃣ S3 + Lambda (`s3_lambda.yaml`)
Cria:
- Um **Bucket S3**.
- Uma **função Lambda Python** simples com permissões básicas.

📌 **Quando usar:**  
Bom exemplo para aprender **event-driven** e integração entre serviços AWS. Pode ser expandido para processar arquivos, imagens ou logs enviados ao bucket.

---

### 3️⃣ EC2 Stack (`ec2_stack.yaml`)
Cria:
- Uma instância **EC2 t2.micro**.
- Security Group liberando **SSH (22)** e **HTTP (80)**.

📌 **Quando usar:**  
Exemplo para praticar **deploy de servidores** ou hospedar uma aplicação simples.  
⚠️ Necessário informar um **KeyPair existente** da sua conta AWS para acesso via SSH.

---

## 🛠️ Como usar os templates

### Criar uma stack

```bash
aws cloudformation create-stack \
  --stack-name MinhaStackVPC \
  --template-body file://examples/vpc_stack.yaml \
  --capabilities CAPABILITY_NAMED_IAM
```

### Validar template antes do deploy

```bash
aws cloudformation validate-template \
  --template-body file://examples/vpc_stack.yaml
```

### Atualizar uma stack existente

```bash
aws cloudformation update-stack \
  --stack-name MinhaStackVPC \
  --template-body file://examples/vpc_stack.yaml \
  --capabilities CAPABILITY_NAMED_IAM
```

### Deletar uma stack

```bash
aws cloudformation delete-stack --stack-name MinhaStackVPC
```

---

## ✅ Boas práticas

- Sempre valide o template antes do deploy.
- Use ambientes de teste antes de aplicar em produção.
- Versione suas alterações no GitHub para controle de mudanças.
- Prefira parâmetros nos templates para torná-los reutilizáveis.

---

## 📚 Referências

- [Documentação oficial AWS CloudFormation](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/Welcome.html)
- [AWS S3 + Lambda integration](https://docs.aws.amazon.com/pt_br/AmazonS3/latest/userguide/NotificationHowTo.html)
- [Guia de boas práticas em IaC](https://aws.amazon.com/architecture/infrastructure-as-code/)