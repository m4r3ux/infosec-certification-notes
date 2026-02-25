## Networking

Uma rede é formada por dois ou mais computadores conectados para compartilhar dados, informações ou recursos.

### Tipos de rede

**LAN (Local Area Network)**  
Rede que cobre uma área geográfica limitada, como um prédio ou andar.

**WAN (Wide Area Network)**  
Conecta redes geograficamente distantes por meio de links de longa distância.

## Dispositivos de rede

### Hub
- Dispositivo cabeado.
- Conecta múltiplos dispositivos.
- Reenvia o tráfego para todos os dispositivos.
- Pouco utilizado em ambientes corporativos.

### Switch
- Dispositivo cabeado mais inteligente que o hub.
- Encaminha o tráfego apenas para a porta correta.
- Melhora eficiência e desempenho.
- Pode criar VLANs e domínios de broadcast separados.

### Router
- Controla o fluxo de tráfego entre redes.
- Conecta redes diferentes.
- Pode ser cabeado ou sem fio.
- Determina a rota mais eficiente para os dados.
- Mais inteligente que hubs e switches.

### Firewall
- Filtra o tráfego de rede com base em regras.
- Geralmente posicionado entre rede interna e internet.
- Pode segmentar redes internas.
- Utiliza listas de controle de acesso (ACLs).

## Padrão de rede

**Ethernet (IEEE 802.3)**  
Define o padrão de comunicação cabeada e o formato dos dados transmitidos, garantindo interoperabilidade entre dispositivos.

## Componentes da rede

### Servidor
- Fornece recursos para outros computadores.
- Exemplos:
  - Servidor web
  - Servidor de e-mail
  - Servidor de arquivos
  - Servidor de banco de dados
  - Servidor de impressão
- Normalmente possui segurança reforçada.

### Endpoint
- Dispositivo final da comunicação.
- Pode ser:
  - Desktop
  - Notebook
  - Tablet
  - Smartphone
  - Outro servidor

## Endereçamento de dispositivos

### Endereço MAC (Media Access Control)
- Identificador físico único da interface de rede.
- Exemplo: 00-13-02-1F-58-F5
- Os primeiros 24 bits identificam o fabricante.
- Não pode haver duplicidade na mesma rede local.

### Endereço IP (Internet Protocol)
- Endereço lógico associado ao dispositivo.
- Permite comunicação na rede.
- Pode permanecer o mesmo mesmo após troca de hardware.
- Exemplos:
  - 192.168.1.1 (IPv4)
  - 2001:db8::f:0:1 (IPv6)

## Conceito central

Para garantir comunicações seguras, é necessário compreender:

- Hardware
- Software
- Protocolos
- Endereçamento
- Criptografia
- Padrões de rede

Todos esses elementos trabalham em conjunto para permitir comunicação eficiente e segura.

---

## Networking at a Glance

O conteúdo apresenta a comparação entre uma rede de pequena empresa e uma rede doméstica típica.

## Rede de pequena empresa

Características principais:

- Dispositivos conectados por cabos.
- Componentes separados:
  - Router
  - Firewall
  - Switch
- O firewall fica posicionado entre a rede interna e a internet.
- Todos os dispositivos internos se conectam ao switch.
- Pode incluir:
  - Servidor
  - Workstations
  - Impressoras
  - Laptops
  - Telefones

Estrutura lógica:

Internet → Firewall → Switch → Dispositivos internos

Esse modelo oferece maior segmentação e controle de segurança.

## Rede doméstica típica

Principais diferenças:

- Router, firewall e switch geralmente estão combinados em um único dispositivo.
- Esse dispositivo costuma ser fornecido pelo provedor de internet.
- É representado como um Wireless Access Point.
- A maioria dos dispositivos se conecta via Wi-Fi.

Dispositivos comuns:

- Desktop
- Laptops
- Tablets
- Smartphones
- Impressora

Estrutura simplificada:

Internet → Wireless Access Point (router + firewall + switch) → Dispositivos

## Diferença principal

- Em ambientes empresariais, os componentes de rede normalmente são separados, permitindo maior controle e segurança.
- Em redes domésticas, as funções são consolidadas em um único equipamento para simplificar instalação e uso.

---

## Wi-Fi

### O que é Wi-Fi?

Wi-Fi é uma tecnologia de rede sem fio que permite conectar dispositivos à rede e à internet sem a necessidade de cabos físicos.

É amplamente utilizada em ambientes corporativos e residenciais devido a:

- Facilidade de implantação
- Custo relativamente baixo
- Flexibilidade de mobilidade

## Alcance e evolução

- O alcance do sinal geralmente é suficiente para casas e pequenos escritórios.
- Repetidores (range extenders) podem ampliar a cobertura em áreas maiores.
- O padrão Wi-Fi evoluiu ao longo do tempo, com versões cada vez mais rápidas e eficientes.

