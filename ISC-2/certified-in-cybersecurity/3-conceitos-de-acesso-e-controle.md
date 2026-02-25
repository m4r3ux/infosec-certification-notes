Controles são meios de proteger quem acessa o que baseando-se em cargos.

Um gerente tem acesso à arquivos sensíveis, mas um profissional da área comercial não.

Um profissional de TI tem acesso ao servidor, mas o de RH não.

Tudo isso, visa manter e zelar pela tríade CIA - Confidencialidade, Integridade e Disponibilidade.

Não é apenas sobre restringir acesso à determinada tipo de informação ou sistema, mas também garantir que a pessoa com o nível de acesso condizente tenha acesso à informação, e a que não tem não tenha acesso.

---

O acesso é baseado em três elementos:

1. Sujeito
2. Objeto
3. Regra

### 1. Sujeito

É quem **solicita o acesso** (usuário, processo, programa, dispositivo etc.).

- É **ativo**, pois inicia a requisição.
- Possui um nível de autorização (permissões).

### 2. Objeto

É aquilo que **recebe a solicitação** (arquivo, sistema, servidor, banco de dados, prédio etc.).

- É **passivo**, pois apenas responde quando solicitado.
- Pode ter um proprietário, que define quem pode acessá-lo.
- Não possui lógica própria de controle de acesso — essa proteção é aplicada por outros mecanismos (como sistemas de gerenciamento de identidade).

### 3. Regra

Define se o acesso será **permitido ou negado**, com base na identidade e atributos do sujeito.  
Uma regra pode:

- Permitir ou negar acesso
- Definir nível de acesso
- Aplicar restrições (ex.: horário)
- Comparar múltiplos atributos

Essas regras geralmente ficam registradas em uma **lista de controle de acesso (ACL)**.

---

##  Defesa em Profundidade (Defense in Depth)

A **defesa em profundidade** é uma estratégia de segurança que aplica **múltiplas camadas de proteção** para proteger os ativos da organização (edifícios, redes, sistemas, aplicações e dados).

Ela integra **pessoas, processos e tecnologia**, criando barreiras em diferentes níveis para dificultar ou impedir ataques. Importante: não garante que um ataque nunca ocorrerá, mas **reduz significativamente a probabilidade de sucesso e o impacto**.

### Coceito central

Em vez de depender de um único controle de segurança, a organização implementa **camadas sucessivas de contramedidas**. Se uma falhar, outra ainda protege o ativo.
### Exemplos técnicos

- **Autenticação multifator (MFA)**:  Login com usuário e senha (algo que você sabe) + código enviado ao celular (algo que você tem).  Combinar dois fatores é mais seguro do que usar apenas um.
- **Múltiplos firewalls**: Redes não confiáveis (internet) são separadas das redes internas por camadas de firewalls.  Dados mais sensíveis podem ficar protegidos por **mais de um firewall**.
### Exemplo físico + técnico + administrativo

Para acessar dados em um data center:
1. **Controle físico** – porta trancada impede acesso ao local.
2. **Controle técnico/lógico** – regras de rede impedem acesso não autorizado aos sistemas.
3. **Controle administrativo** – políticas definem quem está autorizado a ter acesso.
### Tipos de controles na defesa em profundidade

- **Controles físicos** – portas, fechaduras, barreiras.
- **Controles técnicos/lógicos** – firewalls, autenticação, regras de acesso.
- **Controles administrativos** – políticas, procedimentos, regras formais.

---

## Princípio do Privilégio Mínimo

O **princípio do privilégio mínimo** estabelece que cada usuário deve possuir apenas o nível de acesso estritamente necessário para executar suas funções, nada além disso. Essa prática é aplicada por meio do gerenciamento de acesso privilegiado e contribui para proteger a:

- **Confidencialidade**
- **Integridade**
- **Disponibilidade**

### Exemplos práticos

- Funcionários do setor financeiro podem visualizar dados financeiros de clientes.
- Um grupo ainda mais restrito pode alterar ou excluir esses dados.
- Em ambientes de saúde, profissionais acessam apenas as informações necessárias ao seu trabalho.
- O acesso pode ser:
  - Temporário  
  - Limitado a horários específicos  
  - Restrito a determinados campos ou tipos de dados  

### Monitoramento e proteção adicional

Os sistemas registram e monitoram acessos a informações sensíveis. Caso alguém tente acessar dados sem as permissões adequadas, um alerta pode ser gerado para análise do incidente.

Quanto mais sensível for a informação ou maior o nível de privilégio concedido, mais rigorosos devem ser os controles aplicados, como o uso de **autenticação multifator (MFA)**.

---

## Controles de Acesso Lógico

