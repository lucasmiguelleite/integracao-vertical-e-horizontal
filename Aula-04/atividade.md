# Análise de Aplicação de Sistema Digital de Controle Distribuído (SDCD)

**Contexto da Aplicação:** O sistema analisado visa monitorar e gerenciar um processo contínuo com base na seguinte arquitetura tecnológica proposta: Sensor de Temperatura $\rightarrow$ ESP32 $\rightarrow$ MQTT $\rightarrow$ Servidor $\rightarrow$ Aplicativo Mobile $\rightarrow$ Dashboard $\rightarrow$ Gestão da Fábrica.

---

### 1. Papel de cada componente do sistema

- **Sensor de Temperatura:** Atua no nível de campo. Sua função é monitorar a grandeza física (temperatura) do ambiente ou equipamento industrial e coletar essas informações brutas para o sistema.
- **ESP32 (Controlador Distribuído):** Atua como o controlador inteligente localizado próximo ao processo controlado. Ele recebe os sinais analógicos/digitais do sensor de temperatura, realiza o processamento local das informações e atua como gateway de conectividade.
- **Protocolo MQTT:** Representa a camada de comunicação digital do sistema. É o protocolo de rede responsável por empacotar e transmitir os dados lidos pelo ESP32 de maneira leve, rápida e confiável até o servidor central.
- **Servidor:** Atua como o núcleo de recepção, armazenamento e roteamento das informações recebidas dos controladores na rede de alta velocidade.
- **Aplicativo Mobile e Dashboard (Nível de Supervisão):** Operam como a Interface Homem-Máquina (IHM) e sistema SCADA (Supervisory Control and Data Acquisition) na sala de controle ou dispositivo remoto. Eles traduzem os dados armazenados no servidor em gráficos, indicadores e alertas visuais compreensíveis.

### 2. Fluxo de dados no sistema

O fluxo de dados ocorre de maneira estruturada, partindo do nível de campo até o nível de supervisão:

1. **Coleta:** O sensor captura as variações térmicas do ambiente físico de forma ininterrupta.
2. **Processamento Local e Publicação:** O ESP32 lê esses dados elétricos, converte em valores digitais compreensíveis (por exemplo, graus Celsius) e utiliza o protocolo MQTT para publicar essas informações na rede.
3. **Roteamento e Armazenamento:** O Servidor recebe as mensagens MQTT de temperatura vindas do ESP32 e atualiza sua base de dados.
4. **Apresentação e Visualização:** O Aplicativo Mobile e o Dashboard solicitam (ou assinam) esses dados do servidor e atualizam as telas do usuário final. Dessa forma, a gestão da fábrica visualiza o status em tempo real na sala de controle de forma integrada.

### 3. Decisões ou ações com base nas informações do dashboard

A partir do monitoramento centralizado integrado, a gestão pode tomar diversas ações:

- **Controle de Processos:** Identificar desvios na temperatura ideal de produção e enviar um comando remoto de volta (através da rede MQTT) para que o controlador ative um atuador, como o acionamento de um sistema de resfriamento.
- **Prevenção de Falhas e Manutenção:** Observar padrões anormais de aquecimento (tendências) que indiquem desgaste ou atrito mecânico de um equipamento, agendando uma manutenção preditiva antes que a máquina quebre.
- **Segurança e Monitoramento:** Configurar alertas visuais e sonoros no aplicativo caso a temperatura atinja níveis críticos, permitindo o desligamento de emergência da linha ou a evacuação da área.

### 4. Vantagens de utilizar um sistema distribuído nesse contexto

A implementação dessa arquitetura de SDCD traz melhorias significativas em comparação aos sistemas de controle centralizado antigos:

- **Eliminação de pontos únicos de falha:** O processamento ocorre de forma inteligente e local no ESP32. Se o servidor ou a rede cair, o ESP32 ainda pode estar programado para desligar a máquina automaticamente em caso de superaquecimento extremo, garantindo segurança.
- **Redução drástica de cabeamento:** Como a comunicação via MQTT pode utilizar redes modernas (e muitas vezes sem fio, no caso de microcontroladores como o ESP32), elimina-se o alto custo de materiais e mão de obra para interligar fisicamente todos os sensores do chão de fábrica até um único painel na sala de controle.
- **Confiabilidade e Redundância:** Sistemas distribuídos permitem múltiplos caminhos de comunicação.
- **Escalabilidade:** É muito mais simples adicionar novos sensores e microcontroladores (ESP32) à rede MQTT existente para monitorar outras partes da fábrica, sem a necessidade de paralisar a produção constante do processo contínuo.
