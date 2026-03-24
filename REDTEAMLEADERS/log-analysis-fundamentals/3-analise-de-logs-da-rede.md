# Firewall logs e monitoramento de perímetro

Firewalls são o ponto mais externo de visibilidade da rede. Antes mesmo de um ataque chegar no sistema operacional ou gerar logs de autenticação, ele já passa pelo firewall. Por isso, esses logs costumam ser o primeiro indício de atividade maliciosa.

Enquanto logs de host (Linux/Windows) mostram o que aconteceu *dentro* da máquina, logs de firewall mostram *quem tentou chegar até ela* — e isso muda completamente a perspectiva de análise.

Pensamento chave:
firewall = tentativa de acesso  
host = execução real  



# O que realmente aparece nos logs

Um log de firewall, na prática, descreve uma tentativa de comunicação entre dois pontos.

Ele sempre responde perguntas essenciais:
- quem tentou (IP de origem)
- para onde (IP de destino)
- como (protocolo/porta)
- o que aconteceu (allow ou deny)

Exemplo clássico:
tentativa de conexão TCP na porta 22 com flag SYN

Isso, isoladamente, já indica início de conexão — e possivelmente tentativa de acesso SSH.



# Mais importante que o log: o padrão

Assim como em autenticação, um evento isolado raramente diz algo relevante.

O valor está no comportamento:

- muitas conexões negadas → possível scan
- várias portas diferentes → enumeração
- padrão repetitivo → automação (ferramenta)

Exemplo típico:
um único IP tentando dezenas de portas em poucos segundos  
→ port scanning

Outro padrão:
vários IPs tentando a mesma porta  
→ ataque distribuído (botnet)



# Entrada, saída e lateral

Logs de firewall não são só sobre ataques externos.

Eles mostram três direções importantes:

Entrada (inbound):
- internet → rede interna  
- foco: tentativas de invasão

Saída (outbound):
- host interno → internet  
- foco: malware, C2, exfiltração

Lateral (east-west):
- comunicação entre máquinas internas  
- foco: movimento lateral

Isso é crítico.

Exemplo:
um endpoint comprometido pode parecer normal no host  
mas no firewall ele começa a:
- tentar conexões externas estranhas
- usar portas incomuns
- comunicar com IPs maliciosos

Ou seja:
firewall revela comportamento que o endpoint esconde



# Correlação com outros logs

Aqui é onde firewall ganha valor real.

Exemplo prático:

Firewall:
- IP externo tentando acessar porta 22

Linux:
- várias falhas de SSH

→ confirmação de brute force

Outro:

Firewall:
- host interno conectando em IP suspeito

Endpoint:
- execução de powershell ou malware

→ possível C2 ativo

Firewall sozinho levanta suspeita  
correlação confirma ataque  



# Casos clássicos de detecção

Port scanning:
muitas conexões negadas para várias portas  
→ reconhecimento inicial

Acesso não autorizado:
tentativa de acessar serviços internos  
(ex: RDP, SSH, SMB)

Movimento lateral:
máquinas internas se comunicando fora do padrão  
(ex: workstation acessando servidor via SMB sem motivo)

Beaconing (malware):
conexões periódicas para o mesmo IP externo  
→ padrão de C2

Exfiltração:
grande volume de tráfego de saída  
ou uso de portas incomuns



# O papel do "deny"

Muita gente ignora logs bloqueados — erro crítico.

Logs de deny são:
- tentativas de ataque
- reconhecimento
- atividade que *não deveria existir*

Na prática:
deny mostra o atacante tentando  
allow pode mostrar ele conseguindo  

Ambos são importantes, mas deny revela intenção.



# Enriquecimento: transformando log em contexto

Um IP sozinho não diz muito.

Mas quando você adiciona contexto:
- país (GeoIP)
- reputação (threat intel)
- tipo de serviço (porta)

o mesmo log ganha significado.

Exemplo:
IP tentando SSH vindo de outro país + listado em blacklist  
→ risco muito maior

Isso é o que SIEM faz bem:
transformar dados em contexto acionável



# SIEM e deteccao

No SIEM, logs de firewall viram campos como:
- source.ip
- destination.ip
- destination.port
- action

Isso permite criar regras como:

muitos bloqueios do mesmo IP  
ou  
conexões para portas críticas (22, 3389, 445)

E o mais importante:
correlacionar com logs de autenticação e endpoint



# Pensamento operacional

Firewall mostra o início da história.

