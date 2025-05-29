# 🌬️ Système de Ventilation Intelligente avec Alerte de Surchauffe

## 📌 Description

Ce projet utilise un microcontrôleur Arduino Uno et un capteur de température DHT11 pour surveiller la température ambiante. La température est affichée sur un écran LCD 16x2. Si elle dépasse 28 °C, un message indique que le ventilateur est activé. En cas de surchauffe (au-delà de 35 °C), une LED rouge s’allume pour avertir d’un danger.

> Ce système est utile pour surveiller des pièces sensibles à la température comme des salles serveurs, des armoires électriques ou des laboratoires.

---

## 🔧 Matériel utilisé

| Composant                 | Rôle                               |
|---------------------------|------------------------------------|
| Arduino Uno               | Microcontrôleur principal          |
| Capteur DHT11             | Mesure la température ambiante     |
| Écran LCD 16x2 (mode 4 bits) | Affichage de la température       |
| LED rouge + résistance 220 Ω | Alerte visuelle                   |
| Résistance 4,7 kΩ         | Pull-up du capteur DHT11          |
| Breadboard                | Montage sans soudure               |
| Câbles de connexion       | Connexions entre composants        |
| Alimentation 5V (USB ou externe) | Alimentation du système     |

---

## 🔌 Schéma de câblage (texte)

- **DHT11** :  
  - DATA → D9 (via résistance de 4,7 kΩ à VCC)  
  - VCC → 5V  
  - GND → GND  

- **LCD 16x2** (en 4 bits) :  
  - RS → D7  
  - E → D6  
  - D4–D7 → D5, D4, D3, D2  
  - VSS → GND  
  - VDD → 5V  
  - RW → GND  
  - Vo → GND (ou potentiomètre pour contraste)  

- **LED rouge** :  
  - Anode (+) → D8 via résistance 220 Ω  
  - Cathode (–) → GND  

---

## 🧠 Fonctionnement

- 💡 Si température < 28 °C → État normal (affichage : "Temp. normale")
- 🌬️ Si température entre 28 et 35 °C → Affichage "Ventilateur ON"
- 🚨 Si température > 35 °C → Allumage LED + affichage "ALERTE CHALEUR!"

---

## 💻 Code Arduino

Le code complet du projet se trouve dans le fichier `ventilation_test.ino`. Il contient également un **mode de test automatique** activable via :

```cpp
bool modeTest = true; // Pour simuler des températures de test
