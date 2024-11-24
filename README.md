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

### Vídeo demonstrativo do ambiente em funcionamento


---








**Grupo 4**:

Alexandre Magno, João Alfredo, Leonardo Scarlato
