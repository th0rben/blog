---
layout: post
title:  "Wetterstation mit einem Rapspberry Pi"
ref: weatherstation
date:   2018-07-30 13:29:44 +0100
categories: raspberry server
lang: de
---
Mit der hier beschrieben Wetterstation kann die Raumtemperatur und -feuchtigkeit gemessen werden. Wenn diese Daten, kritische Wert unter- oder überschreiten, werden sie über ein Alarmsystem an den Benutzer gesandt.

Was wir dazu brauchen:
- Raspberry Pi Zero mit Wlan und aufgelöteten Pins
- Temperatur und Feuchtigkkeitsmesser

Was man vorher können sollte:
- Etwas Python

Dieser Artikel umfasst 3 Abschnitte um möglichst wenig Redundanz zu erzeugen haben ich für Abschnitte, die auch von anderen Artikeln verwendet werden, einzelne Artikel erstellt. Das erhöht auch die Übersichtlichkeit dieses Artikels.

1. Installieren von Raspbian und Herstellung einer SSH-Verbindung
(link zum Artikel)
2. Installation der Hardware
3. Aufbau des Warnsystem

## Aufbau des Warnsystems
Das Warnsystem sendet eine Benachritung über E-Mail oder Telegram an den Benutzer. Für unerfahrene Benutzer empfehle ich die Verwendung von E-Mails.

### E-Mail Warnungen

{% highlight python %}
sender = "sender@gmail.com"
recipient = "recipient@gmail.com"
password = "password"
subject = "subject"
server = "smtp.gmail.com"
port = 465
def sendmail(text):
    smtp_server = smtplib.SMTP_SSL(server, port)
    smtp_server.login(sender, password)
    message = "Subject: {}\n\n{}".format(subject, text)
    smtp_server.sendmail(sender, recipient, message)
    smtp_server.close()
{% endhighlight %}

Belege nun die Variablen so wie es deinen Daten entspricht. Ich empfehle die Einrichtung einer Wegwerf-Email-Adresse, da bei zu häufigem Versenden (z. B. bei häufigem ausprobieren), Email-Adressen gesperrt werden können.