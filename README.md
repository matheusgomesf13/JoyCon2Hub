# JoyCon2 Hub

**Use os Joy-Con 2 (Nintendo Switch 2) no PC e no Ryujinx — botões, analógico, SL/SR, vibração e movimento.**

O JoyCon2 Hub conecta até **8 Joy-Con 2** por Bluetooth, ativa todos os recursos deles (inclusive os botões **SL** e **SR**, que normalmente não funcionam no PC) e cria, para cada um, um **controle virtual** que qualquer jogo ou emulador reconhece. O movimento é enviado pelo protocolo **CemuHook (DSU)**, usado pelo Ryujinx, Cemu, Dolphin e outros.

> ⬇️ **[Baixar a última versão](../../releases/latest)** — arquivo `JoyCon2Hub_Setup_x.y.z.exe`

---

## Recursos

- **Até 8 Joy-Con 2 ao mesmo tempo**, cada um como um jogador separado (esquerdo ou direito, identificado sozinho).
- **Todos os botões**, incluindo **SL/SR**, HOME, Captura e o botão **C** do Joy-Con 2 direito.
- **Controle virtual por jogador**: Xbox 360 para os jogadores 1 a 4 e DualShock 4 para os jogadores 5 a 8.
- **Movimento (CemuHook/DSU)**: uma porta por controle (26760, 26761, …), sempre no slot 0.
- **Vibração** do jogo repassada ao Joy-Con.
- **LED de jogador** aceso conforme o número do jogador.
- **Bateria em porcentagem** de cada controle.
- **Calibração guiada**: o sensor de movimento em 6 posições, com um exemplo em 3D de como posicionar, e o analógico. Fica salva por controle (pelo endereço MAC).
- **Janela de teste** com o Joy-Con em 3D se mexendo junto com o controle real, o analógico, os sensores e os botões acendendo.
- **Atualização automática**: ao abrir, o programa avisa quando há uma versão nova e se atualiza sozinho, mantendo as calibrações.

## Requisitos

- Windows 10 (1809) ou Windows 11, 64 bits.
- Bluetooth com suporte a **Bluetooth LE** (Bluetooth 4.0 ou mais novo).
- Joy-Con 2 (Nintendo Switch 2).
- O driver **ViGEmBus**, que o instalador já instala se ainda não estiver no computador.

## Instalação

1. Baixe o `JoyCon2Hub_Setup_x.y.z.exe` na página de **[Releases](../../releases/latest)**.
2. Execute o instalador.
   - O instalador não é assinado digitalmente, então o Windows pode mostrar **"O Windows protegeu o computador"**. Clique em **Mais informações → Executar assim mesmo**.
3. Se o ViGEmBus ainda não estiver instalado, o instalador dele abre no meio do processo: é só seguir as telas.
4. No final, marque **Abrir o JoyCon2 Hub agora**.

**Atualizar:** basta rodar o instalador de uma versão nova (ou aceitar o aviso de atualização do próprio programa). A atualização é feita por cima e **mantém calibrações, configurações e atalhos**.

## Como usar

### 1. Conectar os Joy-Con 2
1. Abra o **JoyCon2 Hub**.
2. **Segure o botão SYNC** do Joy-Con 2 (o botãozinho no trilho) até as luzes correrem.
3. O controle aparece na lista como **Jogador 1, 2, …**, identificado como **esquerdo** ou **direito**. O LED do jogador acende no controle.

Para conectar outro controle, repita com ele. Cada controle ocupa o primeiro lugar livre.

### 2. Calibração (só na primeira vez de cada controle)
Na primeira conexão de um controle, a janela **Testar controle** abre e guia a calibração:

- **Sensor de movimento, em 6 posições:** deitado com os botões para cima, de ponta-cabeça, em pé sobre cada ponta e em pé com o trilho para baixo e para cima. Use uma mesa e deixe o controle **parado** em cada posição; o 3D mostra como posicionar.
- **Analógico:** solte o analógico e depois empurre para cima e para a direita, como o programa pedir.

A calibração fica salva e é usada automaticamente nas próximas vezes. Para refazer, abra **Testar** e use **Calibrar sensor de movimento** ou **Calibrar analógico**.

