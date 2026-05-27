<img src="https://capsule-render.vercel.app/api?type=waving&color=0:6a00ff,100:00c8ff&height=300&section=header&text=Hi,%20I'm%20Joshua&desc=Software%20Engineer%20%7C%20BITLC%20Student&fontSize=55&fontColor=ffffff&descAlign=center&descAlignY=70" width="100%"/>

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LINKEDIN-CONNECT-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/joshua-molnar-2bba77405/)
[![Discord](https://img.shields.io/badge/DISCORD-JOIN-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/users/shujinko2639)
[![Instagram](https://img.shields.io/badge/INSTAGRAM-FOLLOW-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://instagram.com/shujinkohope)
[![Email](https://img.shields.io/badge/EMAIL-CONTACT-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:jmolnar2639@gmail.com?subject=Kontaktanfrage)

![Profile Views](https://komarev.com/ghpvc/?username=IT-W1zard&label=PROFILE%20VIEWS&style=flat&color=00FF00)

</div>

---

## 👨‍💻 About Me

- 🌱 Currently learning at **BITLC** :contentReference[oaicite:1]{index=1}  
- 💻 Focus: Software Engineering & System Basics (Linux, Networking, Dev Tools)
- 💬 Ask me about anything tech related
- 🚀 Always building & improving projects

---

## 📚 Main Learning Hub (IMPORTANT)

 ### 🧾 BITLC 
### > **[My Full Learning Repository](https://github.com/BitLC-NE-2025-2026/Linux-Essentials)** <  
*(This repo contains all exercises, notes, and projects from BITLC)*

---

## 📡 Current project I'm working on [User Lifecycle: Creation, Logging & Deletion]
```

 GNU nano 5.6.1                                        UserMaker                                                    
#!/usr/bin/env bash

#erstellt die Varibale USERFILE und greift auf die Datei NewUsers also unsere Namensliste zu
USERFILE="NewUser"
#erstellt die Variable LOGFILE und die Datei CreatedUsers.log
LOGFILE="CreatedUsers.log"
#Erschafft eine User datei zum aufrufen für den Lösch befehl
> created_users.tmp
#v- speichert Datum und macht dann ein space in LOGFILE
echo "Datum $(date)" >> "$LOGFILE"
echo "" >> "$LOGFILE"
#IFS Was IFS= Was IFS wirklich macht sorgt dafür, dass: führende Leerzeichen erhalten bleiben Bash Zeilen sauber ein>
while IFS= read -r line
do
        #[[ ]] guckt ob etwas wahr oder falsch ist und -z prüft ob etwas leer ist und springt dann in dem fall hier >
        [[ -z "$line" ]] && continue
        #Die erste zeile sagt firstname ist eine variable, $line enthäl die ganze zeile, awk zerlegt Text in Wörter,>
        #Die zweite zeile sagt tr translate zeichen heißt äöüß zu ae oe ua ss und so weiter
        #Dritte zeile, cut Text abschneiden, -c Zeichen auswählen, 1-3 von Zeichen 1 bis 3


        firstname=$(echo "$firstname" | tr 'äöüÄÖÜß' 'aeoeuAEOEss')
        lastname=$(echo "$lastname" | tr 'äöüÄÖÜß' 'aeoeuAEOEss')


        firstpart=$(echo "$firstname" | cut -c1-3 | tr '[:upper:]' '[:lower:]')
        lastpart=$(echo "$lastname" | cut -c1-3 | tr '[:upper:]' '[:lower:]')
        #username ist hier einfach nur der speicherort für die ersten 3 vom vor und nachnamen zusammen
        username="${firstpart}${lastpart}"
        #Schreibt die usernames in die neue logdatei für den löschen befehl
        echo "$username" >> created_users.tmp
        #pwgen passwort generieren, -s random, 12 länge, 1 anzahl
        password=$(pwgen -s 12 1)
        #erstellt einen user mit dem spezifischen namen
        sudo useradd -m "$username"
        # echo in dem fall gibt automatisch für chpasswd hier den username und das passwort an, $username:$password >
        echo "$username:$password" | sudo chpasswd
        #echo schreibt die Logfile und speichert alles in $LOGFILE
        {
                echo "Name: $line"
                echo "Username: $username"
                echo "Passwort: $password"
                echo "Erstellt: $(date)"
                echo "-----------------"
        } >> "$LOGFILE" 

done <  "$USERFILE"

while IFS= read -r username
do
    sudo userdel -r "$username"

        {
                echo "Gelöscht: $username - $(date)"
                echo "-----------------"
        } >> "$LOGFILE"

done < created_users.tmp


echo "Fertig!"
echo "Logdatei: $LOGFILE"

```

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:6a00ff,100:00c8ff&height=300&section=footer" width="100%"/> 
