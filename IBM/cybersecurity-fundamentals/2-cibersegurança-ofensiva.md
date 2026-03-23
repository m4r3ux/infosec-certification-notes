## **Objetivos do aprendizado  

Depois de concluir este curso, você será capaz de: 

- Comparar os cinco principais grupos de atores de ameaças com base em seus perfis e características
- Descrever tipos comuns de ataques cibernéticos
- Explicar a estrutura geral de um ataque cibernético típico descrito na estrutura Cyber Kill Chain
- Identificar táticas e técnicas de invasores cibernéticos com a matriz MITRE ATT&CK
- Explicar os principais elementos do ecossistema do crime cibernético
- Descrever técnicas comuns de engenharia social
- Descrever inteligência de código aberto (OSINT) e fontes padrão que os invasores cibernéticos utilizam
- Explicar o propósito e as informações apresentadas por técnicas típicas de varredura técnica
- Realizar reconhecimento de rede com ferramentas de varredura de rede
- Liste os detalhes e as lições aprendidas com vários ataques cibernéticos de alto perfil

---
## Modulo 1 - Grupos de atores de ameaca

## Conceitos

- Atacante: pessoa que realiza um ataque sem autorizacao
- Agente de ameaca: entidade que representa uma possivel ameaca (pode ainda nao ter atacado)

Diferenca:
- Atacante = ja executa ataque
- Agente de ameaca = potencial de ataque

## Tipos de agentes de ameaca

### Script kiddie
- Baixa habilidade tecnica
- Usa ferramentas prontas
- Motivacao: curiosidade ou diversao

### Hacktivista
- Motivacao politica ou ideologica
- Realiza ataques por causa de causas

### Gangue criminosa
- Grupo organizado
- Motivacao: dinheiro
- Atividades: fraude, ransomware, roubo de dados

### Hacker de estado-nacao
- Ligado a governos
- Alto nivel tecnico e recursos
- Objetivo: espionagem ou sabotagem

### Agente interno malicioso
- Pessoa de dentro da organizacao
- Ja possui acesso ao sistema
- Pode agir por vinganca ou ganho financeiro

## Objetivo

- Entender os tipos de agentes de ameaca
- Comparar motivacoes, recursos e comportamentos

## Resumo

- Agente de ameaca = risco potencial
- Existem 5 principais tipos
- Diferenciam-se por motivacao, habilidade e recursos

---

## Modulo 2 - Tipos de ataques ciberneticos

## Conceito

- Ataques ciberneticos sao metodos usados para explorar sistemas
- Podem focar em:
  - Vulnerabilidades tecnicas (sistemas, redes)
  - Vulnerabilidades humanas (engenharia social)

## Tipos de ataques

### DoS (Denial of Service)
- Ataque de negacao de servico
- Objetivo: derrubar um sistema ou servico
- Fazendo sobrecarga de requisicoes

### DDoS (Distributed Denial of Service)
- Versao distribuida do DoS
- Usa varios dispositivos (botnet)
- Mais dificil de bloquear

### Phishing
- Enganar o usuario para roubar informacoes
- Ex: emails falsos
- Objetivo: senhas, dados bancarios

### Spear phishing
- Phishing direcionado
- Alvo especifico (pessoa ou empresa)
- Mais sofisticado e convincente

### Malware
- Software malicioso
- Tipos:
  - Virus
  - Trojan
  - Ransomware
- Objetivo: danificar, roubar ou controlar sistemas

### MitM (Man-in-the-Middle)
- Intercepta comunicacao entre duas partes
- Pode roubar ou alterar dados

### Ataques DNS
- Exploram o sistema de nomes de dominio
- Podem redirecionar usuarios para sites falsos

## Objetivos do modulo

- Entender os principais tipos de ataques
- Reconhecer como a IA pode aumentar ataques
- Analisar ameacas em tempo real

## Resumo

- Ataques podem explorar tecnologia ou pessoas
- Existem varios tipos comuns
- Diferem por tecnica e objetivo
---

## Modulo 3 - Estrutura de um ataque cibernetico

## Conceito

- Ataques ciberneticos evoluem com o tempo
- Dependem de vulnerabilidades (ex: software desatualizado)
- Mesmo com mudancas, existe uma estrutura comum de ataque

## Estruturas utilizadas

### Cyber Kill Chain
- Modelo que descreve as etapas de um ataque
- Ajuda a entender como o ataque acontece do inicio ao fim
- Usado para detectar e interromper ataques

### MITRE ATT&CK
- Matriz que organiza tecnicas e taticas de invasores
- Baseada em ataques reais
- Ajuda a identificar comportamento de atacantes

## Objetivos do modulo

- Entender a estrutura de um ataque cibernetico
- Aplicar o modelo Cyber Kill Chain em cenarios reais
- Identificar tecnicas usando MITRE ATT&CK

## Resumo

- Ataques seguem uma estrutura, mesmo evoluindo
- Cyber Kill Chain mostra as etapas do ataque
- MITRE ATT&CK mostra como os ataques sao feitos

---

## Cyber Kill Chain

## Conceito

- Modelo criado pela Lockheed Martin
- Descreve as etapas de um ataque cibernetico
- Ataque e visto como um processo (nao evento unico)
- Etapas acontecem em ordem e dependem umas das outras

## Etapas

### 1. Reconhecimento
- Coleta de informacoes sobre o alvo
- Ex: pesquisa, escaneamento, engenharia social

### 2. Armamento
- Criacao ou obtencao de malware
- Baseado na vulnerabilidade encontrada

### 3. Entrega
- Envio do malware para o alvo
- Ex: email, download, USB infectado

### 4. Exploracao
- Execucao do malware
- Explora uma vulnerabilidade do sistema

### 5. Instalacao
- Malware cria persistencia
- Ex: backdoor, novas contas, acesso remoto

### 6. Comando e Controle (C2)
- Invasor se comunica com o sistema infectado
- Envia comandos e recebe dados

### 7. Acoes sobre objetivos
- Execucao do objetivo final
- Ex: roubo, alteracao ou destruicao de dados

## Resumo

- Ataques seguem 7 etapas sequenciais
- Cada etapa depende da anterior
- Objetivo: infiltrar, manter acesso e agir no sistema
---

## Matriz MITRE ATT&CK

## Conceito

- Criada pela organizacao MITRE
- Baseada em dados reais de ataques
- Reune taticas, tecnicas e procedimentos (TTP)
- Uso: entender e analisar ataques ciberneticos
- Disponivel gratuitamente

## Estrutura

- Colunas = taticas (objetivos do invasor)
- Linhas/itens = tecnicas (formas de atingir o objetivo)

## Como funciona

- O invasor tem um objetivo (tatica)
- Escolhe uma tecnica para atingir esse objetivo
- Se falhar, pode tentar outra tecnica

## Exemplo

- Objetivo: obter acesso ao sistema (tatica)
- Tecnica: forca bruta
  - Testa varias combinacoes de usuario e senha
- Se nao funcionar, tenta outra tecnica

## Resumo

- ATT&CK organiza como ataques sao feitos
- Taticas = objetivo
- Tecnicas = metodo
- Ajuda a identificar comportamento de invasores