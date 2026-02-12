## Section 2: The CIA Triad

### 2.1 Fundamentos do CIA Triad

O CIA Triad é uma forma fácil de lembrar os fundamentos da segurança de TI.

**Nomenclatura alternativa**: Às vezes é referido como **AIC Triad** para diferenciá-lo da agência federal dos EUA (Central Intelligence Agency).

### 2.2 Os Três Pilares da Segurança

#### C - Confidentiality (Confidencialidade)

**Desafio**: Tornar dados disponíveis para outros, mas apenas para as pessoas certas.

**Métodos de Implementação**:

##### 1. Encryption (Criptografia)
- Uma pessoa criptografa os dados
- Envia para outra pessoa
- O destinatário descriptografa para ver o plaintext (texto original)
- **Proteção**: Qualquer pessoa interceptando os dados criptografados não consegue discernir informações importantes

##### 2. Access Controls (Controles de Acesso)
- Define limites sobre quem pode acessar determinados tipos de informação
- **Exemplo**: 
  - Departamento de Marketing: acesso total a apresentações de marketing
  - Departamento de Marketing: SEM acesso a informações contábeis da organização

##### 3. Authentication Factors (Fatores de Autenticação)
- Fatores adicionais de autenticação ao fazer login
- **Proteção**: Impede acesso a contas sem as credenciais apropriadas
- Múltiplos fatores = maior confidencialidade

---

#### I - Integrity (Integridade)

**Objetivo**: Verificar que os dados recebidos são exatamente os mesmos que foram enviados, sem alterações durante a transmissão.

**Métodos de Implementação**:

##### 1. Hashing
- **Processo**:
  1. Remetente cria um hash dos dados
  2. Envia dados + hash simultaneamente
  3. Destinatário executa a mesma função de hash
  4. Se os hashes coincidirem = dados íntegros
- **Validação**: Confirma que nenhuma alteração ocorreu durante a transmissão

##### 2. Digital Signatures (Assinaturas Digitais)
- **Processo**: Hash + criptografia assimétrica
- **Benefícios**:
  - Verifica que os dados não foram alterados
  - Confirma a identidade de quem enviou
- **Uso**: Importante para dados muito sensíveis
- **Nível adicional** de integridade comparado ao hashing simples

##### 3. Certificates (Certificados)
- Identifica dispositivos ou pessoas
- Fornece fatores adicionais de integridade
- **Uso comum**: Transferência de dados entre dispositivos

##### 4. Non-repudiation (Não-repúdio)
- **Definição**: Prova de integridade sem possibilidade de negação
- **Garantia**: Confirmação absoluta de que a informação recebida veio da parte originária
- Impossível para o remetente negar que enviou os dados

---

#### A - Availability (Disponibilidade)

**Objetivo**: Garantir que pessoas tenham acesso aos dados quando necessário.

**Métodos de Implementação**:

##### 1. High Availability Systems (Sistemas de Alta Disponibilidade)
- **Design**: Sistemas projetados para estar sempre operacionais
- Redundância de componentes

##### 2. Fault Tolerance (Tolerância a Falhas)
- **Conceito**: Múltiplos componentes redundantes
- **Funcionamento**: Se um componente falha, outro assume automaticamente
- **Resultado**: Operação normal continua sem interrupção

##### 3. Patching (Aplicação de Patches)
- Gerenciamento e atualização constante dos sistemas
- **Benefícios**:
  - Garante máxima estabilidade dos sistemas
  - Fecha vulnerabilidades de segurança existentes
  - Previne exploits e acessos não autorizados
- **Importância**: Manutenção contínua para disponibilidade

---

### 2.3 Representação Visual

O triad é frequentemente representado como um **triângulo**, onde cada lado representa um dos três objetivos de segurança:
```
        Confidentiality
              /\
             /  \
            /    \
           /      \
          /        \
         /          \
        /____________\
  Integrity      Availability
```

---

## Notas de Estudo

### Pontos-Chave para Memorização:

#### CIA Triad
1. **CIA** = Confidentiality + Integrity + Availability
2. Também chamado de **AIC Triad** (para evitar confusão com a agência CIA)
3. Representa os **três objetivos fundamentais** da segurança da informação
4. Todos os três pilares devem estar presentes para segurança efetiva

#### Confidentiality - Métodos Principais
- **Encryption**: Protege dados em trânsito
- **Access Controls**: Limita acesso baseado em permissões
- **Authentication**: Múltiplos fatores aumentam segurança

#### Integrity - Métodos Principais
- **Hashing**: Verifica se dados foram alterados
- **Digital Signatures**: Hash + identidade do remetente
- **Non-repudiation**: Prova irrefutável de origem

#### Availability - Métodos Principais
- **High Availability**: Sistemas sempre operacionais
- **Fault Tolerance**: Redundância para continuidade
- **Patching**: Manutenção preventiva contínua
