# JoyCon2 Hub

**Use os Joy-Con 2 (Nintendo Switch 2) no PC e no Ryujinx — botões, analógico, SL/SR, vibração e movimento.**

O JoyCon2 Hub conecta até **8 Joy-Con 2** por Bluetooth, ativa todos os recursos deles (inclusive os botões **SL** e **SR**, que normalmente não funcionam no PC) e cria, para cada um, um **controle virtual** que qualquer jogo ou emulador reconhece. O movimento é enviado pelo protocolo **CemuHook (DSU)**, usado pelo Ryujinx, Cemu, Dolphin e outros.

> ⬇️ **[Baixar a última versão](../../releases/latest)** — arquivo `JoyCon2Hub_Setup_x.y.z.exe`

<p align="center">
  <img src="docs/main.png" alt="JoyCon2 Hub - controles conectados" width="420">
  &nbsp;
  <img src="docs/joined.png" alt="Esquerdo + direito unidos num controle completo" width="420">
</p>
<p align="center">
  <img src="docs/test.gif" alt="Janela de teste com o Joy-Con 2 em 3D, analógico, sensores e botões" width="860">
</p>

### English

**Use Joy-Con 2 (Nintendo Switch 2) controllers on Windows and in Ryujinx — every button including SL/SR, sticks, HD rumble and motion (real gyro).**

- Up to **8 Joy-Con 2** over Bluetooth LE, no Windows pairing needed (just hold SYNC).
- Each one becomes a **virtual Xbox 360** (players 1–4) or **DualShock 4** (players 5–8) controller.
- **Join** a left + right pair into one full controller.
- **Motion via CemuHook/DSU** for Ryujinx, Cemu, Dolphin: one port per player (`127.0.0.1`, port 26760 + player − 1, slot 0).
- **Switch 2 emulators (Lichii, Eden-NX2):** Lichii only connects the Switch 2 *Pro Controller* by itself. JoyCon2 Hub adds the **Joy-Con 2**. In *Emulation → Configure… → Controls*, pick the virtual Xbox controller as the input device. Then go to *Motion → Configure → CemuhookUDP Config*: `127.0.0.1:26760` is there by default; add 26761, 26762… for more players. Finally click the motion field (*Motion 2* for Right Joycon, *Motion 1* for Left/Pro) and shake the Joy-Con without touching the mouse. If it says "Mouse", right-click → Clear and retry.
- Guided calibration, live 3D test window, battery %, player LEDs, tray icon, auto-update.
- The interface follows your Windows language (English, Português, Español, Français, Deutsch, Italiano, Русский, 日本語, 한국어, 中文).

**Install:** download `JoyCon2Hub_Setup_x.y.z.exe` from **[Releases](../../releases/latest)** and run it (it installs the ViGEmBus driver if needed). The installer is not code-signed, so SmartScreen may warn: *More info → Run anyway*. Requires Windows 10 1809+ / 11 (64-bit) and a Bluetooth 4.0+ (LE) adapter.

Questions or problems? Open an **[Issue](../../issues)** (attach `%LOCALAPPDATA%\JoyCon2 Hub\joycon2hub_log.txt`).

---

## Recursos

- **Até 8 Joy-Con 2 ao mesmo tempo**, cada um como um jogador separado (esquerdo ou direito, identificado sozinho).
- **Todos os botões**, incluindo **SL/SR**, HOME, Captura e o botão **C** do Joy-Con 2 direito.
- **Controle virtual por jogador**: Xbox 360 para os jogadores 1 a 4 e DualShock 4 para os jogadores 5 a 8.
- **Juntar esquerdo + direito num controle completo**: o botão **Juntar** no cartão de um Joy-Con une ele a um do outro lado (com mais de um disponível, você escolhe qual). Os dois viram **um só controle virtual**, segurados na vertical como um controle comum: dois analógicos, direcional, ABXY, L/R, ZL/ZR, −/+ e HOME (SL/SR não são usados). O movimento vai pela porta DSU do jogador principal, e você escolhe se vem do Joy-Con **esquerdo ou direito**. O cartão unido tem **Testar** (tela própria do controle completo), **Separar** e **Desconectar** (os dois). Ao conectar, os Joy-Con continuam separados como sempre.
- **Movimento (CemuHook/DSU)**: uma porta por controle (26760, 26761, …), sempre no slot 0.
- **Vibração** do jogo repassada ao Joy-Con.
- **LED de jogador** aceso conforme o número do jogador.
- **Bateria em porcentagem** de cada controle.
- **Calibração guiada**: o sensor de movimento em 6 posições, com um exemplo em 3D de como posicionar, e o analógico. Fica salva por controle (pelo endereço MAC).
- **Janela de teste** com o Joy-Con em 3D se mexendo junto com o controle real, o analógico, os sensores e os botões acendendo.
- **Ícone na bandeja** e **configurações na engrenagem**: iniciar com o Windows (inclusive oculto, só na bandeja) e manter rodando ao fechar a janela.
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

