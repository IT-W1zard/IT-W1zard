<img src="https://capsule-render.vercel.app/api?type=waving&color=0:6a00ff,100:00c8ff&height=300&section=header&text=Hi,%20I'm%20Joshua&desc=Software%20Engineer%20%7C%20BITLC%20Student&fontSize=55&fontColor=ffffff&descAlign=center&descAlignY=70" width="100%"/>

<div align="center">

[![LinkedIn](https://img.shields.io/badge/LINKEDIN-CONNECT-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/joshua-molnar-2bba77405/)
[![Discord](https://img.shields.io/badge/DISCORD-JOIN-5865F2?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/users/shujinko2639)
[![Instagram](https://img.shields.io/badge/INSTAGRAM-FOLLOW-E4405F?style=for-the-badge&logo=instagram&logoColor=white)](https://instagram.com/shujinkohope)
[![Email](https://img.shields.io/badge/EMAIL-CONTACT-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:jmolnar2639@gmail.com?subject=Kontaktanfrage)

![Profile Views](https://komarev.com/ghpvc/?username=IT-W1zard&label=PROFILE%20VIEWS&style=flat&color=00FF00)

</div>

---

# 👨‍💻 About Me

- 🌱 Currently learning at **BITLC** :contentReference[oaicite:1]{index=1}  
- 💻 Focus: Software Engineering & System Basics (Linux, Networking, Dev Tools)
- 💬 Ask me about anything tech related
- 🚀 Always building & improving projects

---

# 📚 Main Learning Hub (IMPORTANT)

 ### 🧾 BITLC 
## > **[My Full Learning Repository](https://github.com/BitLC-NE-2025-2026/Linux-Essentials)** <  
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

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:6a00ff,100:00c8ff&height=300&section=footer" width="100%"/> ```

/*=============== GOOGLE FONTS ===============*/
@import url("https://fonts.googleapis.com/css2?family=Poppins:wght@400;500;600&display=swap");

/*=============== VARIABLES CSS ===============*/
:root {
  --header-height: 3.5rem;

  /*========== Colors ==========*/
  /*Color mode HSL(hue, saturation, lightness)*/
  --white-color: hsl(0, 0%, 100%);

  /*========== Font and typography ==========*/
  /*.5rem = 8px | 1rem = 16px ...*/
  --body-font: "Poppins", sans-serif;
  --h3-font-size: 1rem;
  --normal-font-size: .938rem;
}

/*========== Responsive typography ==========*/
@media screen and (min-width: 1150px) {
  :root {
    --h3-font-size: 1.25rem;
    --normal-font-size: 1rem;
  }
}

/*=============== BASE ===============*/
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body {
  font-family: var(--body-font);
  font-size: var(--normal-font-size);
}

ul {
  list-style: none;
}

a {
  text-decoration: none;
}

img {
  display: block;
  max-width: 100%;
  height: auto;
}

/*=============== LAYOUT ===============*/
.image-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
  z-index: -1;
}

.main {
  padding-top: 5rem;
  margin-inline: 1.5rem;
  color: var(--white-color);
}

/*=============== HEADER ===============*/
.header {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  margin: 1rem;
}

.header__container {
  width: 100%;
  height: var(--header-height);
  background-color: hsla(0, 0%, 0%, .2);
  backdrop-filter: blur(16px);
  border-radius: 1rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding-inline: 1rem;
}

.header__logo {
  display: flex;
  align-items: center;
  column-gap: .25rem;
  color: var(--white-color);
  font-weight: 500;
}

.header__logo i {
  font-size: 1.5rem;
}

.header__toggle {
  width: 32px;
  height: 32px;
  border-radius: .5rem;
  border: none;
  outline: none;
  font-size: 1.5rem;
  background-color: hsla(0, 0%, 0%, .2);
  color: var(--white-color);
  cursor: pointer;
}

/*=============== SIDEBAR ===============*/
.sidebar {
  position: fixed;
  top: 0;
  left: -120%;
  bottom: 0;
  width: 232px;
  background-color: hsla(0, 0%, 0%, .2);
  backdrop-filter: blur(16px);
  z-index: 100;
  padding: 1rem 1rem 1.5rem;
  margin: 1rem;
  border-radius: 1rem;
  transition: left .4s;
}

.sidebar__logo {
  display: flex;
  align-items: center;
  column-gap: .75rem;
  color: var(--white-color);
  padding: 0 0 1rem .5rem;
  font-weight: 500;
  border-bottom: 1px solid hsla(0, 0%, 100%, .3);
}

.sidebar__logo i {
  font-size: 1.5rem;
}

.sidebar__content {
  display: grid;
  row-gap: .5rem;
  padding-top: 1.5rem;
}

.sidebar__link {
  display: flex;
  align-items: center;
  column-gap: .75rem;
  color: var(--white-color);
  padding: .5rem;
  border-radius: .5rem;
  transition: background-color .4s;
}

.sidebar__link i {
  font-size: 1.25rem;
}

.sidebar__link span {
  font-weight: 500;
}

.sidebar__link:hover {
  background-color: hsla(0, 0%, 0%, .2);
}

/* Show sidebar */
.show-sidebar {
  left: 0;
}

/*=============== DROPDOWN ===============*/
.drop__button {
  width: 100%;
  flex-direction: row;
  border: none;
  outline: none;
  background: none;
  font: 500 var(--normal-font-size) var(--body-font);
  cursor: pointer;
}

.drop__arrow {
  margin-left: auto;
  transition: transform .4s;
}

.drop__list {
  display: grid;
  row-gap: .25rem;
  height: 0;
  overflow: hidden;
  transition: height .4s;
}

.drop__item {
  position: relative;
  display: block;
  color: var(--white-color);
  padding: .5rem .5rem .5rem 2.25rem;
  border-radius: .5rem;
  transition: background-color .4s;
}

.drop__item::after {
  content: "";
  width: 6px;
  height: 6px;
  background-color: var(--white-color);
  position: absolute;
  left: 1rem;
  top: 0;
  bottom: 0;
  margin: auto 0;
  border-radius: 50%;
}

.drop__item:hover {
  background-color: hsla(0, 0%, 0%, .2);
}

/* Rotate drop icon */
.show-drop .drop__arrow {
  transform: rotate(-180deg);
}

/*=============== BREAKPOINTS ===============*/
/* For small devices */
@media screen and (max-width: 320px) {
  .header {
    margin-inline: .5rem;
  }

  .sidebar {
    width: 200px;
    margin-inline: .5rem;
  }
}

/* For large devices */
@media screen and (min-width: 1150px) {
  .header {
    margin: 1.5rem;
    padding-left: 274px;
    transition: padding .4s;
  }
  .header__container {
    height: calc(var(--header-height) + 2rem);
    padding-inline: 1.5rem;
  }
  .header__toggle {
    display: none;
  }

  .sidebar {
    left: 0;
    width: 250px;
    margin: 1.5rem;
    padding: 2rem 1.5rem;
  }

  .main {
    padding-left: 274px;
    padding-top: 8rem;
    transition: padding .4s;
  }
}