Ele responde:
"quem está tentando entrar ou sair?"

Mas não responde sozinho:
"o ataque funcionou?"

Por isso:
firewall + endpoint + autenticação = visão completa



# Resumo mental

Firewall = perímetro e visibilidade inicial  

Muitas conexões → scan  
Muitas portas → enumeração  
Saída suspeita → possível malware  
Tráfego interno estranho → movimento lateral  

Logs bloqueados mostram tentativa  
Logs permitidos podem mostrar sucesso  

Firewall não confirma ataque sozinho  
mas quase sempre mostra onde ele começou


---

# IDS/IPS logs e deteccao de ameacas em rede

Diferente do firewall, que decide se o trafego passa ou nao, IDS/IPS analisa *o que existe dentro do trafego*. Ele nao olha so IP e porta — ele olha comportamento, padrao e conteudo.

Isso muda o nivel de visibilidade.

Pensamento chave:
firewall controla acesso  
IDS/IPS entende intencao  



# IDS vs IPS na pratica

A diferenca entre os dois nao e tecnica, e operacional.

IDS observa e alerta.  
IPS observa e interfere.

Isso significa:

- IDS e ideal para visibilidade e investigacao
- IPS e ideal para bloqueio em tempo real

Mas IPS tem risco:
um falso positivo pode derrubar trafego legitimo

Por isso, em ambientes maduros:
IDS ajuda a entender  
IPS entra depois, quando ha confianca nas deteccoes  



# O que um alerta realmente mostra

Um log de IDS/IPS nao e apenas um evento de rede — ele e uma interpretacao.

Ele ja vem com contexto:
- qual regra disparou (signature_id)
- o que foi detectado (signature)
- classificacao (ex: exploit, scan, malware)
- severidade

Ou seja:
ele ja tenta responder "isso parece ataque?"

Exemplo mental:

firewall:
conexao porta 80

IDS:
possivel scan Nmap usando User-Agent suspeito

Isso reduz muito o tempo de analise.



# Assinatura = conhecimento encapsulado

Cada alerta vem de uma regra.

Essa regra representa:
- comportamento conhecido
- tecnica de ataque
- padrao de malware

Exemplo:
"ET SCAN Nmap Scripting Engine"

Isso nao e so texto — e inteligencia embutida.

O analista nao precisa identificar manualmente  
o IDS ja fez essa primeira camada



# Suricata e o salto para SIEM

Ferramentas modernas como Suricata usam JSON.

Isso muda tudo:

- campos estruturados (src_ip, dest_ip, severity)
- facil ingestao em SIEM
- correlacao direta com outros logs

Comparando:

Snort (texto) → leitura humana  
Suricata JSON → analise automatizada  

Para Blue Team moderno, isso e essencial.



# Tipos de comportamento detectados

IDS/IPS cobre fases inteiras do ataque.

Reconhecimento:
- scans (Nmap, masscan)
- probes estranhos
- user-agents anormais

Exploit:
- tentativas de vulnerabilidade (ex: Log4j)
- shellcode
- payloads maliciosos

Malware / C2:
- beaconing (conexoes periodicas)
- padroes conhecidos de familias (Emotet, TrickBot)

Exfiltracao:
- volume alto de dados
- protocolos usados de forma anormal

Movimento lateral:
- uso interno de SMB, RDP, PsExec fora do padrao

Ou seja:
IDS nao mostra so tentativa de acesso  
mostra comportamento de ataque em andamento  



# Correlacao com outras camadas

Aqui IDS brilha de verdade.

Exemplo completo:

Firewall:
conexao permitida para web server

IDS:
alerta de exploit (ex: Log4j)

Endpoint:
processo suspeito iniciado

→ ataque confirmado

Sem IDS:
firewall diria que foi trafego normal

Outro exemplo:

IDS:
beaconing detectado

Firewall:
conexoes repetidas para mesmo IP

→ possivel C2 ativo

IDS adiciona contexto ao trafego bruto  



# Signature ID como pivô

Cada alerta tem um ID de assinatura.

Isso permite:
- agrupar eventos iguais
- mapear para MITRE ATT&CK
- entender tipo de ataque rapidamente

Analista experiente nao le tudo  
ele pivota pelo signature_id

Isso acelera triagem absurdamente.



# Escrita de regras: deteccao sob medida

Ambientes reais nao dependem so de regras prontas.

Voce pode criar deteccoes especificas:

