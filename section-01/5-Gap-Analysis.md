## Aula 5: Gap Analysis

### 5.1 Conceito de Gap Analysis

**Definição**: Estudo comparativo entre onde estamos versus onde gostaríamos de estar.

**No contexto de IT Security**:
- Análise constante para entender necessidades futuras de segurança
- Simples de explicar, mas complexo de executar
- Requer análise profunda do ambiente atual
- Desenvolvimento de plano para alcançar objetivos

---

### 5.2 Complexidade e Escopo

#### Características do Processo

**Duração**:
- Processo envolvido e extenso
- Pode levar semanas, meses ou até **anos** para compilar

**Recursos Necessários**:
- Múltiplas pessoas da organização
- Plano de projeto extensivo
- Coleta de dados intensiva
- Emails, reuniões, documentação

**Desafio**: Compreender TODOS os aspectos de IT security e como se aplicam à organização

---

### 5.3 Baselines (Linhas de Base)

#### Importância das Baselines

**Propósito**: Ter algo para trabalhar em direção a um objetivo

**Benefícios**:
- Define metas claras para a organização
- Fornece framework de referência
- Permite medição de progresso

---

#### Tipos de Baselines Disponíveis

**1. NIST (National Institute of Standards and Technologies)**

**Documento**: Special Publication 800-171 Revision 2

**Título**: "Protecting Controlled Unclassified Information in Nonfederal Systems and Organizations"

**Uso**: Organizações que trabalham com informações governamentais não classificadas

---

**2. ISO/IEC 27001**

**Organização**: 
- International Organization for Standardization (ISO)
- International Electrotechnical Commission (IEC)

**Foco**: Information Security Management Systems (ISMS)

**Uso**: Padrão internacional amplamente adotado

---

**3. Custom Baselines (Baselines Personalizadas)**

**Características**:
- Criadas pela própria organização
- Baseadas em necessidades específicas
- Podem combinar elementos de múltiplos frameworks

**Quando usar**: Quando baselines padrão não atendem necessidades específicas

---

### 5.4 Análise de Pessoas e Processos

#### Avaliação de Pessoas

**Aspectos a avaliar**:

**1. Formal Experience (Experiência Formal)**
- Background em IT security
- Anos de experiência
- Certificações obtidas

**2. Training (Treinamento)**
- Tipo de treinamento recebido
- Atualização de conhecimentos
- Áreas de especialização

**3. Knowledge (Conhecimento)**
- Políticas de segurança específicas
- Procedimentos organizacionais
- Best practices da indústria

---

#### Avaliação de Processos

**Mesmo com pessoas certas**, é necessário avaliar:

**1. IT Systems (Sistemas de TI)**
- Sistemas existentes em operação
- Como se relacionam com políticas formais

**2. Security Policies (Políticas de Segurança)**
- Documentação central de políticas
- Alinhamento com práticas atuais
- Gaps entre política e implementação

**3. Procedures (Procedimentos)**
- Processos operacionais
- Compliance com políticas
- Efetividade na prática

---

### 5.5 Processo de Análise

#### Fase de Comparação

**PASSO 1: Identificação de Sistemas**
```
Inventariar sistemas existentes no ambiente
```

**PASSO 2: Identificação de Fraquezas**
```
Comparar sistemas atuais com baseline
Identificar weaknesses (fraquezas)
```

**PASSO 3: Comparação com Best Practices**
```
Avaliar processos mais efetivos
Entender como compensar fraquezas
```

**PASSO 4: Análise Detalhada**
```
Broad categories → Individual segments
```

---

#### Metodologia: Do Amplo ao Específico

**Abordagem**:
1. Começar com **broad categories** (categorias amplas)
2. Quebrar em **individual smaller segments** (segmentos menores individuais)
3. Análise detalhada de cada segmento

---

### 5.6 Exemplo Prático: NIST 800-171 Rev 2

#### Access Control Requirements

**Categoria Ampla**: Access Control
- Limitar acesso ao sistema a usuários não autorizados
- Processos agindo em nome de usuários autorizados
- Dispositivos

#### Quebra em Segmentos Individuais

**Account Management** inclui:

1. **User Registration and Deregistration**
   - Como usuários são registrados
   - Processo de desativação de contas

2. **User Access Provisioning**
   - Como acesso é provisionado
   - Processo de concessão de permissões

3. **Management of Privileged Access Rights**
   - Gestão de acessos privilegiados
   - Controle de contas administrativas

4. **Review of User Access Rights**
   - Revisões periódicas
   - Auditorias de permissões

5. **E outros controles específicos...**

**Análise**: Para cada segmento, avaliar quão bem os processos e procedimentos estão sendo seguidos

---

### 5.7 Compilação do Gap Analysis Report

#### Elementos do Relatório Final

**1. Comparison Summary (Resumo Comparativo)**
```
Baseline Objectives ↔ Current State
(Onde queremos estar) ↔ (Onde estamos)
```

**2. Gap Identification (Identificação de Lacunas)**
- Detalhamento de cada objetivo da baseline
- Perspectiva atual vs. desejada
- Nível de conformidade

---

#### Path to Compliance (Caminho para Conformidade)

**Pergunta mais difícil**: Como ir de onde estamos para onde queremos estar?

**Recursos Necessários**:

**1. Time (Tempo)**
- Planejamento de cronograma
- Fases de implementação
- Marcos de progresso