Enquanto os **controles de acesso físico** são mecanismos tangíveis que impedem o acesso a áreas ou ativos (como portas e fechaduras), os **controles de acesso lógico** são métodos eletrônicos que restringem o acesso a sistemas e, em alguns casos, até a ativos físicos integrados a esses sistemas.

Eles determinam quem pode acessar recursos digitais, mesmo que a pessoa já possua acesso físico ao local.

### Exemplos de controles de acesso lógico

- **Senhas**
- **Biometria** (implementada em dispositivos como smartphones ou laptops)
- **Leitores de crachá ou token** conectados a sistemas

Esses mecanismos funcionam como uma camada adicional de proteção, garantindo que apenas usuários autorizados tenham acesso lógico aos ativos da organização.

---

## Controls and Risks

Controles são mecanismos utilizados para **reduzir riscos** a um nível aceitável, de acordo com a tolerância ao risco de uma pessoa ou organização.

### Tipos de controles

- **Controle físico**: mecanismo tangível ou ação concreta.  
  - Exemplo: cinto de segurança.  
  - Exemplo: fixar uma estante na parede.

- **Controle administrativo**: leis, normas, políticas ou regulamentos.  
  - Exemplo: lei que obriga o uso do cinto de segurança.  
  - Exemplo: código de construção que exige a fixação de estantes.

### Funcionamento conjunto

Controles administrativos e físicos atuam em conjunto para mitigar riscos.

No exemplo da estante:

- **Risco**: queda da estante e possível lesão.
- **Controle administrativo**: exigência legal de fixação.
- **Controle físico**: suporte ou braçadeira prendendo a estante à parede.

Um controle tem como objetivo reduzir o risco para dentro da tolerância aceitável, não necessariamente eliminá-lo completamente.

---
## Privileged Access Management

Privileged Access Management (PAM) é o gerenciamento de acessos privilegiados concedidos a usuários ou contas administrativas.

Ele controla permissões como:

- Criar
- Ler
- Atualizar
- Excluir

### Problema do acesso privilegiado permanente

Em um cenário onde a equipe de TI adiciona suas contas ao grupo **Domain Admins**, os privilégios administrativos ficam ativos continuamente.

Se um administrador:

- Abrir um e-mail malicioso
- Executar um anexo infectado

O malware (como ransomware) pode:

- Utilizar os privilégios elevados
- Criptografar todos os servidores e estações de trabalho

Sem PAM, os privilégios administrativos permanecem ativos 24 horas por dia, aumentando o impacto de incidentes.

### Just-in-Time Privileged Access

O modelo Just-in-Time (JIT):

- Ativa privilégios elevados apenas quando necessário.
- Concede permissões específicas por função.
- Remove privilégios após a conclusão da tarefa.

Assim:

- Atividades rotineiras (ex.: leitura de e-mails) não usam privilégios administrativos.
- O risco e o impacto de ataques são reduzidos.

### Importância do PAM

O gerenciamento de acesso privilegiado:

- Reduz a superfície de ataque.
- Limita o impacto de malware.
- Garante uso controlado de privilégios elevados.
- Aplica o princípio do menor privilégio.

---
## Authorized Versus Unauthorized Personnel

O acesso a recursos envolve duas etapas principais:

- **Autenticação**: confirmação da identidade do usuário (subject).
- **Autorização**: verificação se o usuário tem permissão para executar determinada ação.

Após a autenticação, o sistema consulta uma **matriz de segurança** com níveis de acesso previamente definidos.

### Exemplos

- **Acesso físico**:  
  Um crachá é apresentado na porta do data center.  
  O sistema verifica o ID na matriz de segurança:
  - Se autorizado → a porta é liberada.
  - Se não autorizado → a porta permanece trancada.

- **Acesso lógico**:  
  Um usuário tenta excluir um arquivo.
  - Se possuir permissão → o arquivo é excluído.
  - Se não possuir → o sistema exibe erro e mantém o arquivo.

---

## Provisionamento de Usuários

O provisionamento define como contas são criadas, modificadas ou desativadas.

### 1. Novo funcionário

- O gestor solicita a criação da conta.
- Define-se o nível de acesso adequado à função.
- Permissões elevadas podem exigir aprovação adicional.

### 2. Mudança de cargo

- Permissões são ajustadas conforme o novo papel.
- Acessos que não são mais necessários devem ser removidos.

### 3. Desligamento

- A conta deve ser desativada após a data de saída.
- Recomenda-se manter a conta desativada antes da exclusão definitiva para preservar trilhas de auditoria.
- A conta deve ser removida de grupos e perfis de acesso.

Isso protege:

- A empresa, evitando acessos indevidos.
- O ex-funcionário, impedindo uso indevido da conta.

---

## Boa prática: evitar privilege creep

Não é recomendado copiar o perfil de um usuário existente para criar outro.

Motivo:

- Permissões temporárias podem permanecer.
- O novo usuário pode receber privilégios excessivos.

