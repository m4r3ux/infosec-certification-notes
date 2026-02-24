## Terminologia de incidentes
O trabalho de um profissional de cibersegurança não é apenas de prevenção a riscos, mas também de respostas a incidentes.

Infelizmente nenhum sistema está seguro, e estarmos cientes de processos de respostas a incidentes é de suma importância para a integridade organizacional.

### Violação 
Qualquer incidente que envolva **perda de controle**, **comprometimento**, **divulgação não autorizada**, **aquisição não autorizada** ou situação semelhante em que:

- uma **pessoa não autorizada** acessa ou **pode ter acessado** informações pessoalmente identificáveis (PII); ou um **usuário autorizado** acessa PII para **finalidades não autorizadas**.

**Em resumo:** é considerado incidente de privacidade qualquer acesso — real ou potencial — a dados pessoais fora das permissões ou do propósito autorizado.

### Evento
Qualquer ocorrência observável em uma rede ou sistema, como logs, alterações, remoções, etc.

### Exploit
Um ataque em particular, é chamado assim por conta da maneira como tais ataques exploram as vulnerabilidades de um sistema.

### Incidente
Um evento que coloca ou pode colocar em risco a tríade CIA de um sistema de informação ou outros.

### Intrusão
Um evento ou combinação  de eventos de segurança que constituem um incidente onde o intruso ganha ou tenta ganhar acesso ao sistema ou recurso de sistema sem autorização.

### Ameaça
Qualquer evento que, por meio de um sistema de informação, possa causar **impacto negativo** à organização ou a terceiros devido a **acesso não autorizado, alteração, divulgação, destruição de dados ou negação de serviço**.

### Vulnerabilidade
Falha em sistemas, controles ou procedimentos de segurança que **pode ser explorada por uma ameaça**.

### Zero-day
Vulnerabilidade **desconhecida** que pode ser explorada **sem detecção ou prevenção**, por não corresponder a padrões ou assinaturas conhecidas.

## O objetivo da resposta à incidentes
Toda organização precisa estar preparada não só para evitar tais problemas, mas para agir caso aconteçam. Pois apesar de todo grande esforço realizado em segurança, prevenção, etc, todo sistema está vulnerável a riscos técnicos ou humanos.

A resposta a incidentes deve **priorizar sempre a vida, saúde e segurança**.  
Eventos são ocorrências comuns; quando podem impactar a missão do negócio, tornam-se **incidentes**.  

Toda organização precisa de um **plano de resposta a incidentes** para reduzir impactos e retomar operações rapidamente.  

Esse planejamento faz parte da **gestão de continuidade de negócios (BCM)** e foca na **preparação** para crises.

## Componentes de um plano de continuação de negócio
O **Business Continuity Plan (BCP)** é um planejamento **proativo** para restaurar as operações após desastres ou grandes interrupções. Embora seja principalmente um processo **de negócio**, a tecnologia deve estar alinhada para garantir **confidencialidade, integridade e disponibilidade** das informações.

**Componentes principais do BCP:**

- Lista da **equipe do BCP**, com contatos e substitutos.
- **Orientações à gestão**, incluindo autoridade e responsabilidades.
- Contatos críticos da **cadeia de suprimentos** (fornecedores, parceiros, emergências).
- Definição de **quando e como ativar o plano**.
- **Procedimentos imediatos** e checklists (segurança, incêndio, notificação de autoridades).
- **Sistemas de notificação** e árvores de chamada para alertar o pessoal.

Falhas são inevitáveis; por isso, profissionais de segurança também atuam como **primeiros respondedores**. Compreender **resposta a incidentes** começa pelo domínio dos termos e tipos de ataques.

## Exemplo de BCP em ação
Após um incêndio destruir o setor de faturamento, a empresa conseguiu manter as operações porque já havia feito uma **Business Impact Analysis (BIA)** e um **plano de continuidade**.  

O faturamento foi considerado importante, mas não crítico a curto prazo. Um **local alternativo** foi ativado em menos de uma semana, enquanto o **atendimento ao cliente** assumiu temporariamente as demandas.  

Com **planejamento prévio**, reservas financeiras e execução do plano, não houve impacto relevante no negócio — caracterizando **BCP bem-sucedido**.

---

## Componentes de um plano de respostas a incidentes
Uma política de resposta a incidentes é uma referência a um plano de respostas a incidentes que todos os funcionários vão seguir, dependendo do seus cargos no processo.

O plano deve conter vários procedimentos e padrões a serem seguidos em caso de incidente.

Deve ser levado em conta a visão, estratégia e missão da empresa para moldar tal documento, e o plano deve definir o que deve ser feito em relação a processos técnicos, checklists ou outras ferramentas que o time usará.

![[incident-response-plan.png]]

**1. Preparação**

- Desenvolver política de resposta a incidentes aprovada pela gestão.
- Identificar dados e sistemas críticos.
- Mapear pontos únicos de falha (SPOF).
- Definir e implementar um time de resposta a incidentes (IR Team).
- Definir papéis e responsabilidades.
- Treinar a equipe em resposta a incidentes.
- Planejar comunicação entre stakeholders.
- Considerar indisponibilidade do meio primário de comunicação.
- Padronizar a documentação de incidentes.

**2. Detecção e Análise**

- Praticar identificação do incidente (primeira resposta).
- Identificar e classificar o incidente.
- Identificar o atacante (quando possível).
- Monitorar todos os vetores de ataque potenciais.
- Analisar o incidente com base em dados conhecidos e threat intelligence.
- Priorizar incidentes conforme impacto e criticidade.
- Coletar e preservar evidências relevantes.