## Comparação: Rede Cabeada vs. Rede Sem Fio

### Rede Cabeada (LAN tradicional)

Para comprometer a rede, um atacante normalmente precisa:

- Acesso físico ao ambiente
- Instalar dispositivos de captura (sniffer taps)
- Conectar dispositivos USB maliciosos
- Interagir diretamente com cabos ou equipamentos

### Rede Sem Fio

- Não exige acesso físico direto à infraestrutura.
- Ataques podem ocorrer à distância, dentro do alcance do sinal.
- A superfície de ataque é maior em comparação com redes cabeadas.

## Vantagens do Wi-Fi

- Mobilidade
- Flexibilidade
- Dispositivos não ficam presos a cabos
- Permite roaming dentro da área de cobertura

## Riscos adicionais

A liberdade oferecida pela rede sem fio também traz vulnerabilidades adicionais, como:

- Interceptação de tráfego
- Acesso não autorizado
- Ataques de força bruta a redes mal configuradas
- Necessidade de criptografia forte e boas práticas de segurança

O Wi-Fi tornou o networking mais versátil, mas exige atenção redobrada à segurança.

---

## Microsegmentation

A microsegmentação é uma estratégia de segurança que aplica controles granulares dentro do ambiente de TI, limitando a comunicação entre sistemas para reduzir a superfície de ataque.

Ataques modernos utilizam técnicas avançadas e polimórficas que conseguem contornar controles estáticos tradicionais e se mover lateralmente dentro de data centers. A microsegmentação ajuda a impedir esse movimento lateral.

## Objetivo principal

- Controlar o tráfego interno do data center.
- Controlar o tráfego de entrada e saída da internet.
- Reduzir a possibilidade de comprometimento amplo do ambiente.

## Características da Microsegmentação

### Controle granular

Permite aplicar regras detalhadas para:

- Máquinas individuais
- Usuários específicos
- Endereços IP autorizados
- Horários específicos
- Credenciais utilizadas
- Serviços permitidos

### Regras lógicas

- Baseia-se em regras lógicas, não físicas.
- Não exige novo hardware.
- Não requer intervenção física nos dispositivos.
- Pode ser aplicada remotamente pelo administrador.

### Defesa em profundidade

- Representa o estado mais avançado da filosofia defense-in-depth.
- Um único ponto comprometido não deve permitir acesso ao restante do ambiente.

### Importância em ambientes compartilhados

Fundamental em ambientes como:

- Cloud computing
- Infraestruturas multi-tenant

Ajuda a proteger dados mesmo quando:

- Diferentes clientes compartilham o mesmo hardware.
- Administradores do provedor têm acesso físico aos equipamentos.

### Aplicação do princípio do menor privilégio

Permite restringir a comunicação entre:

- Departamentos
- Unidades de negócio
- Escritórios

Exemplo:
O setor de Recursos Humanos pode ser isolado para proteger dados sensíveis como:

- Endereço residencial
- Salário
- Informações médicas

Semelhante ao conceito de VLAN, cria enclaves isolados dentro da infraestrutura.

### Tecnologias associadas

Disponível graças a:

- Virtualização
- Software-Defined Networking (SDN)

Na nuvem, pode ser implementada por meio de:

- Security Groups
- VPNs (dependendo da arquitetura)

### Uso doméstico

Mesmo em casa, pode ser utilizada para:

- Separar computadores pessoais
- Isolar smart TVs
- Isolar dispositivos IoT
- Reduzir riscos provenientes de dispositivos vulneráveis

## Benefício central

A microsegmentação reduz drasticamente a movimentação lateral de um invasor, limitando o impacto de um comprometimento inicial.

![[tools.png]]

---

## Intrusion Detection System (IDS)

Sistema que monitora logs e eventos em tempo real para identificar atividades suspeitas ou tentativas de invasão.

Faz parte da estratégia de defesa em profundidade. Complementa o firewall, mas não o substitui.

## Objetivos

- Detectar tentativas de intrusão  
- Identificar falhas e anomalias  
- Gerar alertas para resposta rápida  

## Tipos de IDS

### HIDS (Host-Based IDS)

Monitora um único host.

Monitora:
- Processos
- Logs do sistema e aplicações
- Logs de segurança

Vantagens:
- Análise detalhada
- Detecta alterações em arquivos e processos

Desvantagens:
- Gestão individual por máquina
- Não monitora outros sistemas da rede

### NIDS (Network-Based IDS)

Monitora o tráfego da rede.

Características:
- Analisa padrões de pacotes
- Usa sensores distribuídos
- Administração centralizada

Limitações:
- Não inspeciona conteúdo criptografado
- Não confirma se o ataque foi bem-sucedido

## SIEM

Ferramenta que centraliza e correlaciona logs de múltiplas fontes para melhorar a detecção e resposta a incidentes.

---