ex:
detectar user-agent do Nmap  
detectar padrao de DNS exfiltration  

Isso transforma IDS em algo adaptado ao seu ambiente.

Mas tem risco:
quanto mais regras → mais ruido

Por isso entra tuning.



# Ruido e falso positivo

IDS pode gerar MUITOS alertas.

Sem ajuste, vira inutil.

Problemas comuns:
- regras genericas demais
- ambiente nao considerado
- trafego legitimo parecendo ataque

Solucoes:
- suprimir regras irrelevantes
- usar threshold (limite de alertas)
- ajustar com base no comportamento real da rede

Pensamento importante:
IDS sem tuning = alerta inutil  
IDS ajustado = sensor de alta precisao  



# Correlacao temporal

Assim como logs de autenticacao, tempo importa.

Exemplo:

IDS:
alerta de exploit

segundos depois:
endpoint executa processo

→ forte indicio de sucesso do ataque

Se o tempo nao bate:
pode ser falso positivo ou tentativa falha

Por isso:
timestamp alinhado e essencial (NTP novamente)



# Pensamento operacional

IDS/IPS nao substitui firewall nem endpoint.

Ele conecta os dois.

Firewall diz:
"alguem tentou"

Endpoint diz:
"algo rodou"

IDS diz:
"isso parece um ataque conhecido"

Juntos:
formam uma narrativa completa



# Resumo mental

Firewall = controle de acesso  
IDS = interpretacao do trafego  

Assinatura = conhecimento de ataque  
Alerta = suspeita contextualizada  

Scan → reconhecimento  
Exploit → tentativa real  
Beacon → persistencia / C2  

IDS sozinho alerta  
correlacao confirma ataque  

Sem tuning = ruido  
Com tuning = deteccao poderosa


---

# DNS logs e deteccao de comportamento oculto

DNS e um dos pontos mais subestimados em analise de seguranca — mas, na pratica, quase tudo passa por ele primeiro.

Antes de qualquer conexao HTTP, malware ou C2, existe uma consulta DNS.

Pensamento chave:
DNS nao mostra ataque direto  
mostra a intencao antes do ataque  



# DNS como ponto inicial da comunicacao

Quando um host quer se comunicar, ele resolve um dominio.

Isso significa que logs DNS respondem:
- o que o host quer acessar
- quando tentou
- com que frequencia

Diferente de firewall:
que mostra conexao

DNS mostra *interesse*

Exemplo:
host consulta dominio malicioso  
mesmo que conexao nao aconteca  
isso ja e um sinal forte  



# O que realmente importa no log DNS

Um log DNS simples ja traz muito contexto:

- query (dominio)
- IP de origem
- tipo (A, AAAA, TXT)
- resposta (NOERROR, NXDOMAIN)

Mas o valor real nao esta no campo isolado  
esta no padrao de uso



# Comportamento vs evento

Um dominio estranho sozinho nao significa muito.

Mas quando voce ve:

- muitas consultas para o mesmo dominio
- consultas em intervalos regulares
- nomes estranhos ou aleatorios

isso muda o jogo

Exemplo:
consultas a cada 10 segundos para mesmo dominio  
→ forte indicio de beaconing (C2)

Outro:
varios subdominios longos e diferentes  
→ possivel exfiltracao via DNS



# DNS como canal de ataque

Atacantes usam DNS porque ele quase sempre e permitido.

Isso permite tecnicas como:

C2 disfarcado:
malware consulta dominio para receber instrucoes

DNS tunneling:
dados sao enviados dentro do nome do dominio

Exfiltracao:
informacoes sensiveis codificadas em queries

Ou seja:
DNS vira canal de comunicacao invisivel



# Padroes tipicos de ameaca

Alguns comportamentos sao praticamente assinatura de ataque.

Dominios aleatorios:
strings longas sem sentido  
→ possivel DGA (malware gerando dominios)

Alta frequencia:
mesmo dominio repetidamente  
→ beaconing

Subdominios exagerados:
abc123.xyz.c2domain.com  
→ tunelamento

Consultas TXT incomuns:
→ transporte de dados

NXDOMAIN em massa:
→ tentativa de encontrar dominio valido (DGA ativo)



# Correlacao com outras fontes

DNS sozinho levanta suspeita  
correlacao confirma

Exemplo:

DNS:
consulta dominio suspeito

Firewall:
conexao para IP resolvido

Endpoint:
processo desconhecido executando

→ cadeia completa de ataque

Outro:

DNS:
dominio recem-criado

