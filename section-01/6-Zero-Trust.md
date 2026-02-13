# Security+ SY0-701 Study Notes

## Aula 6: Zero Trust

### 6.1 Problema das Redes Tradicionais

#### Modelo Tradicional de Segurança

**Característica principal**: "Hard shell, soft center" (Casca dura, interior mole)

**Problemas**:
- ✅ Firewall protege perímetro externo
- ❌ **Interior da rede relativamente aberto**
- ❌ Poucos security controls internos
- ❌ Movimento livre entre sistemas após autenticação inicial

**Consequências**:
- Usuários autorizados: movimento sem restrições ✅
- **Usuários não autorizados**: movimento sem restrições ❌
- **Malware**: propagação livre pela rede ❌

**Problema fundamental**: Confiança implícita após passar pelo firewall

---

### 6.2 Conceito de Zero Trust

#### Definição

**Zero Trust**: Nada é confiável por padrão - tudo requer verificação contínua

**Princípio fundamental**: "Never trust, always verify"

**Aplicação universal**:
- ✅ Cada dispositivo na rede
- ✅ Cada processo em execução
- ✅ Cada usuário na rede
- ✅ Cada tentativa de acesso a recursos

**Filosofia**: Autenticar/provar identidade **cada vez** que tentar acessar um recurso

---

#### Características do Zero Trust

**1. Continuous Verification (Verificação Contínua)**
- Não existe "confiança permanente"
- Cada acesso requer nova verificação
- Sessões não conferem acesso automático a outros recursos

**2. Multiple Security Layers (Múltiplas Camadas de Segurança)**
- Multi-factor authentication (MFA)
- Encryption at rest (dados armazenados)
- Encryption in transit (dados em trânsito)
- Granular permissions
- Additional firewalls internos
- Diversas políticas e controles

**3. Nothing is Trusted (Nada é Confiável)**
- Localização não garante confiança
- Credenciais anteriores não garantem acesso futuro
- Todos os recursos requerem verificação

---

### 6.3 Control Planes (Planos de Controle)

#### Conceito de Functional Planes of Operation

**Estratégia**: Dividir dispositivos de segurança em componentes funcionais menores

**Aplicação universal**:
- Physical devices (dispositivos físicos)
- Virtual devices (dispositivos virtuais)
- Cloud-based security processes (processos de segurança na nuvem)

**Benefício**: Separação de responsabilidades e controle granular

---

#### Os Dois Planos Principais

**1. Data Plane (Plano de Dados)**

**Definição**: Parte do dispositivo que **executa** o processo de segurança real

**Funções**:
- Processar frames, packets e network data em **tempo real**
- Realizar forwarding (encaminhamento)
- Executar Network Address Translation (NAT)
- Processar routing (roteamento)
- **Mover dados** de uma parte da rede para outra

**Exemplos de dispositivos**:
- Switches processando frames
- Routers processando packets
- Firewalls inspecionando tráfego

**Característica**: **Ação em tempo real**

---

**2. Control Plane (Plano de Controle)**

**Definição**: Parte que **gerencia e controla** as ações do data plane

**Funções**:
- Configurar policies e rules
- Definir se dados podem atravessar a rede
- Estabelecer forwarding policies
- Configurar routing
- Gerenciar routing tables
- Definir firewall rules
- Configurar NAT policies

**Exemplos de configurações**:
- Network address settings
- VLAN configurations
- Trunk configurations
- Security policies

**Característica**: **Configuração e gerenciamento**

---

### 6.4 Exemplo: Physical Switch

#### Separação de Planos em Switch Físico
```
┌─────────────────────────────────────┐
│      CONTROL PLANE                  │
│  - Configurações                    │
│  - Policies                         │
│  - Management                       │
└─────────────────────────────────────┘
            ↕ (controla)
┌─────────────────────────────────────┐
│      DATA PLANE                     │
│  - Interfaces físicas               │
│  - Forwarding de frames             │
│  - Processamento em tempo real      │
└─────────────────────────────────────┘
```

**Data Plane**: Interfaces na parte inferior do switch
- Movimento de dados entre partes da rede
- Forwarding de tráfego

**Control Plane**: Configurações do dispositivo
- Como o forwarding deve ocorrer
- Quais políticas aplicar
- Como gerenciar o tráfego

---

### 6.5 Aplicação em Diferentes Ambientes

#### Physical Devices
- Separação clara entre data plane e control plane
- Exemplos: switches, routers, firewalls físicos

#### Virtual Devices
- Mesma separação se aplica
- **Virtual switches**: data plane + control plane
- **Virtual firewalls**: data plane + control plane

#### Cloud-Based Security
- Controles de segurança na nuvem também usam separação
- Mesmos princípios de data plane e control plane
- Aplicação consistente independente do ambiente

---

### 6.6 Adaptive Identity (Identidade Adaptativa)

#### Conceito

**Definição**: Examinar identidade e aplicar controles baseados em múltiplos fatores - não apenas credenciais

