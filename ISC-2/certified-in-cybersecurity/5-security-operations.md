## Data Handling – Ciclo de Vida dos Dados

dados → passam por um ciclo de vida próprio  
modelo pode variar → mas etapas principais são comuns  

### 6 fases principais

create  
- geração do conhecimento  
- inicialmente conhecimento tácito  

store  
- registro formal (torna explícito)  
- banco de dados, arquivos, sistemas  

use  
- consulta, processamento, modificação  
- pode alterar, complementar ou apagar parcialmente  

share  
- envio para terceiros  
- cópia ou movimentação de local  
- aumenta superfície de risco  

archive  
- retenção para uso futuro  
- não está ativo, mas precisa proteção  

destroy  
- descarte seguro  
- quando não há mais necessidade legal ou operacional  

### Estados do dado

in use → sendo processado  
at rest → armazenado  
in motion → em trânsito  

### Importância para segurança

- ajuda a alinhar responsabilidades (usuários, TI, segurança, compliance)  
- facilita aplicar controles adequados em cada fase  
- base para governança e classificação da informação  
---

## Encryption Overview

criptografia → base da segurança digital moderna  
usada em: transações, atualizações de software, contratos digitais, e-mails  

### Conceito central

plaintext → dado original, legível (não criptografado)  
ciphertext → dado cifrado, ilegível sem chave  
encryption → transforma plaintext em ciphertext  
decryption → processo reverso  
key → elemento que permite cifrar/decifrar  

objetivo → tornar informação ininteligível para não autorizados  

### Plaintext pode ser

- texto e números  
- imagens, áudio, vídeo  
- registros de banco de dados  
- qualquer dado digital  
obs: nem todo plaintext é legível por humanos  

### Serviços de segurança fornecidos

confidentiality  
- oculta o conteúdo da informação  
- apenas o destinatário autorizado consegue entender  

integrity  
- garante que o conteúdo não foi alterado  
- uso de hash functions e assinaturas digitais  
- qualquer modificação → gera resultado diferente  

### Encryption System (sistema criptográfico)

conjunto de:  
- hardware  
- software  
- algoritmos  
- chaves (cryptovariables)  
- processos de key management  

fluxo básico  
plaintext → encryption (algoritmo + chave) → ciphertext  
ciphertext → decryption (algoritmo + chave) → plaintext  

---

## Security Awareness Training

Organizações utilizam três tipos principais de atividades de aprendizado:

### Education
- Ampliar o entendimento de conceitos.
- Relacionar ideias com experiências reais.
- Aplicar o conhecimento de forma prática.

### Training
- Desenvolver habilidades específicas.
- Foco na execução correta de tarefas.
- Ensina quando usar, como usar e qual técnica aplicar.
- Pode envolver tarefas simples ou processos complexos.

### Awareness
- Chamar atenção para riscos e responsabilidades.
- Gerar consciência sobre ameaças.
- Engajar o público.

## Objetivo do Security Awareness Training

- Garantir que todos compreendam suas responsabilidades.
- Reforçar accountability.
- Reduzir descuido e complacência.
- Diminuir riscos causados por falhas humanas.

## Ponto importante

Não depende de cargo ou nível hierárquico.  
Exemplo: um executivo recém-contratado pode precisar primeiro se tornar consciente das exigências de compliance antes de receber treinamento mais aprofundado.

## Ideia central

Pessoas são parte crítica da segurança.  
Awareness é a primeira camada de defesa.

---

## Data Security Event Example

Exemplo: análise de log bruto (raw log).  
Objetivo → identificar tentativa de acesso não autorizado a arquivo ou servidor.

### O que um log pode mostrar

- Quem tentou acessar (usuário/IP).
- Porta utilizada (segura ou suspeita).
- Tipo de tentativa (login, acesso a arquivo, exploração).
- Horário e origem da conexão.

Engenheiros de segurança aprendem a interpretar códigos e eventos para identificar:
- Tentativas de invasão.
- Uso indevido de portas.
- Possível comprometimento do servidor.

Hoje existem ferramentas mais amigáveis (SIEM, dashboards), mas entender log bruto continua essencial.

## Conceito importante

Segurança não é algo que se “pluga” depois.

- Patches e atualizações ajudam.
- Mas não corrigem uma arquitetura insegura.
- Segurança deve ser planejada desde o início.
- Deve estar presente antes mesmo da entrada dos dados na rede.

### Ideia central

Monitoramento + arquitetura segura desde a concepção  
Segurança eficaz começa no design, não na correção.

---

## Common Security Policies – Deeper Dive

Políticas de segurança  
→ alinhadas à missão, visão e necessidades da organização  

Devem sempre incluir:  
- Regras claras  
- Consequências por não conformidade  

### Penalidades (exemplos)

- Primeira violação → advertência  
- Reincidência → suspensão / afastamento  
- Violação grave → demissão  

Aplicação progressiva, dependendo da gravidade.

## Onboarding

- Políticas apresentadas formalmente na entrada do colaborador  
- Especialmente crítico para profissionais de segurança da informação  
- Funcionário deve assinar ciência (acknowledgment)  
- Deve existir documentação registrada  

Pode incluir:  
- Questionário ou quiz  
- Confirmação de entendimento real da política  

## Governança e Responsabilidade

- Deve estar claro quem é responsável por aplicar e fiscalizar as políticas  
- Políticas sustentam procedimentos técnicos  
- Data handling e controles de segurança precisam estar formalmente respaldados  

### Ideia central

Políticas são base da postura de segurança (baseline security posture).  
Sem política formal, não há sustentação para controle ou punição.