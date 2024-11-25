# PF - Cybersegurança

### Diagrama de arquitetura

![DIAGRAMA_PF_CYBER drawio (3)](https://github.com/user-attachments/assets/bc5615ce-c6fa-4225-9ad1-775304c7bb4d)

Dentro da VPC, criamos duas sub-redes para segmentar os recursos e melhorar a segurança da infraestrutura:

**Sub-rede pública (10.0.1.0/24)**:

- Essa sub-rede é acessível pela internet por meio de um Internet Gateway, contendo os serviços que precisam de comunicação externa ou interação direta com usuários e sistemas externos

- **Jump Server**: ponto de acesso seguro para gerenciar e interagir com os recursos dentro do ambiente, atuando como um "intermediário" para proteger o acesso direto às instâncias.
- **Zabbix**: ferramenta de monitoramento da infraestrutura, responsável por coletar métricas e garantir que o ambiente esteja funcionando corretamente.
- **Wazuh**: solução de monitoramento de segurança e detecção de intrusão, protegendo o ambiente contra ameaças.
- **FastAPI**: serviço de backend contendo uma API para ser utilizada.

**Sub-rede privada (10.0.2.0/24)**:

- Essa sub-rede é isolada da internet para proteger os dados sensíveis. Apenas os recursos internos têm acesso a ela, por meio de regras específicas

- **Banco de Dados**: responsável pelo armazenamento seguro das informações (por isso está na sub-rede privada, a fim de não estar diretamente exposto à internet).
- **NAT Gateway**: permite que os recursos privados realizem tarefas que exigem acesso à internet sem comprometer a segurança da sub-rede privada

### Cloudflare

A plataforma Cloudflare foi utilizada como uma ferramenta robusta para performance, segurança e estabilidade dos serviços online. Os servidores Cloudflare atuam como intermediários entre os visitantes de um site e o servidor de origem, respondendo às solicitações DNS, entregando conteúdo em cache e filtrando tráfego malicioso.

![image](https://github.com/user-attachments/assets/85423b15-48f4-46d7-b25e-0ca060bb8a05)


Sobre o DNS foram registrados os serviços:

|Serviço|Subdomínio|
|-----|-----|
|FastApi|api|
|Zabbix|sec|
|Wazuh|dash|

### Serviços em funcionamento
#### Zabbix

![image](https://github.com/user-attachments/assets/1b3b85e9-8f5e-4ebe-a9fa-0f700ab0a8e5)

#### Wazuh

![image](https://github.com/user-attachments/assets/8c9cab28-de04-4292-8be3-a9d32c2a1b37)

Obs.: Ao entrar no IP relacionado ao serviço do Wazuh, é mostrado que não é um site seguro, mesmo realizando as mudanças de certificado SSL.

![image](https://github.com/user-attachments/assets/e7dfbca2-77c8-4d82-b9d8-c4a620e6a018)

Tutorial que seguimos: https://documentation.wazuh.com/current/user-manual/wazuh-dashboard/configuring-third-party-certs/ssl.html


#### FastAPI

![image](https://github.com/user-attachments/assets/32575907-5a6b-4e43-bbaa-9c3cbb1fabb1)

#### PRITUNL (VPN)

Recursos Implentados: 
- Autenticação por dois fatores via Google Autenticatior
- Server VPN Admin com acesso completo a todas as máquinas: 10.0.0.0/16
- Server VPN Database com acesso restrito apenas para a Subnet 10.0.2.0/32
- Log de autenticação dos usuários à VPN

![image](https://github.com/user-attachments/assets/887442f5-2592-4901-a905-1f62a358e0b4)

Teste de Segurança de acesso SSH

Acesso negado para acesso via IP público:
![image](https://github.com/user-attachments/assets/5b1e3889-057c-4545-8a76-8d966de4c436)

Acesso para usuário conectado na vpn:
![image](https://github.com/user-attachments/assets/4126c9b6-e085-4f95-a3af-d3ed706ac4e2)




### Vídeo demonstrativo do ambiente em funcionamento

https://1drv.ms/v/c/80ee50809c367d42/EaCD1dK_MkBGh8U8xr76KZABE0INkUO70_jU87wxK8nyYA?e=tgHaiY

---








**Grupo 4**:

Alexandre Magno, João Alfredo, Leonardo Scarlato