Boa prática:

- Criar **papéis padronizados (roles)**.
- Basear novos usuários nesses padrões.
- Aplicar o princípio do **menor privilégio**.
---
## Privileged Accounts

Contas privilegiadas possuem permissões superiores às de usuários comuns, como acesso administrativo ou funções críticas de gerenciamento.

### Quem utiliza contas privilegiadas

- **Administradores de sistemas**  
  Responsáveis por sistemas operacionais, implantação de aplicações e desempenho.

- **Help Desk / Suporte de TI**  
  Necessitam executar operações restritas em endpoints, servidores e aplicações.

- **Analistas de segurança**  
  Podem precisar de acesso amplo à infraestrutura, sistemas e dados.

Também podem existir contas privilegiadas específicas para projetos ou clientes.

---

## Riscos associados

O uso indevido ou abuso de privilégios pode causar danos significativos à organização.  
Por isso, controles adicionais são necessários.

---

## Medidas de controle para contas privilegiadas

### 1. Logging mais detalhado

- Registro extensivo das ações realizadas.
- Logs servem como:
  - Mecanismo de dissuasão.
  - Ferramenta de auditoria.
  - Evidência para investigação.

---

### 2. Controles de acesso mais rigorosos

- Uso obrigatório de MFA.
- Autenticação adicional para ativação de privilégios.
- Implementação de **Just-in-Time (JIT)** para ativar privilégios apenas quando necessário.

---

### 3. Verificação de confiança reforçada

- Background checks mais detalhados.
- Acordos de confidencialidade mais rigorosos.
- Possíveis verificações financeiras.
- Revisões periódicas ou baseadas em eventos.

---

### 4. Auditoria contínua

- Monitoramento mais frequente que o de usuários comuns.
- Revisão sistemática das ações privilegiadas.

---

## Exemplo prático (Help Desk)

Em um ambiente Windows, redefinir senhas pode exigir privilégios de *Domain Admin*.

Boa prática:

- Conceder apenas permissões específicas (reset de senha e desbloqueio de conta).
- Evitar conceder acesso total ao domínio.
- Registrar e auditar todas as redefinições.
- Comparar relatórios diários com tickets do Help Desk.

Isso permite:

- Resolver problemas rapidamente.
- Manter segurança.
- Aplicar o princípio do menor privilégio.
---

## Monitoring

Monitoramento é um componente essencial da segurança física e envolve o uso de controles, registros e sistemas de detecção para proteger ativos organizacionais.

## Principais mecanismos de monitoramento

### Câmeras

- Integradas ao programa geral de segurança.
- Funcionam como elemento dissuasório.
- Podem detectar atividades quando combinadas com sensores.
- Fornecem evidência forense quando há gravação.
- Úteis em áreas de difícil acesso ou que exigem registro detalhado.

### Logs físicos

Um log é um registro de eventos ocorridos.

Exemplos:
- Livro de registro manual (sign-in).
- Sistema eletrônico de controle de acesso.

Boas práticas:
- Reter logs conforme exigências legais ou de negócio.
- Proteger contra manipulação.
- Proteger contra divulgação não autorizada.
- Revisar regularmente conforme política organizacional.

Logs são essenciais para comprovação de conformidade, investigações forenses e identificação de incidentes.

### Anomalias em logs

Anomalia é qualquer evento fora do padrão esperado.

Exemplos:
- Lacunas em data ou hora.
- Bloqueios frequentes de conta.
- Tentativas de gravação em diretórios protegidos.

Registrar tudo indiscriminadamente não é recomendado, pois gera volume excessivo de dados.

### Sistemas de alarme

- Alertam quando portas ou janelas são abertas sem autorização.
- Podem exigir código ou crachá válido para evitar disparos indevidos.
- Alarmes de incêndio detectam calor ou fumaça.
- Botões de pânico notificam autoridades ou equipe de segurança.

### Guardas de segurança

- Funcionam como controle físico eficaz.
- Reduzem riscos de personificação.
- Dificultam práticas como tailgating.

### Sensores de perímetro

Podem incluir:
- Infravermelho.
- Micro-ondas.
- Lasers.
- Sensores de vibração em cercas.
- Sensores integrados a portões e catracas.

Esses sensores ajudam a detectar tentativas de invasão ou violação do perímetro.

## Retenção de logs

A retenção deve seguir:

- Políticas internas.
- Requisitos legais.
- Regulamentações do setor.

O padrão PCI DSS, por exemplo, exige retenção de um ano de logs.

Se não houver exigência específica, o departamento jurídico deve definir o período adequado.

## Elementos centrais do monitoramento

- Controles de acesso físico.
- Monitoramento de entrada e saída.
- Registro e auditoria de eventos.
- Proteção adequada dos logs.

Esses elementos sustentam a segurança organizacional de forma integrada.