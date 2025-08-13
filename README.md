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
- Identity Based Policy - Associa ao usuário dentro do [IAM](<img width="941" height="561" alt="image" src="https://github.com/user-attachments/assets/45744f1c-737c-4316-a15a-e44480a7d83f" />)
- Recurso [Usuário e Sistema](<img width="931" height="509" alt="image" src="https://github.com/user-attachments/assets/7878a536-5623-4a1c-a2a8-cc77a6e2f51d" />)


  



---
