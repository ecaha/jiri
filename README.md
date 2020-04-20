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

Teď je na čase rozblikat built in led světlo esp8266. Na tohle je potřeba program [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html). V PuTTY je potřeba se dostat do esp. Je potřeba změnit connection type na "Serial", do "Serial line" napsat port, do kterého je esp připojené. Do "Speed" napsat 115200 a pak nastává problém který jsme poměrně dlouho řešili. V levé nabídce úplně dole lze najít pod nabídkou "Connection" "Serial". Tam je potřeba změnit flow control na None. Jinak po otevření session se nedá psát.

Jakmile úspěšně otevřeme PuTTY potřebujeme importovat 2 knihovny z micropythonu. Na začátku každého kódu co se bude používat je potřeba naimportovat knihovny se kterými program bude potom pracovat. Potřeba budou knihovny time a machine. To uděláme příkazem `import <knihovna>`.

Takže by to mělo vypadat takhle:
```
>>> import time
>>> import machine
```
Teď je potřeba definovat pin:

`>>> pin = machine.Pin(2, machine.Pin.OUT)`

_pozn.: pin 2 zastává pin DH4. DH4 je pin vbudované led diody Takhle je to jen u ESP8266._

![Pins](https://github.com/ecaha/jiri/blob/master/esp8266pins.jpg "Logo Title Text 2")

