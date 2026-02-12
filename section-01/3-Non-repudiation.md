## Aula 3: Non-repudiation

### 3.1 Conceito Fundamental de Non-repudiation

**Definição**: Garantia criptográfica de que quando alguém envia dados a um terceiro, esse terceiro pode verificar que a informação realmente veio do remetente.

**Analogia**: Similar a um contrato assinado em papel
- Assinamos nosso nome no contrato
- Qualquer pessoa pode ver a assinatura e verificar que foi assinada por nós
- Na criptografia, temos recursos similares

**Componentes do Non-repudiation**:
1. **Proof of Integrity** (Prova de Integridade)
2. **Proof of Origin** (Prova de Origem)
3. **High Assurance of Authenticity** (Alta garantia de autenticidade)

---

### 3.2 Proof of Integrity (Prova de Integridade)

#### Conceito
Verificar que os dados recebidos são exatamente os mesmos que foram originalmente enviados.

**Características**:
- Dados são precisos e consistentes
- Nada dentro dos dados foi alterado
- Garante integridade, mas **NÃO** identifica o remetente

#### Hashing

**Definição**: String curta de texto criada com base nos dados do plaintext (texto original).

**Também conhecido como**:
- Message Digest
- Fingerprint (impressão digital)

**Funcionamento**:
- Se qualquer dado mudar → hash diferente
- Assim como impressões digitais: pessoa diferente = impressão diferente

**Limitação**: Hash verifica integridade, mas **não associa** dados a um indivíduo específico.

---

### 3.3 Exemplo Prático de Hashing

#### Caso: Project Gutenberg Encyclopedia

**Cenário**:
- Download do Volume 1 da Gutenberg Encyclopedia
- Tamanho: 8.1 MB de dados
- Hash gerado do arquivo completo

**Teste de Integridade**:
1. Mudança de **um único caractere** no arquivo
2. Tamanho do arquivo permanece o mesmo (8.1 MB)
3. Hash resultante será **completamente diferente**
4. Impossível para humanos identificar a mudança lendo 8.1 MB de texto

**Soluções para Verificação**:
- Download novamente para verificar corrupção/modificação
- Usar **diff** ou comparação entre os dois arquivos
- Localizar exatamente onde a mudança ocorreu

**Resultado**: Hashes fornecem **proof of integrity** - sabemos se algo foi alterado durante o envio.

---

### 3.4 Proof of Origin (Prova de Origem)

**Conceito**: Nível adicional de integridade que verifica **quem** enviou os dados.

**Também chamado de**: Authentication (autenticação da fonte da mensagem)

#### Digital Signature (Assinatura Digital)

**Funcionalidade**:
- Fornece **non-repudiation**
- Identifica quem enviou os dados
- Qualquer terceiro pode examinar e verificar a transação
- Confirmação de que a informação realmente veio da parte remetente

**Componentes**:
1. **Private Key** (Chave Privada)
   - Conhecida **apenas** pelo remetente
   - Ninguém mais possui cópia
   - Usada para criar a assinatura

2. **Public Key** (Chave Pública)
   - Disponível para qualquer pessoa
   - Usada para verificar a assinatura
   - Confirma que a private key foi usada

---

### 3.5 Processo de Assinatura Digital

#### Na Prática
Geralmente é simples: clicar em "Add Digital Signature" e a criptografia acontece nos bastidores.

#### Processo Técnico Detalhado

**PARTE 1 - Alice Envia Mensagem para Bob**

**Passo 1: Criação do Hash**
- Alice escreve: "You're hired, Bob"
- Sistema cria hash da mensagem

**Passo 2: Criptografia com Private Key**
- Alice criptografa o hash com sua **private key**
- Apenas Alice tem essa chave

**Passo 3: Envio**
- Bob recebe:
  - Mensagem em plaintext: "You're hired, Bob"
  - Digital signature anexada (hash criptografado)
- Envio via email ou outro meio eletrônico

---

**PARTE 2 - Bob Verifica a Mensagem**

**Passo 1: Descriptografia**
- Bob usa a **public key** de Alice (disponível para todos)
- Descriptografa a digital signature
- Obtém o hash original criado por Alice

**Passo 2: Criação de Novo Hash**
- Bob executa o **mesmo algoritmo de hash**
- Usa o plaintext recebido: "You're hired, Bob"
- Cria seu próprio hash da mensagem

**Passo 3: Comparação**
- Bob compara:
  - Hash da digital signature (de Alice)
  - Hash que ele criou da mensagem
- **Se os hashes coincidirem**:
  ✅ Informação recebida = informação enviada (integridade)
  ✅ Mensagem teve que ser enviada por Alice (origem)

---

### 3.6 Fluxograma do Processo
```
ALICE (REMETENTE)
    ↓
Mensagem: "You're hired, Bob"
    ↓
[HASH] → Cria hash da mensagem
    ↓
[ENCRYPT com Private Key de Alice] → Hash criptografado
    ↓
Envia: Plaintext + Digital Signature
    ↓
═══════════════════════════════════
    ↓
BOB (DESTINATÁRIO)
    ↓
Recebe: "You're hired, Bob" + Digital Signature
    ↓
[DECRYPT com Public Key de Alice] → Hash original
    ↓
[HASH da mensagem recebida] → Novo hash
    ↓
[COMPARAÇÃO]
    ↓
Hashes idênticos? 
    ↓
SIM → ✅ Integridade + Origem Verificadas
NÃO → ❌ Mensagem foi alterada ou não é de Alice
```

---

### 3.7 Automação do Processo

**Na maioria dos casos**:
- Processo ocorre automaticamente ao clicar em um botão
- Usuário nunca vê o processo acontecer
- Tudo acontece "por trás dos bastidores"

**Importância de entender o processo**:
- Compreender a integridade que estamos buscando
- Entender a importância da proof of origin
- Crítico para transações que exigem confiança

---

## Resumo - Pontos-Chave

### Non-repudiation Garante:
1. ✅ **Integrity**: Dados não foram alterados
2. ✅ **Origin**: Identifica quem enviou
3. ✅ **Authenticity**: Alta garantia de autenticidade
4. ✅ **Impossível negar**: Remetente não pode negar que enviou

### Diferenças Importantes:

| **Hash Simples** | **Digital Signature** |
|------------------|----------------------|
| Verifica integridade | Verifica integridade + origem |
| Não identifica remetente | Identifica remetente |
| Apenas proof of integrity | Proof of integrity + proof of origin |
| Qualquer um pode criar | Apenas dono da private key pode criar |

### Elementos-Chave:
- **Hash**: Fingerprint dos dados
- **Private Key**: Só o remetente possui
- **Public Key**: Todos podem usar para verificar
- **Digital Signature**: Hash + Private Key encryption
- **Verification**: Public Key + Comparação de hashes

### Caso de Uso Principal:
Transações que requerem **prova irrefutável** de que:
1. Os dados são íntegros
2. Vieram de uma fonte específica
3. Não podem ser negados posteriormente
