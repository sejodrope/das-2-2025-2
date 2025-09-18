# Design e Arquitetura de Software II 2025/2

**Disciplina:** Design e Arquitetura de Software II 2025/2  
**Framework Principal:** [AWS Well-Architected](https://aws.amazon.com/pt/architecture/well-architected/)  
**Canvas:** [AWS Academy Course](https://awsacademy.instructure.com/courses/129676)

---

## Aula 30/07/25 - Cloud Computing e AWS

### Well-Architected Framework
O arquiteto planeja, testa e valida protótipos baseado nos **6 pilares fundamentais** que todo arquiteto deve conhecer:

1. **Excelência Operacional** - Executar e monitorar sistemas para entregar valor ao negócio
2. **Segurança** - Proteger informações e sistemas (ID seguro - Humano é o elo fraco)
3. **Confiabilidade** - Capacidade de recuperação e disponibilidade
4. **Eficiência e Performance** - Uso eficiente de recursos (Estático e Dinâmico)
5. **Custo e Otimização** - Evitar gastos desnecessários (Precisa medir o uso e eliminar o que não usar)
6. **Sustentabilidade** - Minimizar impactos ambientais (Não desperdiçar recursos)

### Serviços Principais Introduzidos
- **EC2** - Elastic Compute Cloud
- **Amazon S3** - Simple Storage Service

---

## Aula 06/08/25 - Estrutura AWS e Segurança

### Regions and Availability Zones
- **AZ (Availability Zones)** - Estrutura lógica na mesma região, mas distantes entre si
- **Vantagem:** Em caso de falha, não impacta outras estruturas (baixa latência mesmo com distância)
- **Local Zones** - Específicas para rodar servidores em locais com alta demanda
- **AWS PoPs** - Edge Locations + Regional Edge Cache (CDN - CloudFront)

### Modelo de Responsabilidade Compartilhada
A AWS é responsável pela infraestrutura dos serviços, tipos de nuvem (IaaS/PaaS/SaaS)

### Princípios Fundamentais de Segurança
1. **Implementar base de identidade forte**
2. **Proteger dados em trânsito e em repouso**
3. **Aplicar segurança em todas as camadas**
4. **Manter dados longe das pessoas**
5. **Rastreabilidade completa**
6. **Estar preparado para problemas de segurança**
7. **Automatizar processos de segurança**

### Conceitos Centrais
- **Princípio do Privilégio Mínimo**
- **IAM (Identity and Access Management)** - Gerenciamento de identidades e acessos
- **IAM Credentials** para autenticação

---

## Aula 13/08/25 - IAM e Políticas

### Tipos de Políticas IAM
- **Identity Based Policy** - Associada ao usuário dentro do IAM
- **Resource Based Policy** - Anexada diretamente ao recurso

### Estrutura das Políticas
As políticas seguem uma estrutura JSON específica com elementos como:
- **Effect** (Allow/Deny)
- **Action** (ações permitidas)
- **Resource** (recursos afetados)
- **Principal** (quem pode executar)

### Atividades Práticas Concluídas
- ✅ Módulo 2 - Knowledge Check
- ✅ Guided Lab: Exploring AWS Identity and Access Management (IAM)
- ✅ Módulo 3 - Knowledge Check

---

## Aula 20/08/25 - Armazenamento e Amazon S3

### Tipos de Armazenamento
- **Block Storage** - Armazenamento em blocos (EBS)
- **File Storage** - Sistema de arquivos compartilhado (EFS)
- **Object Storage** - Armazenamento de objetos (S3)

### Amazon S3 - Características Principais
- **Sistema de armazenamento de objetos** (limite 5TB por objeto)
- **Virtualmente ilimitado** em capacidade total
- **Buckets têm nomes únicos globalmente**
- **Buckets residem em regiões específicas**
- **Por padrão, apenas o criador tem acesso**
- **Todos objetos possuem URL pública** (mas bloqueada por padrão)

### Fatores para Escolha de Região
1. **Legislação** - LGPD obriga dados no Brasil
2. **Proximidade/Latência** - Reduzir tempo de acesso
3. **Disponibilidade do Serviço** - Nem todos recursos estão em todas regiões
4. **Custo** - Brasil é mais caro devido carga tributária

---

## Aula 27/08/25 - Programação com S3 (Hands-On)

### Configuração do Ambiente de Desenvolvimento

#### Estrutura de Arquivos
```
projeto/
├── .gitignore
├── .devcontainer/
│   └── devcontainer.json
├── .vscode/
│   └── launch.json
├── s3/
│   ├── requirements.txt
│   ├── venv/
│   ├── criar_bucket.py
│   ├── upload.py
│   ├── listar.py
│   └── excluir.py
└── exemplo.txt
```

#### Configuração Python com Virtual Environment
```bash
# Entrar na pasta do projeto
cd s3

# Criar ambiente virtual
python -m venv venv

# Ativar ambiente virtual (Linux)
source venv/bin/activate

# Instalar dependências
pip install -r requirements.txt
```

#### Arquivo requirements.txt
```
boto3
```

#### Configuração de Credenciais (.vscode/launch.json)
```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: Current File",
            "type": "python",
            "request": "launch",
            "program": "${file}",
            "console": "integratedTerminal",
            "env": {
                "AWS_ACCESS_KEY_ID": "sua_access_key",
                "AWS_SECRET_ACCESS_KEY": "sua_secret_key"
            }
        }
    ]
}
```

### Programação com Boto3

#### 1. Criar Bucket (criar_bucket.py)
```python
import boto3

# Conectar com AWS
s3_client = boto3.client('s3', region_name='us-east-1')

# Criar bucket (nome deve ser único globalmente)
bucket_name = 'seu-nome-sobrenome-ano-nascimento'
s3_client.create_bucket(Bucket=bucket_name)

print("Bucket criado com sucesso!")
```

#### 2. Upload de Arquivo (upload.py)
```python
import boto3

# Conectar com AWS
s3_client = boto3.client('s3', region_name='us-east-1')

# Upload do arquivo
s3_client.upload_file(
    './s3/exemplo.txt',  # arquivo local
    'seu-bucket-name',   # nome do bucket
    'exemplo.txt'        # nome no S3
)

print("Arquivo carregado com sucesso!")
```

#### 3. Listar Objetos (listar.py)
```python
import boto3

# Usar high-level API (resource)
s3 = boto3.resource('s3', region_name='us-east-1')

# Obter referência do bucket
bucket = s3.bucket('seu-bucket-name')

# Listar objetos
for objeto in bucket.objects.all():
    print(f"Arquivo: {objeto.key}, Tamanho: {objeto.size} bytes")
```

#### 4. Excluir Arquivo (excluir.py)
```python
import boto3

# Conectar com AWS
s3 = boto3.resource('s3', region_name='us-east-1')

# Obter referência do objeto
bucket = s3.bucket('seu-bucket-name')
objeto = bucket.Object('exemplo.txt')

# Excluir objeto
objeto.delete()

print("Arquivo excluído com sucesso!")
```

### Configuração de Acesso Público

#### Política de Bucket para Acesso Público
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "PublicReadGetObject",
            "Effect": "Allow",
            "Principal": "*",
            "Action": [
                "s3:ListBucket",
                "s3:GetObject"
            ],
            "Resource": [
                "arn:aws:s3:::seu-bucket-name",
                "arn:aws:s3:::seu-bucket-name/*"
            ]
        }
    ]
}
```

#### Passos para Tornar Bucket Público
1. **Desbloquear acesso público** nas configurações do bucket
2. **Aplicar política de bucket** com as permissões adequadas
3. **Verificar acesso** através da URL pública do objeto

### Conceitos Importantes

#### Boto3 SDK
- **High Level API (resource)** - Mais simples, operações básicas
- **Low Level API (client)** - Mais controle, operações complexas

#### Metadados S3
- **Objetos incluem dados + metadados**
- **Metadados:** informações sobre os dados (criptografia, timestamps, etc.)
- **Por isso é chamado "Object Storage" e não "File Storage"**

#### Gerenciamento de Projetos
- **S3 Inventory** - Relatórios de objetos (pode levar até 1 dia para gerar)
- **Necessário para buckets com trilhões de objetos**

### Boas Práticas de Desenvolvimento

#### Segurança
- **Nunca commitar credenciais** (usar .gitignore)
- **Usar variáveis de ambiente** para credenciais
- **Princípio do privilégio mínimo** em políticas

#### Python
- **Virtual Environment** para isolamento de dependências
- **Requirements.txt** para versionamento de bibliotecas
- **Supply Chain Security** - cuidado com dependências

---
 
## Aula 10/09/25 - Amazon services - EBS 

### Configuração do Ambiente de Desenvolvimento de Servidores(data centers de HD)

- Armazenamento pertsistente (ta de boa se liga e desliga)
- Possui vários tipos de volume HDD-backed 
- **File share**: `EBS e S3` não é Fileshare, pois é 1:1 e várias outras paradas.
- **File share**: `Amazon EFS` é linux (não precisa definir tamanho e é mega robusto)
- **File share**: `Amazon FSx` é Windows e Linux entre outros (NETAPP, openzfs e HPC(O FODÃO))

### Montar um servidor Windows 

- Não precisa de chave como no linux 


---
 
## Aula 17/09/25 - Amazon Redes - Gateway

### Configuração do Ambiente de Desenvolvimento de Servidores(data centers de HD)
### Deploy entre outros...

### Placement strategies:
- **Cluster**: `Todas máquinas na mesma AZ`, ou seja, no mesmo espaço físico pra aumento de performance.
- **Partition**: `É o meio dos dois`, hadoop, kafka, spark (sharding partition). 
- **Spread**: `Alta disponibilidade`, mas baixa performance. 

### Amazon EC2 - Precificação:
- **on-demand**: `O mais caro`, ou seja, no mesmo espaço físico pra aumento de performance.
- **Reserved**: `Até 72% de desconto`, reserva uma máquina fisica
- **Saving Plans**: `Até 74% de desconto`, reserva uma máquina e paga $/hora
- **Amazon EC2 Sopt**: `O queridinho`, 92% de desconto, mas baixa disponivilidade

### Amazon Banco de Dados:
- **OSI**: `IP, TCP/UDP...`, System Operacional Information
- **Internet Gateway**: `transferer`,
- **VPC Peering**: `Interligar VPC's/Redes`, em regiões diferentes
- **VPC endpoints**: `cria um túnel por dentro da AWS`,  


---


### Próximos Passos
- Continuar com outros serviços AWS (DynamoDB, RDS, etc.)
- Aprofundar conceitos de arquitetura
- Implementar projetos mais complexos

---

## Atividades Pendentes
- [ ] [Lab: Creating a Static Website for the Cafe](https://awsacademy.instructure.com/courses/129676/assignments/1485129?module_item_id=12389220)

---

**Observações Importantes:**
- Sempre fazer logout da console AWS após uso
- Executar "End Lab" no Canvas para limpar ambiente
- Fazer commit do código antes de encerrar sessão
- Brasil tem custos mais altos devido à carga tributária
