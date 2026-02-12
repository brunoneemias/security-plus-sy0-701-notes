## Aula 4: Authentication, Authorization, and Accounting (AAA)

### 4.1 O Framework AAA

O **AAA Framework** é composto por três componentes fundamentais da segurança:
```
AAA = Authentication + Authorization + Accounting
```

---

### 4.2 Os Três Componentes do AAA

#### 1. Identification (Identificação)
**Processo inicial**: Afirmar quem você é no sistema
- Fornecimento de username (nome de usuário)
- **Não prova** identidade, apenas declara quem você afirma ser

#### 2. Authentication (Autenticação)
**Processo de verificação**: Provar que você realmente é quem afirma ser

**Elementos de verificação**:
- Username
- Password (senha secreta)
- Fatores adicionais de autenticação

**Resultado**: Confirmação de identidade porque você:
- Conhecia a senha secreta, OU
- Tinha fatores adicionais para provar identidade

#### 3. Authorization (Autorização)
**Processo de permissão**: Determinar que tipo de acesso você tem

**Princípio**: Acesso baseado em função/departamento
- **Exemplo**: Shipping and Receiving department
  - ✅ Acesso a sistemas de shipping and receiving
  - ❌ SEM acesso a informações do finance department

**Baseado em**: Quem você é e qual sua função

#### 4. Accounting (Contabilidade/Auditoria)
**Processo de registro**: Log de todas as atividades

**Informações registradas**:
- Horário de login
- Quantidade de dados enviados/recebidos
- Horário de logout
- Todas as ações realizadas no sistema

**Objetivo**: Rastreabilidade completa de atividades

---

### 4.3 Exemplo Prático: Login em VPN

#### Cenário
- **Cliente**: Na internet
- **VPN Concentrator**: Firewall/concentrador no meio
- **Objetivo**: Acessar file server interno

#### Processo Passo a Passo

**PASSO 1: Solicitação de Acesso**
```
Cliente (Internet) → VPN Concentrator
```
- Cliente acessa VPN concentrator
- Concentrator solicita login
- Cliente fornece username + password

**PASSO 2: Verificação no AAA Server**
```
VPN Concentrator → AAA Server
```
- Concentrator **não tem** informações de usuários armazenadas
- Em organizações, informações ficam em **servidor central** (AAA Server)
- Concentrator envia credenciais para AAA Server verificar

**PASSO 3: Validação**
```
AAA Server verifica:
- Username existe?
- Password está correto?
- Outros fatores de autenticação válidos?
```

**PASSO 4: Resposta**
```
AAA Server → VPN Concentrator
```
- Se credenciais corretas: "Credentials approved" ✅
- Concentrator confirma identidade do usuário

**PASSO 5: Acesso Concedido**
```
VPN Concentrator → Internal File Server
```
- Concentrator permite acesso ao file server interno
- Usuário autenticado pode acessar recursos autorizados

---

### 4.4 Autenticação de Dispositivos

#### Desafio da Segurança Moderna
**Cenário**: Profissional de segurança gerenciando:
- Centenas ou milhares de sistemas
- Sistemas distribuídos globalmente
- Sem acesso físico aos dispositivos

**Pergunta-chave**: Como verificar que um computador tentando conectar é autorizado?

**Problemas**:
- ❌ Computador não pode "digitar" senha
- ❌ Armazenar senha no sistema em campo = inseguro
- ❓ Como confirmar que sistema é permitido na rede interna?

---

#### Solução: Certificados Digitais

**Método**: Usar certificado digitalmente assinado no dispositivo

**Processo**:
1. Certificado instalado no dispositivo
2. Verificação durante processo de login
3. Confirmação de que é laptop da empresa

**Casos de Uso**:
- **VPN Concentrator**: Verificar dispositivos entrando na rede
- **Management Software**: Validar dispositivos (local ou remoto)
- **Network Access Control**: Garantir apenas dispositivos corporativos

---

### 4.5 Certificate Authority (CA)

#### Conceito
**Certificate Authority (CA)**: Autoridade Certificadora

**Definição**: Dispositivo ou software responsável por gerenciar todos os certificados no ambiente

#### Processo de Criação de Certificado

**PASSO 1: Infraestrutura**
```
Requisito obrigatório: ter Certificate Authority (CA)
```

**PASSO 2: Criação do Certificado**
```
CA → Cria certificado específico para o laptop
```
- Certificado único para cada dispositivo
- Assinado digitalmente pela CA

**PASSO 3: Instalação**
```
Certificado → Instalado no laptop
```

**PASSO 4: Autenticação**
```
Laptop se conecta → Apresenta certificado → Sistema verifica assinatura da CA
```

---

#### Hierarquia de Certificados
```
Root CA (Raiz)
    ↓
    [Assina]
    ↓
Certificate Authority (CA da organização)
    ↓
    [Assina]
    ↓
Device Certificate (Certificado do dispositivo)
```