**3. Contenção, Erradicação e Recuperação**

- Escoher a estratégia de contenção apropriada.
- Isolar o ataque/sistemas comprometidos.
- Erradicar a causa raiz do incidente.
- Restaurar sistemas e serviços de forma segura.
- Monitorar o ambiente pós-recuperação.

**4. Pós-Incidente**

- Identificar evidências que devem ser retidas (legal/compliance).
- Documentar lições aprendidas.
- Realizar retrospectiva do incidente:
    - Preparação
    - Detecção e Análise
    - Contenção, Erradicação e Recuperação
    - Atividades Pós-Incidente

**Fluxo resumido:**  
Preparação → Detecção & Análise → Contenção, Erradicação & Recuperação → Pós-Incidente

## Disaster Recovery Planning (DRP)
**Disaster Recovery Planning (DRP)** entra em ação onde o Business Continuity (BC) deixa de atuar. Enquanto o BC foca em manter as funções críticas do negócio operando durante uma interrupção, o DRP tem como objetivo restaurar totalmente os ambientes de TI e comunicação após um desastre ou evento disruptivo.

Disaster Recovery refere-se especificamente à recuperação dos sistemas de informação e dos serviços de comunicação necessários para que a organização funcione, tanto durante o período de interrupção quanto no processo de retorno à normalidade. Embora uma função de negócio possa, em alguns casos, ser recuperada sem que a infraestrutura de TI esteja completamente restabelecida, na maioria dos cenários a recuperação de TI é essencial para sustentar e normalizar as operações do negócio.

O Disaster Recovery Plan (DRP) orienta as ações das equipes de resposta a emergências desde o momento em que ocorre a interrupção até que o objetivo final seja alcançado: restaurar a organização ao seu último estado conhecido confiável, com os serviços e sistemas operando plenamente.

Em síntese, **Business Continuity mantém o negócio funcionando durante a crise; Disaster Recovery restaura a TI para permitir o retorno completo das operações**.

## Componentes de um DRP
Pense no **DRP como um conjunto de documentos**, não como um arquivo único. A ideia é garantir que **cada pessoa envolvida na recuperação tenha exatamente a informação que precisa**, no nível certo de detalhe, no momento certo.

Para **gestão e liderança**, existe um **resumo executivo**. Ele explica, em alto nível, o que é o plano, quando ele é acionado e quais são os objetivos da recuperação. Serve para tomada de decisão e alinhamento estratégico, não para execução técnica.

Para **equipes técnicas (TI, infraestrutura, segurança)**, o DRP inclui **guias técnicos detalhados**. Aqui entram procedimentos práticos: restauração de backups, ativação de ambientes alternativos, ordem correta de subida de serviços e dependências críticas. É documentação feita para ser seguida sob pressão.

Para o **time crítico de disaster recovery**, há **cópias completas do plano acompanhadas de checklists**. Esses checklists são fundamentais em cenários reais, porque reduzem erro humano e evitam improviso quando o ambiente está caótico.

Para **gestores e comunicação (ex.: liderança e PR)**, o plano prevê documentos simples e objetivos. O foco é permitir comunicação clara e consistente sobre o incidente, sem interromper quem está executando a recuperação técnica.

Além disso, o DRP pode conter **planos específicos por departamento**, adaptando responsabilidades e ações conforme o impacto do desastre em cada área do negócio.

Na prática, disaster recovery começa muito antes do desastre acontecer. É essencial que a organização **identifique formalmente seus sistemas críticos** e mantenha **backups frequentes e testados**, porque nem todo incidente é detectado imediatamente. Em muitos casos reais, uma invasão ou falha só é percebida **semanas ou meses depois**, o que muda completamente a estratégia de recuperação.

Em ambientes simples, o DRP pode parecer apenas “restaurar um servidor a partir de backup”. Porém, em organizações reais — especialmente grandes empresas e hospitais — os sistemas são **interdependentes**. Dados inseridos em um sistema frequentemente são distribuídos para outros bancos de dados e aplicações. Isso significa que **não basta recuperar um servidor isolado**; é necessário entender o **fluxo de dados** e as **dependências entre sistemas** para que a restauração seja consistente e funcional.

O exemplo hospitalar ilustra bem isso. Sistemas diferentes (registro de pacientes, laboratório e radiologia) utilizavam **bases de dados separadas**, mas sincronizadas por rotinas automáticas. Um desastre nesse cenário exige que o DRP considere não apenas os backups individuais, mas também **a ordem correta de restauração e sincronização**, evitando inconsistências nos dados clínicos.

O caso mais crítico ocorre quando o backup em si está comprometido. Em um hospital, o último backup disponível continha **malware baseado em tempo**, que corromperia os dados assim que fosse restaurado. A solução foi voltar quase **um ano no tempo**, restaurar o sistema limpo e, só então, reintroduzir os dados de forma gradual para evitar reinfecção. Esse cenário deixa claro por que organizações precisam de **múltiplos níveis de backup** e **políticas de retenção longas**, alinhadas ao risco do negócio.

O dado de que um hospital em Los Angeles levou **260 dias para detectar a invasão** reforça o ponto central: **detecção tardia transforma recuperação em algo muito mais complexo e custoso**. Um DRP eficaz assume que o incidente pode ter começado muito antes de ser descoberto.