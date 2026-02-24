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