**2. Money (Dinheiro)**
- Orçamento necessário
- ROI esperado
- Custos de implementação

**3. Equipment (Equipamento)**
- Hardware necessário
- Software necessário
- Ferramentas de segurança

**4. Change Control (Controle de Mudanças)**
- Processo de implementação
- Gerenciamento de riscos
- Comunicação de mudanças

---

### 5.8 Estrutura do Relatório Final

#### Conteúdo Obrigatório

**1. Current State Analysis**
- Onde estamos hoje
- Inventário completo
- Identificação de gaps

**2. Pathway to Goals**
- Como chegar aos objetivos
- Recursos necessários
- Cronograma proposto

**3. Recommendations**
- Todas as recomendações para atingir baseline
- Priorizações
- Quick wins vs. long-term projects

---

### 5.9 Exemplo de Tabela de Gap Analysis

#### Sistema de Cores para Visualização

| **System Requirements** | **Location 1** | **Location 2** | **Location 3** | **Location 4** | **Location 5** | **Location 6** | **Location 7** |
|------------------------|----------------|----------------|----------------|----------------|----------------|----------------|----------------|
| Access Control | 🟢 | 🟡 | 🔴 | 🟢 | 🟡 | 🔴 | 🟢 |
| Incident Response | 🟡 | 🟢 | 🔴 | 🟡 | 🔴 | 🟢 | 🟡 |
| Media Protection | 🔴 | 🟡 | 🟢 | 🔴 | 🟢 | 🟡 | 🔴 |
| Physical Protection | 🟢 | 🔴 | 🟡 | 🟢 | 🟡 | 🔴 | 🟢 |
| ...outros requisitos... | ... | ... | ... | ... | ... | ... | ... |

---

#### Código de Cores

**🟢 GREEN (Verde)**
- **Significado**: Relativamente próximo de atingir a baseline
- **Status**: Bom compliance
- **Ação**: Manutenção e melhorias incrementais

**🟡 YELLOW (Amarelo)**
- **Significado**: Ponto médio
- **Status**: Compliance parcial
- **Ação**: Requer atenção e melhorias

**🔴 RED (Vermelho)**
- **Significado**: Muito trabalho necessário
- **Status**: Não conforme com baseline
- **Ação**: Prioridade alta, requer ação imediata

---

### 5.10 Estratégia de Priorização

#### Approach Recomendado

**Para MAIOR IMPACTO na melhoria da segurança**:
```
Prioridade 1: 🔴 RED (Crítico)
    ↓
Prioridade 2: 🟡 YELLOW (Médio)
    ↓
Prioridade 3: 🟢 GREEN (Manutenção)
```

**Foco**: Começar com áreas críticas (vermelhas) para maximizar impacto

---

#### Detalhamento no Relatório

**Para cada cor, incluir**:

1. **Justificativa da Classificação**
   - Por que recebeu essa cor
   - Critérios utilizados
   - Evidências coletadas

2. **Gaps Específicos**
   - O que está faltando
   - Diferença entre atual e baseline
   - Impacto da lacuna

3. **Implementation Plan**
   - Como implementar controles de segurança
   - Passos específicos
   - Recursos necessários

4. **Timeline**
   - Cronograma estimado
   - Dependências
   - Marcos importantes

---

## Resumo - Pontos-Chave

### Processo de Gap Analysis
```
1. BASELINE SELECTION
   ↓
2. DATA GATHERING
   ↓
3. CURRENT STATE ANALYSIS
   ↓
4. GAP IDENTIFICATION
   ↓
5. PATH PLANNING
   ↓
6. FINAL REPORT
```

### Elementos Essenciais

| **Componente** | **Descrição** | **Importância** |
|----------------|---------------|-----------------|
| **Baseline** | Referência/meta | Define objetivos claros |
| **People Analysis** | Avaliação de equipe | Garante capacidade técnica |
| **Process Analysis** | Avaliação de processos | Identifica gaps operacionais |
| **Detailed Breakdown** | Segmentação granular | Permite análise profunda |
| **Color Coding** | Visualização rápida | Facilita priorização |
| **Implementation Path** | Plano de ação | Viabiliza mudanças |

### Baselines Principais para Certificação

**NIST SP 800-171 Rev 2**:
- Foco: Controlled Unclassified Information
- Uso: Organizações não federais com dados governamentais

**ISO/IEC 27001**:
- Foco: Information Security Management Systems
- Uso: Padrão internacional

**Custom Baselines**:
- Foco: Necessidades específicas
- Uso: Quando padrões não se aplicam

### Estrutura de Análise

**Top-Down Approach**:
- Broad Categories (ex: Access Control)
- Individual Controls (ex: User Registration)
- Specific Requirements (ex: Password policies)

### Priorização de Ações

**Baseada em impacto**:
1. 🔴 Critical gaps → Ação imediata
2. 🟡 Medium gaps → Planejamento de curto prazo
3. 🟢 Minor gaps → Melhoria contínua

### Recursos para Implementação

**4 Pilares**:
- ⏰ Time (Cronograma realista)
- 💰 Money (Orçamento adequado)
- 🔧 Equipment (Ferramentas necessárias)
- 📋 Change Control (Gestão de mudanças)

### Ciclo Contínuo

Gap Analysis **NÃO é evento único**:
- Repetir periodicamente
- Adaptar baselines
- Melhorar continuamente
