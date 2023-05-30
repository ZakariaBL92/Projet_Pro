# Projet_Pro
Projet d'Automatisation des Actions RED TEAM


Ce projet vise à automatiser diverses actions de sécurité au sein de notre SOC (Security Operations Center). 
Les fonctions implémentées dans ce projet sont les suivantes :

1.	Automatisation d'un test d'intrusion (création d'un scan de vulnérabilités)

2.	Supprimer la conformité réglementaire leaked des emails de votre entreprise

3.	Détecter automatiquement les anomalies en matière de sécurité en temps réel

4.	Créer une plateforme d'alerte automatisée pour les événements de sécurité importants

5.	Automatiser la réponse aux attaques en utilisant des scénarios de défense préétablis

6.	Récupération (scrapping) des vulnérabilités critiques ‘up-to-date’ dans un objectif purple team

Dépendances

Ce projet utilise Python 3. Vous aurez besoin des modules suivants:
•	os
•	re
•	time
•	requests
•	BeautifulSoup

Utilisation

1.	Scan de vulnérabilités
Ce script utilise Nmap pour effectuer un scan de vulnérabilités sur une adresse IP donnée.

import os

def scan_vulnerabilites(ip_address):
    command = f"nmap -sV --script=vulners {ip_address}"
    os.system(command)

scan_vulnerabilites("192.168.1.1")

Ce script lance une commande Nmap depuis le terminal en utilisant os.system(). Nmap est un outil open source pour l'exploration du réseau et l'audit de sécurité. L'option -sV permet d'effectuer une détection de version et l'option --script=vulners permet d'exécuter le script de vulnérabilité vulners, qui est une base de données de vulnérabilités de sécurité en ligne.

2.	Suppression de la conformité réglementaire leaked

Cette fonction supprime les mentions de conformité réglementaire dans le texte donné.

import re

def supprimer_conformite(texte):
    pattern = r"CONFIDENTIALITÉ:\s*\[.+?\]"
    return re.sub(pattern, "", texte)

email = "Bonjour,\n\nCONFIDENTIALITÉ: [RGPD] Voici le rapport ..."
email_modifie = supprimer_conformite(email)



 Automatisation d'un test d'intrusion (création d'un scan de vulnérabilités) avec Nmap:

python

import os

def scan_vulnerabilites(ip_address):
    command = f"nmap -sV --script=vulners {ip_address}"
    os.system(command)

scan_vulnerabilites("192.168.1.1")

Ce script lance une commande Nmap depuis le terminal en utilisant os.system(). Nmap est un outil open source pour l'exploration du réseau et l'audit de sécurité. L'option -sV permet d'effectuer une détection de version et l'option --script=vulners permet d'exécuter le script de vulnérabilité vulners, qui est une base de données de vulnérabilités de sécurité en ligne.

    Supprimer la conformité réglementaire leaked des emails de votre entreprise:

python

import re

def supprimer_conformite(texte):
    pattern = r"CONFIDENTIALITÉ:\s*\[.+?\]"
    return re.sub(pattern, "", texte)

email = "Bonjour,\n\nCONFIDENTIALITÉ: [RGPD] Voici le rapport ..."
email_modifie = supprimer_conformite(email)

Ce script utilise des expressions régulières (module re en Python) pour trouver et supprimer toute information de conformité dans un texte, généralement dans un email. Le pattern spécifié dans le script cherche une chaîne qui commence par "CONFIDENTIALITÉ:" suivie de tout texte entre crochets.

3.	Détection d'anomalies

Cette fonction récupère et analyse les logs pour détecter des anomalies.

import time

def detecter_anomalies(logs):
    # Analyse des logs pour détecter des anomalies
    pass

while True:
    logs = recuperer_logs()
    detecter_anomalies(logs)
    time.sleep(60)  # Vérifie toutes les minutes


Ce script est un exemple simplifié d'un programme qui fonctionne en boucle pour vérifier constamment les logs de sécurité et détecter les anomalies. La fonction recuperer_logs() (non définie ici) pourrait être une fonction qui récupère les derniers logs de sécurité de votre système. La fonction detecter_anomalies(logs) devrait être une fonction qui analyse ces logs et détecte les anomalies.

4.	Plateforme d'alerte

Cette fonction envoie une alerte par email lorsque des événements de sécurité importants sont détectés.


def envoyer_alerte(email, sujet, message):
    # Envoie un email d'alerte
    pass

def plateforme_alerte():
    logs = recuperer_logs()
    if detecter_evenements_important(logs):
        envoyer_alerte("email@entreprise.com", "Alerte de sécurité", "Message d'alerte")

Ce script définirait une fonction envoyer_alerte(email, sujet, message) qui envoie un email avec un sujet et un message donné à une adresse email donnée. La fonction plateforme_alerte() récupérerait les logs de sécurité (avec une fonction recuperer_logs(), non définie ici), vérifierait s'il y a des événements de sécurité importants (avec une fonction detecter_evenements_important(logs), non définie ici) et si c'est le cas, enverrait une alerte par email.

5.	Automatisation de la réponse aux attaques

Cette fonction automatise la réponse aux différentes types d'attaques en utilisant des scénarios de défense préétablis.

def automatiser_reponse(attaque_type):
    if attaque_type == "ddos":
        bloquer_ddos()
    elif attaque_type == "phishing":
        bloquer_phishing()
    # Ajoutez d'autres types d'attaques et les actions à effectuer

Ce script définirait une fonction automatiser_reponse(attaque_type) qui prendrait en entrée le type d'attaque et exécuterait une réponse préétablie en fonction de ce type. Dans cet exemple, si le type d'attaque est "ddos", la fonction bloquer_ddos() serait exécutée, et si le type d'attaque est "phishing", la fonction bloquer_phishing() serait exécutée. Vous devriez définir ces fonctions (bloquer_ddos(), bloquer_phishing(), etc.) en fonction des actions spécifiques que vous souhaitez effectuer en réponse à chaque type d'attaque.

6.  Récupération (scrapping) des vulnérabilités critiques ‘up-to-date’ dans un objectif purple team:

Cette a fonction a pour objectif de récuperer les vulnérabilités critiques.

import requests
from bs4 import BeautifulSoup

def recuperer_vulnerabilites_critiques():
    url = "https://exemple.com/vulnerabilites"
    response = requests.get(url)
    soup = BeautifulSoup(response.content, "html.parser")

    vulnerabilites_critiques = []

    for vuln in soup.find_all("div", class_="vulnerabilite_critique"):
        vulnerabilites_critiques.append(vuln.text)

    return vulnerabilites_critiques

Ce script utilise le module requests pour récupérer le contenu HTML d'une page web qui liste des vulnérabilités de sécurité, et BeautifulSoup pour analyser ce contenu HTML. La fonction recuperer_vulnerabilites_critiques() récupère toutes les div avec la classe "vulnerabilite_critique" et ajoute le texte de ces div à une liste vulnerabilites_critiques, qui est ensuite renvoyée par la fonction. Vous devriez remplacer "https://exemple.com/vulnerabilites" par l'URL de la page web qui liste les vulnérabilités de sécurité que vous souhaitez récupérer.
