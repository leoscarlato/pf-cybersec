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

![image](https://github.com/user-attachments/assets/887442f5-2592-4901-a905-1f62a358e0b4)


### Vídeo demonstrativo do ambiente em funcionamento


---








**Grupo 4**:

Alexandre Magno, João Alfredo, Leonardo Scarlato
