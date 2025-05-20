import yfinance
import pyautogui
import pyperclip
import webbrowser
import time

ticker = input("Digita el código la acción ") # Acá podemos usar otra acción

data = yfinance.Ticker("AAPL").history("6mo")
cierre = data.Close

maxima = round(cierre.max(), 2)
minima = round(cierre.min(), 2)
valor_medio = round(cierre.mean(),2)

destinatario = "dorisdiaz1967@gmail.com"
asunto = "Análisis de acciones últimos 6 meses" 

# Hago un f str para insertar las funciones
mensaje = f"""
Hola Amanda,

Acá te envió el análsis de las acciones de los últimos 6 meses de {ticker}:

Cotización máxima: USD {258.4}
Cotización mínima: USD {172.19}
Valor medio: USD {226.52}

Cualquier cosa me cuentas ;)

Javier,
"""
# Abri el navegador para ir a gmail
webbrowser.open("https://outlook.live.com/mail/0/")

time.sleep(4)

pyautogui.PAUSE = 3

# Click en el botón "Redactar" / "Compose"
pyautogui.click(142, 223)

# Escribir el destinatario
pyperclip.copy(destinatario)
pyautogui.hotkey("ctrl", "v")
pyautogui.hotkey("tab")

# Escribir el asunto
pyperclip.copy(asunto)
pyautogui.hotkey("ctrl", "v")
pyautogui.hotkey("tab")

# Escribir el mensaje
pyperclip.copy(mensaje)
pyautogui.hotkey("ctrl", "v")

# Click en el botón de enviar 
pyautogui.click(670, 272)

# Cerrar gmail
pyautogui.hotkey("ctrl", "f4")

