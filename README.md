# Rozvržení
### 1. OVLÁDNOUT GITHUB  
- trochu markdownu

### 2. ÚVOD
- nastudovat zdroje
- popis co chci udělat
- volba uPython

### 3. OSNOVA
- prostředí - pyCraft - počítač
- μPython do ESP8266

### 4. OŽIVENÍ
- led blink

### 5. DRÁTOVÁNÍ

### 6. SOFTWARE & OLED
- docíit aby se na displayi objevilo "Hello word"

### 7. ZÍSKÁNÍ ČASU
- připojení ESP na internet

##### ZDROJE:
[ESP8266 Part #3 – SSD1306 OLED Displays with MicroPython](https://www.youtube.com/watch?v=Fl61uiyRQdM "Zobrazit na YouTube")

[ESP8266 NodeMCU OLED Display Clock Iot Tutorial](https://www.youtube.com/watch?v=gC8btktOYOg "Zobrazit na YouTube")

[MicroPython: OLED Display with ESP32 and ESP8266](https://randomnerdtutorials.com/micropython-oled-display-esp32-esp8266/ "Zobrazit na randomnerdtutorials.com")

[1. Getting started with MicroPython on the ESP8266](http://docs.micropython.org/en/latest/esp8266/quickref.html "Zobrazit na docs.micropython.org")

# Práce
Prvně jsem nainstaloval [Python](https://www.microsoft.com/cs-cz/p/python-38/9mssztt1n39l?activetab=pivot:overviewtab) do počítače.
Potom jsem nainstaloval esptool v command promtu (příkazovém řádku) / power shellu příkazem:

```pip install esptool```

Dále bylo potřeba stáhnout [micropython](http://micropython.org/download/), [frimware](http://micropython.org/download/esp8266/) a [esptool](https://github.com/espressif/esptool). Používal jsem micropython-1.12 a esp8266-20200417-v1.12-375-g28833690b.bin, nejnovější verze, firmware byl z kategorie Daily.

Teď se dostáváme do části kdy většina tutoriálů používá příkazy MacOS. Windows používá příkaz:

```python esptool.py --port <port> erase_flash```

Místo `<port>` je potřeba dosadit název portu, do kterého je ESP8266 připojeno (např. v mém případě com3). Název portu se dá zjistit v device manageru pod položkou Ports (COM & LPT).

Pro použití příkazu je potřeba přes příkaz `cd` se dostat do složky, kde máte uloženou složku s esptoolem.

Teď je potřeba dostat python do ESP8266 příkazem:

`esptool.py --port <port> --baud 460800 write_flash --flash_size=detect -fm dio 0 <název firmwaru, staženého souboru bin>`

Teď je Python úspěšně v ESP8266
