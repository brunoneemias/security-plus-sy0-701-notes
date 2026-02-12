# Security+ SY0-701 Study Notes

## Section 1: General Security Concepts

### 1.1 Categorias de Controles de Segurança

#### Technical Controls
Controles implementados através de sistemas tecnológicos, incluindo:
- Controles do sistema operacional
- Firewalls
- Antivírus
- Outros sistemas de segurança baseados em tecnologia

#### Managerial Controls
Controles administrativos relacionados ao planejamento e gestão da segurança:
- Associados ao design de segurança
- Relacionados à implementação de políticas e procedimentos
- Focados em aspectos administrativos e gerenciais
- Security policies (políticas de segurança)
- Standard Operating Procedures (procedimentos operacionais padrão)

#### Operational Controls
Controles que utilizam pessoas para gerenciar a segurança:
- Diferente dos controles técnicos, dependem de intervenção humana
- Envolvem processos e procedimentos executados por pessoas

#### Physical Controls
Controles que limitam o acesso físico a recursos:
- Limitam acesso a prédios, salas ou dispositivos
- Exemplos: guard shacks (guaritas), cercas, fechaduras
- Badge readers (leitores de crachá) para controlar acesso a áreas específicas

---

### 1.2 Tipos de Controles de Segurança

#### Preventive (Preventivo)
Controles que limitam o acesso a recursos específicos:
- **Objetivo**: Impedir que uma violação de segurança ocorra
- **Exemplos**:
  - Regras de firewall que bloqueiam acesso a áreas da rede
  - Guard shack verificando identificação na entrada
  - Door locks (fechaduras)

#### Deterrent (Dissuasivo)
Controles que desencorajam ataques:
- **Objetivo**: Fazer o atacante pensar duas vezes antes de agir
- **Não previne** completamente o acesso, mas cria hesitação
- **Exemplos**:
  - Splash screens com avisos de segurança ao iniciar aplicações
  - Warning signs (placas de aviso)
  - Reception desk (recepção)

#### Detective (Detectivo)
Controles que identificam e alertam sobre violações:
- **Objetivo**: Detectar quando uma violação ocorreu
- **Não previne** o acesso, mas registra e alerta
- **Exemplos**:
  - Coleta e revisão de system logs
  - Patrulhas de propriedade
  - Motion detectors (detectores de movimento)
  - Property patrols (patrulhas de propriedade)

#### Corrective (Corretivo)
Controles aplicados **após** a detecção de um evento:
- **Objetivo**: Reverter o impacto ou minimizar o tempo de inatividade
- **Ocorre depois** que o evento foi detectado
- **Exemplos**:
  - Backup recovery (restauração de backup) após ransomware
  - Políticas para criar alertas de incidentes
  - Contact authorities (contatar autoridades) após invasões
  - Fire extinguisher (extintor de incêndio)

#### Compensating (Compensatório)
Controles alternativos quando não há recursos para resolver diretamente:
- **Objetivo**: Fornecer meios alternativos de controle
- **Uso**: Geralmente temporário até implementar solução definitiva
- **Exemplos**:
  - Block instead of patch: criar regra de firewall enquanto aguarda patch de vulnerabilidade
  - Separation of duties (separação de funções)
  - Power backups (backups de energia)

#### Directive (Diretivo)
Controles que direcionam comportamento (controle fraco):
- **Objetivo**: Direcionar usuários a agir de forma mais segura
- **Característica**: Depende da decisão do usuário
- **Relativamente fraco** pois requer julgamento humano
- **Exemplos**:
  - File storage policies: exigir que usuários armazenem dados sensíveis em pastas protegidas
  - Compliance policies (políticas de conformidade)
  - Security policy training (treinamento em políticas de segurança)
  - Sign: Authorized Personnel Only (placas: "Somente Pessoal Autorizado")

---

### 1.3 Matriz de Categorias e Tipos de Controles

| **Categorias** | **Preventive** | **Deterrent** | **Detective** | **Corrective** | **Compensating** | **Directive** |
|----------------|----------------|---------------|---------------|----------------|------------------|---------------|
| **Technical** | Firewall | Splash screen | System logs | Backup recovery | Block instead of patch | File storage policies |
| **Managerial** | On-boarding policy | Demotion | Review login reports | Policies for reporting issues | Separation of duties | Compliance policies |
| **Operational** | Guard shack | Reception desk | Property patrols | Contact authorities | Require multiple security staff | Security policy training |
| **Physical** | Door lock | Warning signs | Motion detectors | Fire extinguisher | Power backups | Sign: Authorized Personnel Only |

---

## Notas de Estudo

### Pontos-Chave para Memorização:
1. **Categorias** descrevem COMO o controle é implementado (Technical, Managerial, Operational, Physical)
2. **Tipos** descrevem QUANDO e QUAL o propósito do controle (Preventive, Deterrent, Detective, Corrective, Compensating, Directive)
3. **Preventive** = ANTES (impede)
4. **Detective** = DURANTE (detecta)
5. **Corrective** = DEPOIS (corrige)
6. **Directive** é o mais FRACO (depende de pessoas tomarem decisões corretas)
