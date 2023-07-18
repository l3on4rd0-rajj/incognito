#!/usr/bin/env python3

import subprocess
import sys
from pyfiglet import Figlet

# Check if pyfiglet module is installed
try:
    from pyfiglet import Figlet
except ImportError:
    print("Installing pyfiglet module...")
    subprocess.check_call([sys.executable, "-m", "pip", "install", "pyfiglet"])

# Rest of your code
from twilio.rest import Client

def send_sms(sender_name, recipient_number, message):
    account_sid =    'seu input'
    auth_token =     'seu input'
    twilio_number =  'seu input'

    client = Client(account_sid, auth_token)

    message = client.messages.create(
        body=message,
        from_=twilio_number,
        to=recipient_number
    )

    print('SMS enviado com sucesso. SID: {}'.format(message.sid))

# Display "INCOGNITO" figlet text art
f = Figlet(font='slant')
figlet_text = f.renderText("INCOGNITO")
print(figlet_text)

# Display developer information and version
developer = "Desenvolvido por Leonardo/Radesh"
github_link = "https://github.com/l3on4rd0-rajj"
current_version = "1.1.2023"

# Calculate the number of spaces needed for center alignment
total_width = len(figlet_text.split('\n')[0])
padding = (total_width - len(developer)) // 2

print(f"{' ' * padding}{developer}")
print(f"{' ' * padding}{github_link}")
print(f"{' ' * padding}Versão atual: {current_version}\n")

# Exemplo de uso
sender_name = input("Nome do remetente: ")
recipient_number = input("Número do destinatário (com código do país): ")
message = input("Mensagem: ")

send_sms(sender_name, recipient_number, message)