**Objetivo**: Ser **mais inteligente** na avaliação de controles de segurança

---

#### Fatores Analisados

**1. Source of Requested Resources**
- **Exemplo**: 
  - Dados nos EUA sendo acessados de IP na China
  - **Ação**: Autenticação adicional necessária
- Verifica consistência geográfica

**2. Relationship to Organization**
- Employee (funcionário)?
- Contractor (contratado)?
- Full-time ou part-time?
- **Impacto**: Diferentes níveis de confiança

**3. Physical Location**
- Localização física do usuário
- Dentro ou fora das instalações
- País de origem da conexão

**4. Connection Type**
- VPN, direct connection, public network
- Tipo de rede (corporativa, pública, doméstica)

**5. IP Addresses**
- Histórico de IPs utilizados
- Padrões de acesso
- Anomalias de origem

**6. Additional Variables**
- Horário de acesso
- Dispositivo utilizado
- Comportamento histórico

---

#### Processo de Avaliação
```
Múltiplas variáveis → Análise automática → Determina nível de autenticação
```

**Resultado**: Sistema cria automaticamente autenticação **mais forte** quando necessário

**Exemplo prático**:
- Acesso normal do escritório: MFA padrão
- Acesso de localização incomum: MFA + verificação adicional
- Acesso de país suspeito: MFA + aprovação manual

---

### 6.7 Policy-Driven Access Control

#### Limitação de Entry Points (Pontos de Entrada)

**Estratégia**: Controlar WHERE (onde) as pessoas podem acessar a rede

**Métodos permitidos** (exemplo):
- ✅ Conexões de dentro do prédio
- ✅ Conexões via VPN
- ❌ Nenhum outro método

**Benefício**: Reduz superfície de ataque

---

#### Policy-Driven Access Control

**Definição**: Controle de acesso baseado em políticas que examina múltiplos data points

**Processo**:
```
1. Coletar TODOS os data points individuais
2. Consolidar informações
3. Decidir tipo de autenticação necessária
4. Verificar se pessoa é realmente quem afirma ser
```

**Características**:
- Análise holística
- Decisões baseadas em contexto completo
- Autenticação adaptativa

---

### 6.8 Security Zones (Zonas de Segurança)

#### Conceito

**Definição**: Categorização ampla de onde usuários estão conectando

**Objetivo**: Expandir além de relacionamento um-para-um (usuário → servidor)

**Foco**: Examinar **path completo da comunicação**

---

#### Tipos de Zonas

**Categorias principais**:
- **Untrusted Network** (Rede não confiável)
- **Trusted Network** (Rede confiável)
- **Internal Network** (Rede interna)
- **External Network** (Rede externa)

**Granularidade adicional**:
- VPN connections separadas
- Grupos por departamento
- Zonas por função organizacional

---

#### Funcionamento de Zonas

**Cenário 1: Untrusted → Trusted**
```
Untrusted Zone → [Policy Check] → Trusted Zone
```
**Regra exemplo**: Negar automaticamente acesso de zona não confiável para dispositivo em zona confiável

---

**Cenário 2: Trusted → Internal (Implicit Trust)**
```
Corporate Office (Trusted Zone) → Data Center (Internal Zone)
```

**Exemplo**:
- Usuário em escritório corporativo = **Trusted zone**
- Database server em data center = **Internal zone**
- **Política**: Comunicação Trusted → Internal = **Implicitly trusted**

**Benefício**: Balancear segurança com usabilidade

---

#### Regras entre Zonas

**Possibilidades**:
- Permitir comunicação entre zonas específicas
- Bloquear comunicação entre zonas específicas
- Exigir autenticação adicional entre zonas
- Aplicar policies diferentes por zona

**Flexibilidade**: Criar regras granulares sobre qual zona acessa quais outras zonas

---

### 6.9 Policy Enforcement Architecture

#### Componentes Principais

**1. Policy Enforcement Point (PEP)**

**Função**: Ponto de aplicação de políticas - "Gatekeeper"

**Características**:
- **TODO** tráfego deve passar pelo PEP
- Avalia subjects e systems
- Aplica políticas definidas

**Subjects and Systems**:
- Users (usuários)
- Individual processes (processos rodando no sistema)
- Applications (aplicações em uso)

**Importante**: PEP é uma **abstração** - pode ser múltiplos dispositivos trabalhando juntos

**Não decide**: PEP **não toma decisões** - apenas coleta informações e aplica decisões

---

**2. Policy Decision Point (PDP)**

Composto por:

**a) Policy Engine**

**Função**: Tomar decisões sobre permitir/negar tráfego

**Processo**:
1. Examina requests recebidos
2. Compara com security policies predefinidas
3. Toma decisão: **Granted**, **Denied**, ou **Revoked**

**Características**:
- Analisa autenticação
- Verifica conformidade com políticas
- Decide sobre acesso

---