### 3. Configurar no Ryujinx
Para cada jogador, em **Opções → Configurações → Entrada**:

1. **Dispositivo de entrada:** escolha o controle Xbox 360 (ou DualShock 4, para os jogadores 5 a 8) daquele jogador.
2. **Tipo de controle:** Joy-Con esquerdo, Joy-Con direito ou Pro Controller, conforme o jogo.
3. Em **Movimento**, marque **"Usar movimento compatível com CemuHook"** e preencha:
   - **Servidor:** `127.0.0.1`
   - **Porta:** a porta DSU do controle, que aparece no cartão dele: jogador 1 = `26760`, jogador 2 = `26761`, e assim por diante.
   - **Slot:** `0`
4. Salve.

O mesmo servidor DSU funciona no **Cemu**, no **Dolphin** e em outros programas compatíveis com CemuHook.

### 4. Janela "Testar controle"
Clique em **Testar** no cartão de um controle para ver:
- o Joy-Con em **3D** acompanhando a posição real;
- o **analógico**, com o valor enviado ao jogo e o valor cru;
- a **aceleração** e o **giro estimado**;
- os **botões** acendendo, inclusive SL/SR.

Botões da janela:
- **Calibrar sensor de movimento** e **Calibrar analógico**.
- **Girar 90°** e **Inverter**: ajustes finos se o movimento no jogo estiver virado ou espelhado.

## Sobre o movimento

No modo usado no PC, o Joy-Con 2 envia o **acelerômetro**, mas **não envia giroscópio**. Por isso, o JoyCon2 Hub calcula o movimento assim:
- **Inclinação** (frente/trás e lados): medida com precisão pela gravidade.
- **Giro**: estimado a partir da mudança da inclinação.
- **Girar em círculo** (laço, volante) e **puxões rápidos**: detectados à parte e enviados como rotação (experimental).
- **Limitação:** girar o controle deitado sobre a mesa, como um volante plano, não é detectado.

## Onde ficam os arquivos

| O quê | Onde |
|---|---|
| Programa | `C:\Program Files\JoyCon2 Hub\` |
| Calibrações (uma por controle) | `%LOCALAPPDATA%\JoyCon2 Hub\Calibracoes\` |
| Log | `%LOCALAPPDATA%\JoyCon2 Hub\joycon2hub_log.txt` |

No Menu Iniciar, o atalho **Pasta de calibrações** abre essa pasta. Para recalibrar um controle do zero, apague o arquivo dele.

## Problemas comuns

- **O controle não aparece:** segure o SYNC até as luzes correrem. Confira também se o Bluetooth do PC está ligado. Não é preciso parear pelas configurações do Windows.
- **Não aparece controle Xbox no Ryujinx:** o ViGEmBus não está instalado. Reinstale o JoyCon2 Hub, que oferece instalar o driver.
- **Movimento virado ou espelhado no jogo:** use **Girar 90°** e **Inverter** na janela de teste.
- **Movimento torto:** refaça a calibração do sensor, com o controle bem parado em cada posição.
- Se o problema continuar, abra uma **[Issue](../../issues)** e anexe o `joycon2hub_log.txt`.

## Créditos e licenças

- Modelo 3D do Joy-Con 2 direito: **"Nintendo Switch Joy-Con 2 R"**, por *joshuagoldenburgh* (Sketchfab), [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/). Adaptado: cores e peças que acendem.
- Modelo 3D do Joy-Con 2 esquerdo: **"Nintendo Switch 2"**, por *Nicolas Pinilla* (Sketchfab), [CC BY 4.0](http://creativecommons.org/licenses/by/4.0/). Adaptado: só o Joy-Con esquerdo, reorientado.
- **ViGEmBus** e **ViGEmClient**, por Nefarius Software Solutions / Benjamin Höglinger-Stelzer (licenças BSD-3 e MIT).
- Instalador feito com **Inno Setup**.

O código-fonte do JoyCon2 Hub não é publicado neste repositório: aqui ficam a documentação e os instaladores (Releases).

*Nintendo Switch, Nintendo Switch 2 e Joy-Con são marcas da Nintendo. Este projeto não é afiliado nem endossado pela Nintendo.*
