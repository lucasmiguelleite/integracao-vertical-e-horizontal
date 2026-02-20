# Projeto de Rede Industrial: Fábrica de Tijolos Ecológicos

**Objetivo:** Elaborar um plano orçamentário e técnico para a implantação de uma rede industrial em uma indústria de produção de tijolos ecológicos. O projeto abrange a infraestrutura de comunicação e automação.

## 1. Levantamento Técnico e Plano Orçamentário

A tabela abaixo apresenta a identificação dos dispositivos necessários para compor a rede, incluindo especificações técnicas, pesquisa de fornecedores online (simulada), cotação de valores e prazos de entrega.

| Equipamento                              | Especificação Técnica                                                                                | Fornecedor (Exemplo)                       | Valor Unit. (Estimado) | Qtd | Prazo de Entrega                   |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------ | ---------------------- | --- | ---------------------------------- |
| **CLP (Controlador Lógico Programável)** | Módulo CPU com portas Ethernet/IP, suporte a Modbus TCP, robustez IP20.                              | Siemens / Rockwell (Distribuidores Locais) | R$ 4.500,00            | 1   | 15 dias                            |
| **Switch Industrial**                    | Switch Gerenciável 8 portas RJ45, montagem em trilho DIN, suporte a redundância, IP30.               | Phoenix Contact / Moxa                     | R$ 2.800,00            | 2   | 10 dias                            |
| **Dispositivos de Campo (Sensores)**     | Sensores de umidade e temperatura para o solo/mistura, interface 4-20mA ou IO-Link.                  | SICK / Balluff                             | R$ 850,00              | 4   | 7 dias                             |
| **Sistema Supervisório (SCADA/IHM)**     | Licença de software SCADA para 500 tags + IHM Touchscreen 10" IP65.                                  | Elipse Software / WEG                      | R$ 8.000,00            | 1   | Imediato (Licença) / 20 dias (IHM) |
| **Cabeamento e Infraestrutura**          | Cabos Ethernet Cat5e/Cat6 blindados (STP) para ambiente industrial, conectores M12/RJ45 industriais. | Furukawa Industrial                        | R$ 1.500,00 (Lote)     | 1   | 5 dias                             |

_Custo Total Estimado:_ **R$ 23.000,00**

### Adequação e Escalabilidade

Os equipamentos selecionados foram escolhidos pela sua adequação ao ambiente industrial (resistência a poeira da fábrica de tijolos, vibração e ruído elétrico). A adoção de protocolos baseados em Ethernet (como Ethernet/IP ou Profinet) garante a escalabilidade da solução e a fácil compatibilidade com integrações futuras com os sistemas corporativos de TI (como ERPs).

---

## 2. Análise de Viabilidade Técnica e Econômica

Com base no levantamento, a análise de viabilidade considera os seguintes pontos:

- **Custo-Benefício:** O investimento inicial de R$ 23.000,00 é justificado pela drástica redução de falhas na mistura e prensagem dos tijolos ecológicos. A automação reduz o desperdício de matéria-prima e padroniza a qualidade do bloco.
- **Possibilidade de Expansão Futura:** A escolha de switches gerenciáveis e um CLP modular permite que a fábrica adicione novas esteiras ou prensas no futuro sem necessidade de descartar o equipamento atual.

- **Riscos Envolvidos:** O principal risco técnico é a interferência eletromagnética (ruído) nos cabos de rede devido aos motores das prensas. Isso é mitigado pelo uso de cabeamento blindado aterrado corretamente.
- **Dependência de Fornecedores:** Optou-se por protocolos abertos (como Modbus TCP) e hardware de fabricantes com ampla rede de distribuição no Brasil para evitar o aprisionamento tecnológico (_vendor lock-in_).

- **Estimativa de Retorno do Investimento (ROI):** Estima-se que a redução de quebras de produção e otimização do tempo de máquina paguem o sistema em aproximadamente 8 a 12 meses.

**Benefícios para o negócio:** A implementação garantirá monitoramento em tempo real, rastreabilidade dos lotes de tijolos, menor tempo de parada (_downtime_) e maior segurança para os operadores.

---

## 3. Visualização Inicial da Solução Proposta

Abaixo está a descrição da arquitetura de rede proposta, demonstrando organização e coerência técnica:

**Estrutura Topológica:**

1. **Rede Corporativa (TI):** Conectada através de um roteador/firewall (Gateway) para isolar o tráfego e proteger o chão de fábrica, permitindo que a gerência acesse os relatórios de produção com segurança.

2. **Nível de Supervisão (SCADA/IHM):** O computador com o software SCADA e a IHM local no painel ficam conectados ao Switch Industrial Principal na sala de controle.

3. **Nível de Controle (CLP):** O Switch Industrial Principal se conecta ao CLP, que processa toda a lógica da máquina de tijolos.

4. **Nível de Campo:** O CLP interage diretamente com as válvulas, motores da prensa e os sensores de mistura através de módulos de Entradas/Saídas (I/O) utilizando cabeamento industrial robusto. Esta separação em camadas garante a possibilidade de expansão futura da infraestrutura.

---

### Referências

- ALBUQUERQUE, Pedro U. B. de; ALEXANDRIA, Auzuir Ricardo de. Redes industriais. São Paulo: Ensino Profissional, 2009.

- CAIÇARA JÚNIOR, Cícero. Sistemas integrados de gestão: ERP – uma abordagem gerencial. Curitiba: Intersaberes, 2015.

- CARDOSO, Wagner. Planejamento e controle da produção (PCP). São Paulo: Blucher, 2021.

- GROOVER, M. P. Automação industrial e sistemas de manufatura. São Paulo: Pearson, 2011.

- LARA, Carla Eduarda Orlando de Moraes de. Automação e controle industrial. Curitiba: Contentus, 2021.

- LUGLI, Alexandre Baratella; SANTOS, Max Mauro Dias. Sistemas Fieldbus para automação industrial. São Paulo: Érica, 2009.

- MORAES, Cícero Couto de; CASTRUCCI, Plinio de Lauro. Engenharia de automação industrial. São Paulo: LTC, 2007.

- SANTOS, Jadir Perpétuo dos. Sistemas integrados de gestão: busca de agilidade e redução de riscos em seus processos. Rio de Janeiro: Freitas Bastos, 2024.

- SERVIÇO NACIONAL DE APRENDIZAGEM INDUSTRIAL. Departamento Nacional. Redes industriais. Porto Alegre: SENAI-RS, 2014. 39 p. (Atualização Tecnológica em Mecatrônica).