**b) Policy Administrator**

**Função**: Comunicar decisões do Policy Engine para o PEP

**Responsabilidades**:
- Receber decisão do Policy Engine
- Criar access tokens ou credentials (se necessário)
- Enviar informações para Policy Enforcement Point

**Fluxo**:
```
Policy Engine → Decision → Policy Administrator → PEP
```

---

### 6.10 Zero Trust Model Completo

#### Fluxo de Comunicação
```
┌──────────────────────┐
│ UNTRUSTED ZONE       │
│ - Subjects           │
│ - Systems            │
└──────────┬───────────┘
           │ Data Plane
           ↓
┌──────────────────────┐
│ POLICY ENFORCEMENT   │
│ POINT (PEP)          │  ←──────────────────┐
└──────────┬───────────┘                     │
           │                                 │
           │ Needs enforcement?              │
           ↓                                 │
┌──────────────────────┐                    │
│ POLICY               │                    │
│ ADMINISTRATOR        │                    │
└──────────┬───────────┘                    │
           │                                 │
           ↓                                 │
┌──────────────────────┐                    │
│ POLICY ENGINE        │                    │
│ (Decision Point)     │                    │
└──────────┬───────────┘                    │
           │                                 │
           │ Decision                        │
           ↓                                 │
     Back to Policy Admin ───────────────────┘
           │
           │ Grant/Deny
           ↓
     Policy Enforcement Point
           │
           │ If Allowed
           ↓
┌──────────────────────┐
│ TRUSTED ZONE         │
│ - Enterprise         │
│   Resources          │
└──────────────────────┘
```

---

#### Processo Passo a Passo

**PASSO 1: Request Initiated**
```
Subjects/Systems (Untrusted Zone) → Data Plane → PEP
```

**PASSO 2: Enforcement Check**
```
PEP → Coleta informações → Envia para Policy Administrator
```

**PASSO 3: Decision Request**
```
Policy Administrator → Policy Engine
```

**PASSO 4: Policy Evaluation**
```
Policy Engine:
- Examina request
- Compara com policies
- Decide: Grant/Deny/Revoke
```

**PASSO 5: Decision Communication**
```
Policy Engine → Policy Administrator → PEP
```

**PASSO 6: Access Control**
```
PEP:
- Se permitido: Access to Trusted Zone + Enterprise Resource ✅
- Se negado: Block access ❌
```

---

## Resumo - Pontos-Chave

### Princípios Fundamentais Zero Trust

| **Princípio** | **Descrição** |
|---------------|---------------|
| **Never Trust, Always Verify** | Verificação contínua obrigatória |
| **Least Privilege** | Acesso mínimo necessário |
| **Assume Breach** | Agir como se rede já estivesse comprometida |
| **Verify Explicitly** | Usar todos os data points disponíveis |

### Comparação: Traditional vs Zero Trust

| **Aspecto** | **Traditional** | **Zero Trust** |
|-------------|----------------|----------------|
| **Trust** | Implícito após firewall | Nunca implícito |
| **Verification** | Uma vez no login | Contínua |
| **Network Segmentation** | Perímetro | Microsegmentação |
| **Access Control** | Baseado em localização | Baseado em identidade + contexto |

### Control Planes

**Data Plane**:
- ⚡ Real-time processing
- 📊 Forwarding, routing, NAT
- 🔄 Movement de dados

**Control Plane**:
- ⚙️ Configuration
- 📋 Policies e rules
- 🎛️ Management

### Adaptive Identity Factors

**Contexto completo** inclui:
- 📍 Location (física e lógica)
- 🔗 Connection type
- 🏢 Relationship to org
- 🌐 IP address
- ⏰ Time patterns
- 💻 Device type

### Security Zones

**Conceito**: Categorizar origem e destino de comunicação

**Regras**:
- Zone to zone permissions
- Implicit trust (quando apropriado)
- Explicit deny (quando necessário)

### Policy Architecture Components
```
PEP (Enforcement) ←→ Policy Administrator ←→ Policy Engine (Decision)
```

**PEP**: Gatekeeper - coleta e aplica
**Policy Engine**: Decisor - analisa e decide
**Policy Administrator**: Mensageiro - comunica decisões

### Implementation Checklist

Zero Trust requer:
- ✅ MFA em todos os acessos
- ✅ Encryption (at rest + in transit)
- ✅ Granular permissions
- ✅ Internal firewalls
- ✅ Continuous monitoring
- ✅ Adaptive authentication
- ✅ Security zones
- ✅ Policy-driven access

### Critical Concepts for Exam

1. **Zero Trust ≠ Zero Access**: Não é sobre bloquear tudo, é sobre verificar tudo
2. **Control Planes**: Separation of concerns em todos os níveis
3. **Adaptive Identity**: Context-aware authentication
4. **Security Zones**: Micro-segmentation vs perimeter only
5. **Policy Architecture**: PEP, Policy Engine, Policy Administrator working together
