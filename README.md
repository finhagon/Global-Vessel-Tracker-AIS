Global Vessel Tracker: Python & Power BI
Este repositório contém uma solução de inteligência logística que realiza o rastreamento global de navios em tempo real. Utilizando Python para o consumo de dados via WebSockets e Power BI para a visualização analítica, o projeto identifica embarcações nos maiores hubs portuários do mundo, calcula telemetria de viagem e monitora a proximidade costeira.

 Objetivo do Projeto
Prover uma ferramenta de baixo custo para monitoramento de frotas e análise de tráfego portuário, focando na chegada e saída de navios nos principais centros comerciais do mundo.

   Funcionalidades Principais
   Streaming de Dados em Tempo Real: Conexão direta com a rede mundial de transponders AIS.

   Cobertura de Hubs Globais: Base de dados integrada com os principais portos da China, Ásia, Oriente Médio e Brasil.

   Cálculo de Proximidade (Haversine): Algoritmo matemático que determina a distância exata entre o navio e o porto de destino.

   Telemetria Operacional: Captura de velocidade (SOG em Nós), curso (COG) e timestamp UTC formatado.
   Classificação de Sinal: Identifica automaticamente a qualidade da recepção do sinal (Forte vs. Fraco).

  Limitações e Pontos Negativos (Transparência Técnica)
Como este projeto utiliza a API gratuita do AISStream, ele possui restrições importantes que devem ser consideradas em análises profissionais:

Restrição T-AIS (Terrestre): O sinal é captado exclusivamente por antenas em terra. Isso limita o alcance a aproximadamente 40-75 km da costa.

Zonas Cegas Oceânicas: O script não captura sinais via Satélite (S-AIS). Portanto, navios em travessias transoceânicas (meio do Atlântico ou Índico) ficarão invisíveis até se aproximarem de uma antena terrestre.

Dependência de Voluntários: A cobertura em tempo real depende de antenas mantidas por entusiastas. Áreas remotas ou países com pouca infraestrutura de rede podem apresentar lacunas de dados.

Latência de Dados Estáticos: O nome do navio e o tipo de carga são transmitidos em intervalos maiores (6 min). Em coletas rápidas, o navio pode aparecer apenas pelo MMSI até que o pacote estático seja recebido.

  Stack Tecnológica
Linguagem: Python 3.x

Bibliotecas: pandas, websocket-client, math, datetime

Visualização: Microsoft Power BI

Protocolo: WSS (Websocket Secure)

   Como Replicar este Projeto
1. Obtenha sua API Key
Cadastre-se gratuitamente em AISStream.io para receber sua chave de acesso.

2. Configuração no Power BI
Abra o Power BI > Obter Dados > Script do Python.

Cole o código disponível no arquivo rastreador_global.py deste repositório.

Importante: No Power Query (Transformar Dados), você deve alterar o tipo das colunas Latitude, Longitude e Velocidade para Número Decimal usando a localidade Inglês (Estados Unidos).

    Exemplo de Insights Gerados
Análise de Congestionamento: Identificação de navios parados (velocidade < 0.5 nós) em zonas de fundeio nos portos de Shanghai e Santos.

Monitoramento de Rota: Rastreamento da aproximação de petroleiros nos terminais do Oriente Médio (Jebel Ali, Hamad).

Performance de Frota: Comparação de velocidades médias entre diferentes tipos de embarcações de carga.
![Dashboard](screenshots/seu_print.png)