Threat intel:
dominio malicioso conhecido

→ alerta imediato

DNS e muitas vezes o primeiro sinal  
antes de qualquer outra evidência  



# Dominios novos e reputacao

Um dos sinais mais fortes e idade do dominio.

Dominios recem-criados:
- muito usados em phishing
- usados em campanhas de malware

Se um host acessa dominio criado ontem  
isso e altamente suspeito

Aqui entra enriquecimento:
WHOIS + threat intel + passive DNS



# DNS e horario (contexto comportamental)

Horario tambem importa.

Exemplo:
workstation fazendo consultas DNS de madrugada  
→ comportamento anormal

Ou:
pico de consultas fora do padrao  
→ possivel atividade automatizada

DNS ajuda a identificar comportamento fora do perfil normal  



# DNS em endpoint vs rede

DNS pode ser visto em varios lugares:

Resolver:
mostra consultas gerais da rede

Zeek/Suricata:
mostra trafego observado

Endpoint (Sysmon):
mostra qual processo fez a consulta

Esse ultimo e poderoso:

processo + dominio = contexto completo

Exemplo:
powershell.exe fazendo query para dominio suspeito  
→ muito mais forte que apenas o dominio



# SIEM e deteccao

No SIEM, DNS vira dados estruturados:

- dns.query
- source.ip
- response.code

Isso permite detectar:

consultas repetidas  
dominios raros  
dominios suspeitos (.xyz, .top, etc)

E principalmente:
correlacionar com IP, usuario e processo



# Pensamento operacional

DNS nao mostra "exploit"  
mas mostra preparacao e comunicacao

Ele responde:
"o que esse host esta tentando resolver?"

E isso, muitas vezes, revela:
- malware ativo
- tentativa de contato com C2
- exfiltracao silenciosa

Por isso:
DNS e uma das melhores fontes para threat hunting  



# Resumo mental

DNS = intencao antes da conexao  

Consulta estranha = possivel indicio  
Repeticao = comportamento automatizado  
Dominio aleatorio = possivel malware  
Subdominio longo = exfiltracao  

DNS sozinho nao prova ataque  
mas quase sempre aponta onde olhar  

Quem controla e analisa DNS  
ganha visibilidade antes do ataque acontecer


---

# Proxy logs e visibilidade de trafego web

Se o DNS mostra *intencao* e o firewall mostra *conexao*, o proxy mostra *o que realmente foi acessado*.

Ele e o ponto mais detalhado da navegacao web.

Pensamento chave:
DNS resolve  
firewall conecta  
proxy revela conteudo  



# O papel do proxy na seguranca

O proxy fica entre o usuario e a internet.

Isso permite:
- aplicar politicas (bloquear/acessar)
- registrar tudo que foi acessado
- categorizar comportamento

Diferente de outras fontes, aqui voce ve:
- URL completa
- metodo HTTP
- resposta do servidor
- volume de dados

Ou seja:
proxy mostra a *acao real do usuario ou malware*  



# O que realmente importa no log

Um log de proxy e rico, mas o valor esta em correlacionar campos.

Exemplo mental:

IP interno + POST + dominio suspeito + resposta 200  
→ possivel envio de dados para C2

Campos chave nao devem ser vistos isoladamente:
- metodo (GET vs POST)
- URL (path e endpoint)
- status HTTP
- bytes transferidos
- user-agent

Tudo junto forma o comportamento  



# GET vs POST (diferenca critica)

GET geralmente representa acesso:
abrir pagina, baixar conteudo

POST geralmente representa envio:
dados, credenciais, arquivos

Isso e essencial.

Exemplo:
GET em dominio estranho → suspeito  
POST em dominio estranho → muito mais grave  

POST + dominio malicioso = possivel exfiltracao ou C2  



# Proxy como detector de C2

Malware moderno frequentemente usa HTTP/HTTPS.

Isso faz o trafego parecer legitimo.

Mas o proxy revela padrao:

- endpoints como /checkin, /gate.php, /api
- conexoes frequentes e regulares
- user-agent estranho ou falso

Exemplo:
host fazendo POST recorrente para /checkin.php  
→ comportamento tipico de beaconing

Mesmo que o firewall permita  
o proxy expoe o padrao  



# User-Agent como indicador

User-Agent deveria representar navegador.

Mas malware frequentemente:
- usa strings falsas
- nao usa padrao de browser
- ou usa ferramentas (curl, python, etc)