**Componentes**:
1. **Root CA**: Autoridade raiz (topo da cadeia de confiança)
2. **CA Certificate**: Certificado da CA (assinado pelo Root CA)
3. **Device Certificate**: Certificado do dispositivo (assinado pela CA)

**Verificação**:
- Comparar CA certificate com device certificate
- Confirmar que device certificate foi assinado pela CA confiável
- Validar cadeia de confiança completa

---

### 4.6 Authorization Models (Modelos de Autorização)

#### O Problema da Escala

**Cenário sem modelo de autorização**:
- Criar direitos e permissões individuais para cada usuário
- Usuário tem rights para acessar cada recurso específico
- **Problema**: NÃO escala bem

**Exemplo: Shipping and Receiving Department**

**Necessidades de acesso**:
- Criar shipping labels
- Rastrear shipments
- Ver relatórios mensais de envio
- Acessar dados de clientes
- Tracking information databases

**Problema de escala**:
- 1 usuário = Gerenciável
- 10 usuários = Trabalhoso
- 100+ usuários = Impossível gerenciar manualmente
- Centenas de recursos × Centenas de usuários = **Inviável**

---

#### Solução: Abstração via Modelos de Autorização

**Conceito**: Abstraction (Abstração)
- Separar usuários das informações que tentam acessar
- Simplifica drasticamente a administração
- Suporta infraestrutura muito grande com configurações simples

**Também conhecido como**: Authorization Model

---

### 4.7 Group-Based Authorization (Autorização Baseada em Grupos)

#### Funcionamento

**ANTES (Modelo Individual)**:
```
User → Manual mapping → Resource 1
User → Manual mapping → Resource 2
User → Manual mapping → Resource 3
...
Repetir para CADA usuário × CADA recurso
```

**DEPOIS (Modelo de Grupo)**:
```
1. Criar grupo: "Shipping and Receiving"
2. Configurar permissões do grupo UMA VEZ:
   - Create shipping label
   - Track shipment
   - View monthly reports
   - Access customer data
3. Adicionar usuários ao grupo
4. TODOS os usuários herdam automaticamente as permissões
```

---

#### Benefícios da Autorização por Grupos

**Escalabilidade**:
- ✅ 1 usuário ou 1.000 usuários = mesmo esforço administrativo
- ✅ Adicionar usuário = 1 ação simples (adicionar ao grupo)
- ✅ Modificar permissões = alterar grupo (afeta todos automaticamente)

**Eficiência**:
- 10 usuários + 3 recursos → Sem grupo: 30 configurações
- 10 usuários + 3 recursos → Com grupo: 1 grupo + 10 adições = 11 ações
- 100 usuários + 100 recursos → Sem grupo: 10.000 configurações
- 100 usuários + 100 recursos → Com grupo: 1 grupo + 100 adições = 101 ações

**Manutenção**:
- Mudanças em permissões = atualizar grupo (não cada usuário)
- Onboarding = adicionar ao grupo apropriado
- Offboarding = remover do grupo

---

### 4.8 Tipos de Authorization Models

**Principais modelos mencionados**:
1. **Role-based** (Baseado em função)
2. **Organization-based** (Baseado em organização)
3. **Attribute-based** (Baseado em atributos)
4. **Many other characteristics** (Muitas outras características)

---

## Resumo - Pontos-Chave

### AAA Framework Resumido

| **Componente** | **Pergunta** | **Função** |
|----------------|--------------|------------|
| **Authentication** | Quem é você? | Verificar identidade |
| **Authorization** | O que você pode fazer? | Determinar permissões |
| **Accounting** | O que você fez? | Registrar atividades |

### Fluxo Completo AAA
```
1. IDENTIFICATION → "Eu sou João"
2. AUTHENTICATION → "Aqui está minha senha para provar"
3. AUTHORIZATION → "João pode acessar X, Y, Z"
4. ACCOUNTING → "João acessou X às 14:30, baixou Y às 14:35..."
```

### Device Authentication

**Elementos-chave**:
- ✅ Certificate Authority (CA) = essencial
- ✅ Device Certificate = assinado pela CA
- ✅ Verification = durante login
- ✅ Chain of Trust = Root CA → CA → Device

### Authorization Scaling

**Sem grupos**: Usuários × Recursos = Configurações necessárias
**Com grupos**: 1 grupo + N usuários = Escalabilidade infinita

**Regra de ouro**: Use abstração (grupos) para escalar!

### Conceitos Críticos para Certificação

1. **AAA** não é apenas um framework, é a BASE da segurança
2. **Central AAA Server** = melhor prática (não armazenar credenciais localmente)
3. **Certificates** substituem passwords para dispositivos
4. **Authorization Models** são essenciais para escala empresarial
5. **Groups** > Individual permissions (sempre!)
