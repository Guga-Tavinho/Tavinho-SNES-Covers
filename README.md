# SNES Super Everdrive Covers editor

**🇧🇷 [Português](#-português) · 🇺🇸 [English](#-english) · 🇪🇸 [Español](#-español)**

![Capa no navegador do Super EverDrive](docs/console_horizontal.png)

---

## 🇧🇷 Português

Firmware custom para o **Super EverDrive (clone) de SNES** que mostra a **capa de cada jogo** ao lado da lista de
jogos, e uma ferramenta para Windows que converte as suas imagens e gera tudo pronto para o cartão SD.

![A ferramenta](docs/ferramenta.png)

### O que tem de novo em relação à firmware original

| | Original | Custom |
|---|---|---|
| **Capa do jogo** | — | Capa à direita da lista, com até **120 cores** e sem tremer |
| **Formato da capa** | — | **Horizontal 128×96** ou **vertical 96×128**, escolhido **em cada jogo** |
| **Nome na lista** | `001 Secret of Ma` + tamanho/`DIR` | Só o nome do jogo (13 letras), sem número na frente |
| **Nome completo** | Só rolando com X/Y | **Barra cinza** embaixo com o nome completo (até 60 letras) |
| **Número da página** | Embaixo, à esquerda | No **canto direito** |
| **← →** (trocar página) | Mantém a linha do cursor | Vai para o **primeiro jogo da página** |
| **Tela "about"** | Créditos do fabricante | Créditos da custom + **teclas de atalho** |
| **Pastas** | Marcadas com `DIR` | Em **amarelo** (os jogos ficam em cinza) |

| Navegador com capa vertical | Tela "about" |
|---|---|
| ![](docs/console_vertical.png) | ![](docs/console_about.png) |

O resto do console funciona como na firmware original: carregar jogos, saves (SRAM), opções, update de OS etc.

### Requisitos

- **Windows 10 ou 11 (64 bits)** para a ferramenta. Não precisa instalar nada (nem Python).
- Um **Super EverDrive clone de SNES**. A firmware foi feita a partir do **OS v12** desse cartucho.
- As imagens das capas (**PNG, JPG, BMP, GIF ou WEBP**).

### Instalação da ferramenta

1. Baixe o **`SNES Super Everdrive Covers Editor.zip`** na página de *Releases*.
2. **Extraia** o zip numa pasta (não rode o programa de dentro do zip).
3. Abra **`SNES Super Everdrive Covers Editor.exe`**. Deixe a pasta **`_internal`** sempre junto do `.exe`.

> O Windows pode mostrar "O Windows protegeu o computador" (programa novo, sem assinatura digital). Clique em
> **Mais informações → Executar assim mesmo**.

### Como usar

**1. Capas, ROMs e saída**
- **Pasta das capas:** a pasta com as imagens. O nome da imagem deve ser parecido com o nome da ROM
  (ex.: `Super Metroid (Japan, USA).png`). A ferramenta associa sozinha mesmo com pequenas diferenças
  (região, versão, `(Rev 1)`, `[!]`…).
- **Pastas de ROMs:** onde estão as suas ROMs (`.sfc`, `.smc`, `.fig`, `.swc`). Pode ser o próprio cartão SD;
  as subpastas também são lidas.
- **Pasta de saída:** onde os arquivos são gerados.

Na lista à esquerda, **"Mostrar só capas das minhas ROMs"** mostra só as imagens que serão usadas, e
**"Ver ROMs sem capa…"** lista as ROMs que não acharam imagem.

**2. Prévia da capa** — clique numa capa da lista para ver como ela fica no SNES.

| Opção | O que faz |
|---|---|
| **Formato** | Horizontal 128×96 (caixas americanas) ou vertical 96×128 (caixas japonesas/europeias). |
| **Nitidez** (10–200%) | Realça contornos e letras ao reduzir a imagem. |
| **Enquadramento** | **Recortar o centro**, **esticar**, **caber** (com bordas pretas) ou **manual**. |
| **Manual** | Arraste o quadro dourado na imagem original: pelos cantos muda o tamanho, a roda do mouse aproxima/afasta. O quadro pode passar da imagem (a sobra fica preta). |
| **Definir padrão** | Aplica a escolha a todas as capas que não têm ajuste próprio. |
| **Prévias** | Original, a capa como o SNES mostra e a **tela do console** (igual à da TV). |

As escolhas de cada capa ficam salvas no arquivo `capas_config_snes.json`, dentro da pasta das capas.

**3. Gerar**
1. Em **Cartão SD**, clique em **Adicionar caminho…** e escolha a raiz do cartão (ex.: `F:\`).
2. Deixe marcado **"copiar também a firmware para o cartão"** (na primeira vez).
3. Clique em **GERAR COVERS.BIN**. Vai para o cartão:
   - `SEVD\COVERS.BIN` (as capas)
   - `os-capas-v4.smc` (a firmware, na raiz do cartão)

**4. Instalar a firmware no console (só uma vez)**
1. Ligue o console e vá em **toolbox → update os**.
2. Escolha o arquivo **`os-capas-v4.smc`**, aperte **Start** e confirme com **B (YES)**.
3. Espere terminar (step1, step2, step3); o console reinicia sozinho.

Depois disso, para mudar ou acrescentar capas, é só **gerar de novo** — não precisa reinstalar a firmware.

### Teclas no navegador

| Tecla | Ação |
|---|---|
| **B** | Abrir pasta |
| **← →** | Página anterior / próxima (vai para o topo da página) |
| **A** | Voltar |
| **X / Y** | Rolar o nome longo na lista |
| **Start** | Selecionar arquivo / pasta |

### Limitações

- **Até 4.000 capas** por cartão (**3.851** se houver alguma capa vertical).
- **Até 200 itens por pasta** (limite do OS original do cartucho).
- **Sem acentos:** a fonte do console não tem letras acentuadas; elas aparecem como espaço.
- **Ordem da lista:** o OS original ordena só pelas **2 primeiras letras**; jogos com o mesmo começo
  (ex.: vários "Super …") podem ficar fora de ordem entre si.
- Na lista o nome aparece com **13 letras**; na barra, até **60 letras**.
- A capa é encontrada pelo **nome do arquivo da ROM**. Se você renomear uma ROM, gere o `COVERS.BIN` de novo.
  ROMs com o mesmo nome em pastas diferentes usam a mesma capa.
- Feita e testada para o **Super EverDrive clone com OS v12**. Outras versões/modelos não foram testados.

### Segurança

- A firmware é instalada pelo **"update os" original** do próprio console e só grava a área do OS principal.
  O **reserve OS** (sistema de recuperação) **nunca é alterado**.
- **Se algo der errado:** ligue o console **segurando X + A** para entrar no *reserve OS* e reinstale a
  firmware original (`os-v12.smc`) por **toolbox → update os**.
- Guarde uma cópia da firmware original do seu cartucho.

### Créditos

- Custom firmware e ferramenta: **Tavinho Games** —
  [Instagram](https://www.instagram.com/tavinho.games) ·
  [GitHub](https://github.com/Guga-Tavinho) ·
  [YouTube](https://www.youtube.com/@tavinho-games)
- OS original do Super EverDrive: **Krikzz** (I. Golubovskiy).

---

## 🇺🇸 English

Custom firmware for the **SNES Super EverDrive (clone)** that shows **each game's cover art** next to the game
list, plus a Windows tool that converts your images and prepares everything for the SD card.

### What's new compared to the original firmware

| | Original | Custom |
|---|---|---|
| **Cover art** | — | Cover on the right of the list, up to **120 colors**, no flicker |
| **Cover format** | — | **Horizontal 128×96** or **vertical 96×128**, chosen **per game** |
| **Name in the list** | `001 Secret of Ma` + size/`DIR` | Game name only (13 characters), no row number |
| **Full name** | Only by scrolling with X/Y | **Gray bar** at the bottom with the full name (up to 60 characters) |
| **Page number** | Bottom left | **Bottom right** |
| **← →** (change page) | Keeps the cursor row | Jumps to the **first game of the page** |
| **About screen** | Manufacturer credits | Custom firmware credits + **shortcut keys** |
| **Folders** | Marked with `DIR` | Shown in **yellow** (games are gray) |

Everything else works like the original firmware: loading games, saves (SRAM), options, OS update, etc.

### Requirements

- **Windows 10 or 11 (64-bit)** for the tool. Nothing to install (no Python needed).
- An **SNES Super EverDrive clone**. The firmware is based on this cartridge's **OS v12**.
- Cover images (**PNG, JPG, BMP, GIF or WEBP**).

### Installing the tool

1. Download **`SNES Super Everdrive Covers Editor.zip`** from the *Releases* page.
2. **Extract** the zip to a folder (do not run the program from inside the zip).
3. Open **`SNES Super Everdrive Covers Editor.exe`**. Always keep the **`_internal`** folder next to the `.exe`.

> Windows may show "Windows protected your PC" (new program without a digital signature). Click
> **More info → Run anyway**.

### How to use

> The tool's interface is in **Portuguese**. Below, the screen labels are shown exactly as they appear,
> with the translation in parentheses.

**1. Capas, ROMs e saída** (covers, ROMs and output)
- **Pasta das capas** (covers folder): the folder with your images. The image name should be similar to the ROM name
  (e.g. `Super Metroid (Japan, USA).png`). The tool matches them automatically even with small differences
  (region, version, `(Rev 1)`, `[!]`…).
- **Pastas de ROMs** (ROM folders): where your ROMs are (`.sfc`, `.smc`, `.fig`, `.swc`). It can be the SD card itself;
  subfolders are included.
- **Pasta de saída** (output folder): where the files are generated.

In the left list, **"Mostrar só capas das minhas ROMs"** (show only covers of my ROMs) shows only the images
that will be used, and **"Ver ROMs sem capa…"** (see ROMs without cover) lists the ROMs that didn't find an image.

**2. Prévia da capa** (cover preview) — click a cover in the list to see how it looks on the SNES.

| Option | What it does |
|---|---|
| **Formato** (format) | Horizontal 128×96 (US boxes) or vertical 96×128 (Japanese/European boxes). |
| **Nitidez** (sharpness, 10–200%) | Enhances edges and text when shrinking the image. |
| **Enquadramento** (framing) | **recortar o centro** (crop center), **esticar** (stretch), **caber** (fit, black borders) or **manual**. |
| **Manual** | Drag the golden frame on the original image: corners resize it, the mouse wheel zooms in/out. The frame may go past the image (the extra area becomes black). |
| **Definir padrão** (set default) | Applies the choice to every cover without its own setting. |
| **Previews** | Original, the cover as the SNES shows it, and the **console screen** (same as on the TV). |

Each cover's settings are saved in `capas_config_snes.json`, inside the covers folder.

**3. Gerar** (generate)
1. Under **Cartão SD** (SD card), click **Adicionar caminho…** (add path) and choose the root of the card (e.g. `F:\`).
2. Keep **"copiar também a firmware para o cartão"** (also copy the firmware to the card) checked (the first time).
3. Click **GERAR COVERS.BIN** (generate). This goes to the card:
   - `SEVD\COVERS.BIN` (the covers)
   - `os-capas-v4.smc` (the firmware, at the root of the card)

**4. Install the firmware on the console (only once)**
1. Turn on the console and go to **toolbox → update os**.
2. Choose **`os-capas-v4.smc`**, press **Start** and confirm with **B (YES)**.
3. Wait until it finishes (step1, step2, step3); the console restarts by itself.

After that, to change or add covers, just **generate again** — there's no need to reinstall the firmware.

### Buttons in the file browser

| Button | Action |
|---|---|
| **B** | Open folder |
| **← →** | Previous / next page (jumps to the top of the page) |
| **A** | Back |
| **X / Y** | Scroll a long name in the list |
| **Start** | Select file / folder |

### Limitations

- **Up to 4,000 covers** per card (**3,851** if any cover is vertical).
- **Up to 200 items per folder** (limit of the cartridge's original OS).
- **No accented letters:** the console font has none; they are shown as spaces.
- **List order:** the original OS sorts by the **first 2 letters** only; games starting the same way
  (e.g. several "Super …") may be out of order among themselves.
- The list shows **13 characters** of the name; the bar shows up to **60 characters**.
- The cover is found by the **ROM file name**. If you rename a ROM, generate `COVERS.BIN` again.
  ROMs with the same name in different folders share the same cover.
- Made and tested for the **Super EverDrive clone with OS v12**. Other versions/models were not tested.

### Safety

- The firmware is installed with the console's **original "update os"** and only writes the main OS area.
  The **reserve OS** (recovery system) is **never changed**.
- **If something goes wrong:** turn on the console **holding X + A** to enter the *reserve OS* and reinstall
  the original firmware (`os-v12.smc`) through **toolbox → update os**.
- Keep a copy of your cartridge's original firmware.

### Credits

- Custom firmware and tool: **Tavinho Games** —
  [Instagram](https://www.instagram.com/tavinho.games) ·
  [GitHub](https://github.com/Guga-Tavinho) ·
  [YouTube](https://www.youtube.com/@tavinho-games)
- Original Super EverDrive OS: **Krikzz** (I. Golubovskiy).

---

## 🇪🇸 Español

Firmware custom para el **Super EverDrive (clon) de SNES** que muestra la **carátula de cada juego** junto a la
lista de juegos, y una herramienta para Windows que convierte tus imágenes y deja todo listo para la tarjeta SD.

### Novedades respecto a la firmware original

| | Original | Custom |
|---|---|---|
| **Carátula** | — | Carátula a la derecha de la lista, hasta **120 colores** y sin parpadeo |
| **Formato de la carátula** | — | **Horizontal 128×96** o **vertical 96×128**, elegido **por juego** |
| **Nombre en la lista** | `001 Secret of Ma` + tamaño/`DIR` | Solo el nombre del juego (13 letras), sin número delante |
| **Nombre completo** | Solo desplazando con X/Y | **Barra gris** abajo con el nombre completo (hasta 60 letras) |
| **Número de página** | Abajo a la izquierda | En la **esquina derecha** |
| **← →** (cambiar página) | Mantiene la línea del cursor | Va al **primer juego de la página** |
| **Pantalla "about"** | Créditos del fabricante | Créditos de la custom + **teclas de acceso rápido** |
| **Carpetas** | Marcadas con `DIR` | En **amarillo** (los juegos en gris) |

El resto de la consola funciona como en la firmware original: cargar juegos, partidas guardadas (SRAM), opciones,
actualización del OS, etc.

### Requisitos

- **Windows 10 u 11 (64 bits)** para la herramienta. No hay que instalar nada (ni Python).
- Un **Super EverDrive clon de SNES**. La firmware está hecha a partir del **OS v12** de este cartucho.
- Las imágenes de las carátulas (**PNG, JPG, BMP, GIF o WEBP**).

### Instalación de la herramienta

1. Descarga **`SNES Super Everdrive Covers Editor.zip`** desde la página de *Releases*.
2. **Extrae** el zip en una carpeta (no ejecutes el programa desde dentro del zip).
3. Abre **`SNES Super Everdrive Covers Editor.exe`**. Deja siempre la carpeta **`_internal`** junto al `.exe`.

> Windows puede mostrar "Windows protegió su PC" (programa nuevo, sin firma digital). Haz clic en
> **Más información → Ejecutar de todas formas**.

### Cómo usar

> La interfaz de la herramienta está en **portugués**. Abajo, los textos de la pantalla aparecen tal cual,
> con la traducción entre paréntesis.

**1. Capas, ROMs e saída** (carátulas, ROMs y salida)
- **Pasta das capas** (carpeta de carátulas): la carpeta con las imágenes. El nombre de la imagen debe parecerse al de la ROM
  (ej.: `Super Metroid (Japan, USA).png`). La herramienta las asocia sola aunque haya pequeñas diferencias
  (región, versión, `(Rev 1)`, `[!]`…).
- **Pastas de ROMs** (carpetas de ROMs): donde están tus ROMs (`.sfc`, `.smc`, `.fig`, `.swc`). Puede ser la propia tarjeta SD;
  también se leen las subcarpetas.
- **Pasta de saída** (carpeta de salida): donde se generan los archivos.

En la lista de la izquierda, **"Mostrar só capas das minhas ROMs"** (mostrar solo carátulas de mis ROMs) muestra
solo las imágenes que se usarán, y **"Ver ROMs sem capa…"** (ver ROMs sin carátula) lista las ROMs que no
encontraron imagen.

**2. Prévia da capa** (vista previa) — haz clic en una carátula de la lista para ver cómo queda en la SNES.

| Opción | Qué hace |
|---|---|
| **Formato** | Horizontal 128×96 (cajas americanas) o vertical 96×128 (cajas japonesas/europeas). |
| **Nitidez** (10–200%) | Realza bordes y letras al reducir la imagen. |
| **Enquadramento** (encuadre) | **recortar o centro** (recortar el centro), **esticar** (estirar), **caber** (ajustar, con bordes negros) o **manual**. |
| **Manual** | Arrastra el marco dorado sobre la imagen original: por las esquinas cambia el tamaño, la rueda del ratón acerca/aleja. El marco puede salir de la imagen (lo que sobra queda negro). |
| **Definir padrão** (definir por defecto) | Aplica la elección a todas las carátulas sin ajuste propio. |
| **Vistas previas** | Original, la carátula como la muestra la SNES y la **pantalla de la consola** (igual que en la TV). |

Los ajustes de cada carátula se guardan en `capas_config_snes.json`, dentro de la carpeta de carátulas.

**3. Gerar** (generar)
1. En **Cartão SD** (tarjeta SD), haz clic en **Adicionar caminho…** (añadir ruta) y elige la raíz de la tarjeta (ej.: `F:\`).
2. Deja marcado **"copiar também a firmware para o cartão"** (copiar también la firmware a la tarjeta) (la primera vez).
3. Haz clic en **GERAR COVERS.BIN** (generar). Se copia a la tarjeta:
   - `SEVD\COVERS.BIN` (las carátulas)
   - `os-capas-v4.smc` (la firmware, en la raíz de la tarjeta)

**4. Instalar la firmware en la consola (solo una vez)**
1. Enciende la consola y ve a **toolbox → update os**.
2. Elige **`os-capas-v4.smc`**, pulsa **Start** y confirma con **B (YES)**.
3. Espera a que termine (step1, step2, step3); la consola se reinicia sola.

Después, para cambiar o añadir carátulas, solo hay que **generar de nuevo** — no hace falta reinstalar la
firmware.

### Botones en el navegador

| Botón | Acción |
|---|---|
| **B** | Abrir carpeta |
| **← →** | Página anterior / siguiente (va al inicio de la página) |
| **A** | Volver |
| **X / Y** | Desplazar un nombre largo en la lista |
| **Start** | Seleccionar archivo / carpeta |

### Limitaciones

- **Hasta 4.000 carátulas** por tarjeta (**3.851** si hay alguna carátula vertical).
- **Hasta 200 elementos por carpeta** (límite del OS original del cartucho).
- **Sin acentos:** la fuente de la consola no tiene letras acentuadas; aparecen como espacios.
- **Orden de la lista:** el OS original ordena solo por las **2 primeras letras**; los juegos que empiezan
  igual (ej.: varios "Super …") pueden quedar desordenados entre sí.
- En la lista el nombre aparece con **13 letras**; en la barra, hasta **60 letras**.
- La carátula se encuentra por el **nombre del archivo de la ROM**. Si renombras una ROM, genera el
  `COVERS.BIN` de nuevo. ROMs con el mismo nombre en carpetas distintas comparten la carátula.
- Hecha y probada para el **Super EverDrive clon con OS v12**. Otras versiones/modelos no se probaron.

### Seguridad

- La firmware se instala con el **"update os" original** de la consola y solo escribe el área del OS principal.
  El **reserve OS** (sistema de recuperación) **nunca se modifica**.
- **Si algo sale mal:** enciende la consola **manteniendo X + A** para entrar en el *reserve OS* y reinstala la
  firmware original (`os-v12.smc`) desde **toolbox → update os**.
- Guarda una copia de la firmware original de tu cartucho.

### Créditos

- Firmware custom y herramienta: **Tavinho Games** —
  [Instagram](https://www.instagram.com/tavinho.games) ·
  [GitHub](https://github.com/Guga-Tavinho) ·
  [YouTube](https://www.youtube.com/@tavinho-games)
- OS original del Super EverDrive: **Krikzz** (I. Golubovskiy).
