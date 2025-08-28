# das-2-2025-2
Design e Arquitetura de Software II 2025/2 
## Architectural AWS [WELL-Architected](https://aws.amazon.com/pt/architecture/well-architected/)

---

# Aula 30/07/25

### Clound Computing and AWS

- O arquiteto planeja o que tem que fazer, testa e valida um protótipo
- **6 pilares** que todo arquiteto deve saber
  - Excelência Operacional
  - Segurança (ID seguro - Humano é o elo fraco)
  - Confiabilidade
  - Eficiência e Performance  (Estático e Dinâmico)
  - Custo e Otimização (Precisa medir o uso e eliminar o que não usar)
  - Sustentabilidade (Não desperdiçar tanto dinheiro quanto recurso)
- EC2 
- Amazon S3 


---

# Aula 06/08/25

### Estrutura da AWS

#### Regions and Availability Zones [Regions](https://aws.amazon.com/pt/about-aws/global-infrastructure/regions_az/)

- AZ -> Estrutura lógica que fica na mesma região, mas distantes um do outros
- Caso tenha falha, não impacta as outras estruturas (mesmo estando longe, a latência é baixa)
- Selecionar zonas disponíveis (zonas de disponibilidades - são interconectadas)
- **Local Zone** específico para rodar servidor (locais onde tem muita gente)
- AWS PoPs - Edge Location + Regional edge cache (CDN - Cloud Front)

### Segurança - Secutiry Acess

- AWS responsability model - Infra dos serviços, tipos de nuvem (IaaS / PaaS / SaaS)
- Principais **pilares/princípios** da segurança:
  - implementar uma base de identidade forte
  - Proteja os dados em trânsito e em repouso
  - Aplicar segurança em todas as camadas
  - Mnater os dados longe das pessoas
  - Rastreabilidade
  - Estar preparado para problemas de segurança
  - Automatizar todos os processos de segurança
- Princípio do privilégio mínimo

### Autenticação e Segurança de Acesso 

- Autenticação - 
- Principais **pilares/princípios** da segurança:
  - implementar uma base de identidade forte
  - Proteja os dados em trânsito e em repouso
  - Aplicar segurança em todas as camadas
  - Mnater os dados longe das pessoas
  - Rastreabilidade
  - Estar preparado para problemas de segurança
  - Automatizar todos os processos de segurança
- Princípio do privilégio mínimo
- Identity and Access Management - (IAM)
  - IAM Credentials for Autenticator

### Best Pratices to secure access 

- Use strong, complex passwords
- Secure local credentials
- Entre outros... 

---

# Aula 13/08/25

### Revisão e Atividade 

#### Pilares - (IAM) 

- Segurança ponta a ponta (tráfego - TLS e em descanso), não dar os dados pro usuário. 
- Princípio do privilégio mínimo
- Identity Based Policy - Associa ao usuário dentro do [IAM](https://aws.amazon.com/pt/iam/)
- Recurso [Usuário e Sistema]<img width="931" height="509" alt="image" src="https://github.com/user-attachments/assets/7878a536-5623-4a1c-a2a8-cc77a6e2f51d" />
- Estrutura da Documentação da Apólice <img width="942" height="503" alt="image" src="https://github.com/user-attachments/assets/98a8ca3a-0646-4537-9e9d-bc6b8e703bf8" />

#### Tarefinha meu rei!

- Módulo 2 - Knowledge Check
- Guided Lab: Exploring AWS Identity and Access Management (IAM)
- Módulo 3 - Knowledge Check

---

# Aula 20/08/25

### Continuação do conteúdo IAM / Finalizar **Guided Lab: Exploring AWS Identity and Access Management (IAM)**

#### Tipos de Armazenamento 

<img width="947" height="496" alt="image" src="https://github.com/user-attachments/assets/59d1becf-dd65-49da-bdf2-3266271fd44c" />

### Amazon S3

- Sistema de armazenamento de objetos (limite 5tb p/objt)
- Virtualmente limitado
- É acessível localmente
- Todo Bucket tem nome **único**
- Os buckets(bounds) vivem em uma região, ou seja, estão fisicamente em uma região
- <img width="917" height="477" alt="image" src="https://github.com/user-attachments/assets/e22b7e94-92b2-4326-b93d-81809344211e" />
- <img width="807" height="445" alt="image" src="https://github.com/user-attachments/assets/9d92e81f-1cab-455d-b623-a246068a2df4" />
- <img width="764" height="400" alt="image" src="https://github.com/user-attachments/assets/714276ef-9509-4d9e-95d0-40aee6dc32f4" />


#### Finalizar a tarefinha meu rei!

- Módulo 2 - Knowledge Check (OK)
- Guided Lab: Exploring AWS Identity and Access Management (IAM) (OK)
- Módulo 3 - Knowledge Check (OK)

---
  
# Aula 27/08/25

Módulo 4 - S3

### Amazon S3

#### Armazenamento de objetos(metadados(dados sobre dados)) 


- Teste link com titulo 


#### Finalizar a tarefinha meu rei!

- [lab: Creating a Static Website for the Cafe](https://awsacademy.instructure.com/courses/129676/assignments/1485129?module_item_id=12389220)
   



  



---