### 3b. Configurar no Lichii (emulador de Switch 2) — e no Eden / Eden-NX2
O Lichii conecta sozinho só o **Pro Controller** do Switch 2. Os **Joy-Con 2** entram pelo JoyCon2 Hub. Baixe o Lichii somente pela página oficial de releases no GitHub ([zortos293/Lichii](https://github.com/zortos293/Lichii/releases)).

1. Abra **Emulation → Configure… → Controls**.
2. **Servidores de movimento:** em **Motion**, clique em **Configure** (janela *Configure Motion / Touch*). Em **CemuhookUDP Config**, o servidor `127.0.0.1` porta `26760` (jogador 1) já vem cadastrado. Para outros jogadores, use **Add Server** com `127.0.0.1` e a porta de cada um (`26761`, `26762`, …). O botão **Test** confere a ligação.
3. Em cada **Player N**:
   - **Input Device:** o controle Xbox 360 (ou DualShock 4) daquele jogador;
   - **Controller type:** Pro Controller, Left Joycon, Right Joycon ou Dual Joycons (para o par unido com **Juntar**), conforme o jogo;
   - **Movimento:** com o tipo **Right Joycon** o campo é **Motion 2**. Com Left Joycon ou Pro Controller é **Motion 1**. Com Dual Joycons, preencha os dois. Clique no campo, **solte o mouse** e **chacoalhe forte** o Joy-Con daquele jogador. O campo deixa de mostrar *[not set]*.
     - Se aparecer **Mouse**, o Lichii gravou o mouse, que se mexeu antes do Joy-Con. Clique com o botão direito no campo, escolha **Clear** e tente de novo sem encostar no mouse.
4. Clique em **OK**.

**Se mesmo assim não gravar:** feche o Lichii e edite `%APPDATA%\lichii\config\qt-config.ini`. Troque as linhas `player_0_motionleft=` e `player_0_motionright=` por (jogador 1, porta 26760):
```
player_0_motionleft="engine:cemuhookudp,motion:0,port:26760,pad:0,guid:0000000000000000000000007f000001"
player_0_motionright="engine:cemuhookudp,motion:0,port:26760,pad:0,guid:0000000000000000000000007f000001"
```
Para o jogador 2, use `player_1_…` com `port:26761` e `pad:4`. Para o jogador 3, `player_2_…` com `port:26762` e `pad:8`, e assim por diante. Os servidores precisam estar cadastrados na mesma ordem: 26760, 26761, 26762…

O Eden e o Eden-NX2 têm as mesmas telas (todos vêm do yuzu).

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

O JoyCon2 Hub envia ao emulador o **acelerômetro** e o **giroscópio real** do Joy-Con 2, nos três eixos:
- O giro vem da orientação que o próprio controle calcula com o giroscópio dele. Por isso funciona também girar o controle deitado sobre a mesa, como um volante plano.
- O giroscópio tem um pequeno desvio que muda de controle para controle. Ao conectar, deixe o controle **parado por 1 segundo** para o programa medir e descontar esse desvio. Enquanto isso, a janela de teste mostra *"Medindo o giro"*.
- Até o desvio ser medido, o giro é estimado pela inclinação (gravidade), como nas versões antigas.

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
