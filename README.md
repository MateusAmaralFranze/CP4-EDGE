Projeto: Smart Lamp (Lâmpada Inteligente)
Autores
Mateus Amaral Franze (RM: 562334)

Felipe Sumida (RM: 563082)

Henrique de Lima (RM: 561876)

Resumo do Projeto
Este projeto tem como objetivo criar uma "Lâmpada Inteligente" utilizando o ESP32 Dev Kit. O projeto permite o controle do LED integrado à placa através de comandos enviados por um Broker MQTT, como o FIWARE. Além disso, ele faz a leitura da luminosidade do ambiente através de um sensor externo (como um fotoresistor ou potenciômetro) e publica esses dados no mesmo broker.

O sistema é composto por:

Hardware: Um ESP32 Dev Kit e os componentes necessários para a medição de luminosidade e controle do LED.

Software: O código em C++ que gerencia a conexão Wi-Fi, a comunicação MQTT e a lógica de controle do LED e do sensor.

Comunicação: O protocolo MQTT para a troca de mensagens entre o ESP32 e o Broker.

Hardware Necessário
1x Placa de Desenvolvimento ESP32 Dev Kit

1x LED (qualquer cor)

1x Potenciômetro (ou um sensor de luminosidade, como um LDR)

Jumpers (fios) para conexão

Conexões (Diagrama de Fios)
O diagrama a seguir ilustra a conexão dos componentes na placa.

LED:

O pino longo (ânodo) do LED está conectado ao pino GPIO 2 do ESP32.

O pino curto (cátodo) do LED está conectado ao pino GND (Terra) do ESP32.

Potenciômetro (ou Sensor de Luminosidade):

Um pino do potenciômetro está conectado ao pino GPIO 34 do ESP32.

O outro pino do potenciômetro está conectado ao pino 3V3 do ESP32.

O pino central do potenciômetro está conectado ao pino GND do ESP32.

Configuração do Código (Código C++)
O código é escrito para a IDE do Arduino, e você pode facilmente ajustar as configurações no início do arquivo main.cpp.

As principais variáveis configuráveis são:

default_SSID: Nome da sua rede Wi-Fi.

default_PASSWORD: Senha da sua rede Wi-Fi.

default_BROKER_MQTT: Endereço IP ou domínio do seu Broker MQTT.

default_TOPICO_SUBSCRIBE: Tópico para receber comandos de controle.

default_TOPICO_PUBLISH_1: Tópico para enviar o status do LED.

default_TOPICO_PUBLISH_2: Tópico para enviar a leitura do sensor de luminosidade.

default_ID_MQTT: Um ID único para a conexão MQTT.

default_D4: Pino GPIO onde o LED está conectado (padrão 2).

Como Usar
Configurar o Código: Abra o arquivo main.cpp na IDE do Arduino e atualize as variáveis de configuração (SSID, PASSWORD, BROKER_MQTT, etc.) com as suas credenciais e detalhes.

Compilar e Fazer Upload: Faça o upload do código para a sua placa ESP32.

Monitorar a Conexão: Abra o Monitor Serial na IDE do Arduino para acompanhar o progresso da conexão Wi-Fi e MQTT.

Enviar Comandos: Use um cliente MQTT (como o Postman ou qualquer outro) para enviar mensagens aos tópicos de controle definidos.

Para ligar o LED, envie a mensagem on para o tópico de controle (/TEF/lamp001/cmd).

Para desligar o LED, envie a mensagem off para o tópico de controle (/TEF/lamp001/cmd).

Receber o Status: O ESP32 irá publicar o status atual do LED no tópico default_TOPICO_PUBLISH_1 e o valor da luminosidade no tópico default_TOPICO_PUBLISH_2, que podem ser monitorados no seu cliente MQTT ou no FIWARE.

Manipulação do LED com Postman
A manipulação do LED foi realizada usando a ferramenta Postman, que foi configurada para enviar comandos MQTT via uma máquina virtual no Azure. O processo envolveu:

Health Check: O Postman foi usado para fazer o "health check" para garantir que o broker estava online e acessível através de um IP público.

Controle: Usando o IP público, o Postman enviou as mensagens "on" e "off" para o tópico de controle, permitindo a manipulação do LED de forma remota.