Exemplo:
user-agent vazio ou incomum  
→ forte indicio de script ou malware

Outro caso:
user-agent "Mozilla" mas comportamento nao bate  
→ possivel spoofing  



# Categoria e contexto

Ferramentas de proxy categorizam dominios:
- malware
- phishing
- C2
- social media

Isso ajuda muito na triagem.

Exemplo:
acesso permitido a categoria "Command and Control"  
→ falha de politica + incidente potencial

Mas cuidado:
categoria ajuda, mas nao substitui analise  
dominio novo pode nao estar categorizado ainda  



# Exfiltracao via web

Proxy e uma das melhores formas de detectar exfiltracao.

Padroes comuns:
- uploads grandes (POST/PUT)
- envio para cloud (Dropbox, Mega, etc)
- volume alto de dados para destino incomum

Exemplo:
host enviando 50MB via POST para dominio desconhecido  
→ altamente suspeito

Aqui os campos de bytes fazem diferenca  



# Beaconing e comportamento repetitivo

Assim como DNS, repeticao e chave.

Exemplo:
mesmo host acessando mesma URL a cada X segundos  
→ padrao de malware

Proxy permite ver isso claramente:
mesma URL + mesmo intervalo + mesmo metodo

Isso dificilmente e comportamento humano  



# Correlacao com outras fontes

Proxy fecha o ciclo.

Exemplo completo:

DNS:
resolve dominio suspeito

Firewall:
permite conexao

Proxy:
mostra POST para /checkin

Endpoint:
processo desconhecido ativo

→ ataque confirmado com alta confianca

Sem proxy:
voce nao veria o endpoint da requisicao  



# Tunelamento e evasao

Proxy tambem ajuda a detectar bypass.

Exemplo:
uso de CONNECT para tunel HTTPS
trafego criptografado vindo de agente estranho

Ou:
uso de proxies externos / VPN / Tor

Isso pode indicar:
- tentativa de anonimato
- evasao de controle corporativo  



# Hunting com proxy

Proxy e excelente para threat hunting.

Algumas abordagens:

- dominios raros ou novos
- user-agents nao padrao
- POST para URLs suspeitas
- comportamento repetitivo (beaconing)
- uploads grandes inesperados

Aqui o foco nao e alerta  
e encontrar comportamento fora do normal  



# Pensamento operacional

Proxy responde uma pergunta essencial:

"o que exatamente esse host fez na web?"

Nao so onde conectou  
mas:
- qual URL
- qual metodo
- quanto dado
- qual resposta

Isso transforma suspeita em evidencia  



# Resumo mental

Proxy = visibilidade completa da web  

GET = acesso  
POST = envio (mais critico)  

URL estranha + POST = alerta forte  
Repeticao = beaconing  
Upload grande = exfiltracao  

User-agent estranho = possivel malware  

Proxy nao substitui DNS/firewall  
mas e onde o comportamento fica claro

---

# Logs de Autenticacao e Acesso

Logs de autenticacao e acesso sao o coracao da visibilidade em seguranca. Eles mostram quem entrou, de onde, como e com qual nivel de privilegio. Na pratica, isso cobre desde tentativa de acesso ate movimento lateral e abuso de conta.

O ponto mais importante aqui nao e o log isolado, mas a identidade sendo usada ao longo do ambiente.

Esses logs aparecem em varios lugares ao mesmo tempo: Windows (Security.evtx), Linux (auth.log), Active Directory, VPNs, SSO (Azure AD, Okta) e ate aplicacoes web. O analista precisa enxergar tudo isso como uma unica linha do tempo de identidade.



# O que realmente importa no log

Todo log de autenticacao gira em torno de alguns campos-chave:

- usuario (quem)
- IP de origem (de onde)
- sistema alvo (para onde)
- tipo de autenticacao (como)
- resultado (sucesso ou falha)

Esses campos permitem responder perguntas criticas:

- esse usuario costuma acessar daqui?
- esse IP faz sentido?
- esse tipo de logon e esperado?
- esse comportamento e normal?

Sem isso, nao existe deteccao — apenas registro.



# Falha vs sucesso (o inicio da historia)

Tentativas de login falhadas mostram ataque em andamento. Logins bem-sucedidos mostram risco real.

Mas o que importa e a relacao entre eles.

Padrao classico:
- varias falhas (4625 ou Failed password)
- seguido de sucesso (4624 ou Accepted password)

Isso indica:
- brute force bem-sucedido
- credential stuffing
- credencial vazada sendo usada

Outro padrao importante:
- falhas vindo de varios IPs contra um unico usuario
→ tentativa automatizada de adivinhar senha

Aqui o raciocinio muda:
falha isolada = ruido  
falha repetida + padrao = ataque  



# Tipo de logon e contexto

Nem todo login e igual.

No Windows, o tipo de logon muda completamente o significado:

- tipo 2 → login local
- tipo 3 → rede (SMB, compartilhamento)
- tipo 10 → RDP (remoto)

Exemplo:
usuario fazendo logon tipo 10 de madrugada
→ acesso remoto fora do padrao

Ou:
conta de servico usando logon interativo (tipo 2)
→ comportamento anormal

O contexto do logon e tao importante quanto o evento em si.



# Movimento lateral (quando o ataque se espalha)

Depois que o atacante entra, ele raramente fica parado.

Ele tenta acessar outros sistemas.

Isso aparece como:
- mesmo usuario logando em varios hosts
- varios logons tipo 3 ou 10 em sequencia
- uso de credenciais explicitas (Event ID 4648)

Padrao suspeito:
um usuario acessa 3, 4, 5 maquinas em poucos minutos

Isso dificilmente e comportamento humano normal  
→ forte indicio de movimento lateral



# Escalada de privilegio via autenticacao

Autenticacao nao e so login — tambem revela aumento de privilegio.

Exemplo no Windows:
- 4624 (login)
- seguido de 4672 (privilegios especiais)

Isso mostra que a sessao ganhou privilegios administrativos.

No Linux:
- login SSH
- seguido de uso de sudo

Padrao perigoso:
usuario comum → acesso → privilegio elevado

Isso indica pos-exploracao ativa.



# Padroes anormais de acesso

Blue Team nao procura apenas ataque direto, mas comportamento estranho.

Alguns exemplos fortes:

- login fora do horario (madrugada, fim de semana)
- login de pais diferente (GeoIP)
- login em sistema nunca acessado antes
- MFA falhando repetidamente
- conta desativada tentando autenticar

Outro caso importante:
"impossible travel"

usuario loga no Brasil  
minutos depois loga na Europa  

→ impossivel fisicamente  
→ credencial comprometida



# Contas sensiveis e alvo prioritario

Nem todas as contas tem o mesmo peso.

Contas como:
- admin / administrator
- root
- contas de servico

devem ser monitoradas com mais rigor.

Padroes suspeitos:

- login direto como admin
- uso frequente de contas privilegiadas
- criacao de novas contas (4720)
- adicionando usuario em grupo admin (4732)

Aqui o risco e alto mesmo com poucos eventos.



# Correlacao e visao unificada

Logs de autenticacao fazem sentido quando conectados:

entrada → acesso → privilegio → movimento

Exemplo completo de ataque:

- 4625 (falhas)
- 4624 (sucesso)
- 4672 (privilegios)
- 4688 (execucao de comando)
- multiplos logons em outros hosts

Separados, parecem eventos comuns  
juntos, contam uma invasao completa



# SIEM e deteccao baseada em identidade

Quando esses logs vao para SIEM, viram dados estruturados:

- user.name
- source.ip
- event.outcome
- logon.type

Isso permite deteccoes como:

- muitas falhas por usuario
- login de IP externo
- acesso fora do horario
- mesmo usuario em varios hosts

Sem normalizacao, nao existe correlacao real.



# Threat hunting focado em autenticacao

Algumas abordagens praticas:

Brute force:
muitas falhas em pouco tempo

Credential stuffing:
varios IPs tentando mesma conta

Movimento lateral:
mesmo usuario em varios hosts

Escalada:
login seguido de privilegio elevado

Conta comprometida:
login fora de padrao + sucesso

O diferencial aqui e buscar comportamento, nao alerta pronto.



# Pensamento operacional

Autenticacao conta a historia da identidade no ambiente:

tentativa → validacao → acesso → privilegio → expansao

O atacante precisa passar por essas etapas  
e cada uma deixa rastro

O papel do analista e conectar esses rastros.



# Resumo mental

Autenticacao = identidade em acao  

Falhas repetidas = ataque em andamento  
Sucesso apos falha = possivel comprometimento  
Logon remoto inesperado = risco alto  
Multiplos hosts = movimento lateral  
Privilegio apos login = escalada  

Logs de autenticacao nao mostram tudo  
mas mostram quem esta controlando o ambientet