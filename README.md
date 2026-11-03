Voici le **récapitulatif final et corrigé** de votre installation complète, avec les **`Shelly 1PM Gen4` placés directement dans les boîtes d'encastrement murales** derrière chacun de vos 9 radiateurs (et zéro câblage à faire dans le cellier !).

---

### 1. Vue d'ensemble de l'architecture

```
====================================================================================
  AU REZ-DE-CHAUSSÉE (4 radiateurs neufs IRSAP Tesi 3 — 5500 W au total)
====================================================================================
  • 4x IRSAP Tesi 3 Électrique type S, SANS RÉGULATION :
    ├── Cuisine : 1x 1000 W (Réf: RT 3 0600 15 .. IR SRN)
    ├── Salle :   1x 1500 W (Réf: RT 3 0600 21 .. IR SVN) — 1500 W nominal IRSAP
    ├── Salon :   1x 1500 W (Réf: RT 3 0600 21 .. IR SVN) — (pour vos 2 emplacements 1550 W)
    └── Bureau :  1x 1500 W (Réf: RT 3 0600 21 .. IR SVN)
  • 4x Shelly 1PM Gen4 (1 caché dans chaque boîte murale derrière chaque Tesi)
  • 2x Sondes Shelly H&T Gen3 (idéalement sur USB-C) ou BLU H&T :
    ├── 1 sonde pour la pièce de vie (groupe Cuisine 1000 W + Salle 1500 W + Salon 1500 W = 4000 W)
    └── 1 sonde pour le Bureau (1500 W) — (ou 1 seule sonde au RDC si bureau ouvert)
  • (Option) 1x Shelly Wall Display

====================================================================================
  À L'ÉTAGE & SALLE DE BAIN (1 Tesi + 1 Sèche-serviettes + 3 Acova — 6250 W)
====================================================================================
  • Palier : 1x IRSAP Tesi 3 Électrique type S, SANS RÉGULATION de 1000 W
    (Réf: RT 3 0600 15 .. IR SRN)
  • Salle de bain : 1x Sèche-serviettes asymétrique IRSAP type S, SANS RÉGULATION
    de 750 W (standard SDB ; ou 500 W si ≤ 5 m²) — Funky_S, Soul_S ou Jazz_S
  • Chambres : Vos 3x Acova TMC-150-086-2 (3x 1500 W) à thermostat MÉCANIQUE
    (molette bloquée au maximum) avec fil pilote câblé jusqu'au cellier
  • 5x Shelly 1PM Gen4 (1 derrière le Tesi, 1 derrière le sèche-serviettes, 3 Acova)
  • 5x Sondes Shelly H&T Gen3 / BLU H&T (1 palier + 1 SDB + 3 chambres)

====================================================================================
  CÔTÉ SERVEUR (Sur votre réseau local)
====================================================================================
  • Votre Odroid-C2 (eMMC) sous Arch Linux :
    ├── TVHeadend (en natif pour votre Digibit R1)
    └── Podman -> Home Assistant Container
                  ├── Intégration Météo-France (température extérieure)
                  ├── Intégration BTHome (uniquement si sondes BLU H&T)
                  └── HACS -> Intégration "Versatile Thermostat" (algorithme TPI)
```

---

### 2. Liste d'Achat Complète (Matériel & Prix vérifiés en € TTC)

#### A. Les 6 Radiateurs IRSAP Neufs (5 Tesi + 1 Sèche-serviettes Salle de bain)
*(Prix vérifiés dans le **[Tarif Officiel IRSAP France 2026 PDF](https://www.irsap.com/fr/assistance/documento/53/4151/download)**, hors taxes + TTC avec TVA 20 % et éco-participation de 1,75 € HT / 2,10 € TTC, suivis du prix net remisé revendeur habituel de -25 % à -35 %. En finition **Couleur / Noir Mat `K1`**, le supplément officiel IRSAP est de **+25 %** sur le tarif Blanc `01`).*

* **5x [IRSAP Tesi 3 Électrique Allège — SANS RÉGULATION (Type S)](https://www.irsap.com/fr/heat/radiateur/tesi-2-3-electrique)** ([Fiche technique officielle PDF FR — tableau « TESI ALLÈGE SANS RÉGULATION » p. 5](https://www.irsap.com/resources/images/products/technical_documents/FR/TESI_ELETTRICO.pdf) | [Tarif Officiel France 2026 p. 301](https://www.irsap.com/fr/assistance/documento/53/4151/download) | [Notice officielle Type S sans régulation](https://www.irsap.com/fr/assistance/documento/48/7837/download) | [Certificat UE Tesi ES](https://www.irsap.com/fr/assistance/documento/239/7904/download) — Hauteur 602 mm, Profondeur 101 mm, Classe II, IP24, câble de 1200 mm 2 fils sans prise ni fil pilote) :
  * **2x en 1000 W** (**Cuisine** + **Palier** — 15 éléments, largeur 703 mm, 32 kg) : Réf. exacte sans régulation **`RT 3 0600 15 [Code Couleur] IR SRN`** *(ex. `RT 3 0600 15 01 IR SRN` en Blanc, `RT 3 0600 15 K1 IR SRN` en Noir Mat)*
    * **Tarif Officiel IRSAP France 2026 (p. 301) :**
      * **Blanc `01` :** **835,00 € HT** (**1 004,10 € TTC** tarif public) → **~650 à 750 € TTC/unité** après remise revendeur (**~1 300 à 1 500 € TTC pour les 2**).
      * **Couleur / Noir Mat `K1` (+25 %) :** **1 043,75 € HT** (**1 254,60 € TTC** tarif public) → **~815 à 940 € TTC/unité** remisé.
  * **3x en 1500 W** (**Salle** + **Salon** + **Bureau** — 21 éléments, largeur 973 mm, 44 kg ; *1500 W est le palier nominal IRSAP pour vos emplacements de 1550 W*) : Réf. exacte sans régulation **`RT 3 0600 21 [Code Couleur] IR SVN`** *(ex. `RT 3 0600 21 01 IR SVN` en Blanc, `RT 3 0600 21 K1 IR SVN` en Noir Mat)*
    * **Tarif Officiel IRSAP France 2026 (p. 301) :**
      * **Blanc `01` :** **1 025,00 € HT** (**1 232,10 € TTC** tarif public) → **~800 à 920 € TTC/unité** après remise revendeur (**~2 400 à 2 760 € TTC pour les 3**).
      * **Couleur / Noir Mat `K1` (+25 %) :** **1 281,25 € HT** (**1 539,60 € TTC** tarif public) → **~1 000 à 1 155 € TTC/unité** remisé (**~3 000 à 3 465 € TTC pour les 3**).
  *(Pour référence si besoin, le modèle 1250 W sans régulation, 18 éléments, largeur 838 mm, Réf. `RT 3 0600 18 [Code Couleur] IR SUN` : 940,00 € HT / 1 130,10 € TTC tarif public en Blanc `01`, 1 175,00 € HT / 1 412,10 € TTC en Couleur).*

* **1x Sèche-serviettes IRSAP 750 W (ou 500 W) pour la Salle de bain :**
  * **Point d'attention catalogue France vs International ([Tarif France 2026 p. 414](https://www.irsap.com/fr/assistance/documento/53/4151/download)) :**
    * Les 3 sèche-serviettes asymétriques (`FUNKY_S`, `SOUL_S`, `JAZZ_S`) existent bien en **version S sans régulation** dans les fiches techniques internationales 2026 ([Notice élément chauffant S sans prise, IP64](https://www.irsap.com/en/support-en/documento/48/7831/download) | [Tableau Ecodesign ES](https://www.irsap.com/en/support-en/documento/48/7834/download)), mais le **Tarif France 2026** (p. 414) ne liste en stock « Sans Régulation » que le **Tesi** et le sèche-serviettes **[`PAGE Électrique`](https://www.irsap.com/fr/heat/radiateur/page-electrique)** (et vend les asymétriques en version `DIGITAL` avec fil pilote, code `G..A4`).
    * **Si votre revendeur peut commander la référence internationale Type S (sans régulation, IP64)**, utilisez les codes `S .. IR 01 NNN` ci-dessous. **S'il ne peut commander que la référence du Tarif France (`G .. A4 01 NNN`, avec thermostat digital + fil pilote, IP44)**, elle fonctionne aussi parfaitement avec le `Shelly 1PM Gen4` (réglée en mode Confort permanent à consigne haute, ou via fil pilote + diode comme vos Acova) :
  * **Choix 1 — [`IRSAP FUNKY_S`](https://www.irsap.com/en/heat/radiator/funky-s-electric)** *(tubes ronds Ø 23 mm + collecteurs ronds Ø 30 mm, le plus assorti aux tubes ronds des Tesi)* :
    * [Fiche PDF Version S (sans régulation, p. 4)](https://www.irsap.com/resources/images/products/technical_documents/EN/FUNKY_S_ELETTRICO.pdf) | [Certificat UE Funky_S ES](https://www.irsap.com/en/support-en/documento/239/7910/download) | [Fiche PDF FR (version Digital A4)](https://www.irsap.com/resources/images/products/technical_documents/FR/FUNKY_S_ELETTRICO_FUNKY_S_BOOSTER_ELETTRICO.pdf) | [Tarif France 2026 p. 336](https://www.irsap.com/fr/assistance/documento/53/4151/download)
    * En **750 W** (H 1455 × L 600 × P 50 mm, 27 tubes, 21,6 kg) :
      * Réf. **Sans régulation (Type S)** : **`YRL060 S [Code Couleur] IR 01 NNN`** *(ou Réf. Tarif France Digital : `YR L 060G [Code Couleur] A4 01 NNN`)*
      * **Tarif Officiel France 2026 (p. 336) :** **603,60 € HT / 726,42 € TTC** en Blanc `01` (**~470 à 545 € TTC** remisé) ; **754,50 € HT / 907,50 € TTC** en Couleur `K1` (+25 %).
    * En **500 W** (H 1170 × L 500 × P 50 mm, 22 tubes, 15,3 kg) : Réf. Type S **`YRM050 S [Code Couleur] IR 01 NNN`** *(ou Tarif FR `YR M 050G .. A4 01 NNN`)* — **507,00 € HT / 610,50 € TTC** en Blanc `01` (**~395 à 460 € TTC** remisé).
  * **Choix 2 — [`IRSAP SOUL_S`](https://www.irsap.com/fr/heat/radiateur/soul-s-electrique)** *(tubes plats 50 × 10 mm + collecteurs ronds Ø 30 mm)* :
    * [Fiche PDF Version S (sans régulation, p. 4)](https://www.irsap.com/resources/images/products/technical_documents/EN/SOUL_S_ELETTRICO.pdf) | [Fiche PDF FR (version Digital A4)](https://www.irsap.com/resources/images/products/technical_documents/FR/SOUL_S_ELETTRICO_SOUL_S_BOOSTER_ELETTRICO.pdf) | [Tarif France 2026 p. 330](https://www.irsap.com/fr/assistance/documento/53/4151/download)
    * En **750 W** (H 1540 × L 550 × P 38 mm, 20,7 kg) :
      * Réf. **Sans régulation (Type S)** : **`URM055 S [Code Couleur] IR 01 NNN`** *(ou Réf. Tarif France Digital : `UR M 055G [Code Couleur] A4 01 NNN`)*
      * **Tarif Officiel France 2026 (p. 330) :** **584,00 € HT / 702,90 € TTC** en Blanc `01` (**~455 à 530 € TTC** remisé) ; **730,00 € HT / 878,10 € TTC** en Couleur `K1` (+25 %).
    * En **500 W** (H 1176 × L 550 × P 38 mm, 15,9 kg) : Réf. Type S **`URS055 S [Code Couleur] IR 01 NNN`** *(ou Tarif FR `UR S 055G .. A4 01 NNN`)* — **536,60 € HT / 646,02 € TTC** en Blanc `01` (**~420 à 485 € TTC** remisé).
  * **Choix 3 — [`IRSAP JAZZ_S`](https://www.irsap.com/fr/heat/radiateur/jazz-s-electrique)** *(tubes rectangulaires 25 × 20 mm + collecteurs carrés 30 × 30 mm)* :
    * [Fiche PDF Version S (sans régulation, p. 4)](https://www.irsap.com/resources/images/products/technical_documents/EN/JAZZ_S_ELETTRICO.pdf) | [Fiche PDF FR (version Digital A4)](https://www.irsap.com/resources/images/products/technical_documents/FR/JAZZ_S_ELETTRICO_JAZZ_S_BOOSTER_ELETTRICO.pdf) | [Tarif France 2026 p. 326](https://www.irsap.com/fr/assistance/documento/53/4151/download)
    * En **750 W** (H 1460 × L 600 × P 55 mm, 25,1 kg) :
      * Réf. **Sans régulation (Type S)** : **`ZRL060 S [Code Couleur] IR 01 NNN`** *(ou Réf. Tarif France Digital : `ZR L 060G [Code Couleur] A4 01 NNN`)*
      * **Tarif Officiel France 2026 (p. 326) :** **771,10 € HT / 927,42 € TTC** en Blanc `01` (**~600 à 695 € TTC** remisé) ; **963,88 € HT / 1 158,76 € TTC** en Couleur `K1` (+25 %).
    * En **500 W** (H 1260 × L 500 × P 55 mm, 19,0 kg) : Réf. Type S **`ZRM050 S [Code Couleur] IR 01 NNN`** *(ou Tarif FR `ZR M 050G .. A4 01 NNN`)* — **722,10 € HT / 868,62 € TTC** en Blanc `01` (**~565 à 650 € TTC** remisé).
  * **Choix 4 (100 % stock Tarif France en version S sans régulation) :**
    * Soit un **[`Tesi 2 Vertical 750 W Sans Régulation`](https://www.irsap.com/fr/heat/radiateur/tesi-2-3-electrique)** (H 1802 × L 388 × P 65 mm, Réf. **`RT 2 1800 08 [Code Couleur] IR SNN`**, **645,00 € HT / 776,10 € TTC** tarif public p. 299, soit **~500 à 580 € TTC** remisé) équipé de 1 ou 2 barres porte-serviettes IRSAP **`TUBE 18`** (L 350 mm, Réf. **`BTB3527IRE [Code Couleur]`**, **81,00 € HT / 97,20 € TTC** tarif public p. 400).
    * Soit le sèche-serviettes symétrique **[`IRSAP PAGE Électrique Sans Régulation`](https://www.irsap.com/fr/heat/radiateur/page-electrique)** (750 W, H 1770 × L 500 × P 11 mm, IP64, Réf. **`PG L 050S [Code Couleur] IR 01 NNN`**, **985,00 € HT / 1 184,10 € TTC** tarif public p. 345).
  *(Pour les asymétriques `YR`/`UR`/`ZR` = collecteurs à droite ; remplacez le `R` par `L` pour collecteurs à gauche : `YL`/`UL`/`ZL`).*

#### B. Les Modules Encastrés et Sondes Shelly (Prix officiels Shelly Europe & revendeurs UE en € TTC)
* **9x [`Shelly 1PM Gen4`](https://www.shelly.com/products/shelly-1pm-gen4-1)** ([Documentation officielle](https://www.shelly.com/blogs/documentation/shelly-1pm-gen4) | [Comparateur de prix UE](https://www.hoteudeals.com/p/shelly-1pm-gen4-wifi-zigbee-relae-362221) — 16 A max à 240 V, avec mesure de consommation en Watts) :
  * Se glissent directement dans la boîte murale (sortie de câble) derrière les 5 Tesi (cuisine, salle, salon, bureau, palier), le sèche-serviettes de la salle de bain et les 3 Acova des chambres à l'étage.
  * **Prix vérifié :** **42,90 € TTC le pack de 2** (et **21,90 € TTC à l'unité**) sur la boutique officielle [Shelly Europe](https://www.shelly.com/products/shelly-1pm-gen4-1) (soit **193,50 € TTC pour les 9** avec 4 packs de 2 + 1 unité, livraison gratuite dès 79 €), ou de **17,00 € à 22,00 € TTC/unité** chez les revendeurs européens (**~153 à 194 € TTC pour les 9**).
  * **Note importante — Cas où le [`Shelly Pro 1PM`](https://www.shelly.com/products/shelly-pro-1pm) (rail DIN au tableau, 75,90 € TTC sur Shelly Europe / ~55–68 € chez les revendeurs, [Documentation](https://us.shelly.com/blogs/documentation/shelly-pro-1pm)) peut être inévitable :**
    * Selon le **groupement et le câblage physique réel** de vos radiateurs (par exemple si les radiateurs de la pièce de vie sont repiqués ensemble sur un même départ `C16` avec des boîtes murales trop encombrées par les ponts de repiquage ou trop peu profondes, ou si un câble est inaccessible), **placer un `Shelly Pro 1PM` directement sur le rail DIN du tableau électrique (avec câble Ethernet RJ45) peut s'avérer inévitable** à la place des `1PM Gen4` encastrés de ce circuit.
    * **Condition électrique impérative :** le `Shelly Pro 1PM` est lui aussi limité à **16 A max (~3 680 W)** sur un disjoncteur **16 A max**. Il convient donc en direct si le disjoncteur `C16` regroupe **Salle (1500 W) + Salon (1500 W) = 3000 W (~13,0 A)** ou **Cuisine (1000 W) + 1 radiateur 1500 W = 2500 W (~10,9 A)**, mais **pas** en direct si les **3 radiateurs de la pièce de vie (Cuisine 1000 W + Salle 1500 W + Salon 1500 W = 4000 W, ~17,4 A)** ou les **4 radiateurs du RDC (5500 W, ~23,9 A)** sont sur un même départ `C20` / `C25` (au-delà de 16 A, le Shelly au tableau devra piloter la bobine d'un contacteur modulaire 20 A / 25 A).
* **Les 7 Sondes de Température sans fil (1 Cuisine/Salon + 1 Bureau + 1 Salle de bain + 1 Palier + 3 Chambres — ou 6 si le bureau est groupé avec le salon) :**
  * **Option 1 — Wi-Fi avec écran E-Ink : [`Shelly H&T Gen3`](https://www.shelly.com/products/shelly-h-t-gen3-matte-black)** ([Documentation FR](https://www.shelly.com/fr/blogs/documentation/shelly-h-t-gen3) | [Comparateur UE](https://www.hoteudeals.com/p/shelly-ht-gen3-wifi-humidity-temperature-sensor-matt-black-342879)) :
    * **Prix vérifié :** **37,90 € TTC/unité** sur Shelly Europe (et de **31,60 € à 38,00 € TTC** chez les revendeurs UE) → **~221 à 265 € TTC pour 7 sondes** (ou ~190 à 227 € pour 6).
    * **Sur USB-C** (chargeur non fourni) : envoie une mesure toutes les 5 min → idéal pour la régulation.
    * **Sur piles (4x AA)** : envoie seulement si la température varie de 0,5 °C (seuil par défaut), sinon au moins une fois toutes les 2 h → fonctionne, mais régulation moins fine (voir § 4).
  * **Option 2 — Bluetooth avec écran E-Paper : [`Shelly BLU H&T Display ZB`](https://www.shelly.com/products/shelly-blu-h-t-display-zb-black)** ([Documentation](https://www.shelly.com/blogs/documentation/shelly-blu-h-t-display-zb)) :
    * **Prix vérifié :** **24,90 € TTC/unité** sur Shelly Europe → **174,30 € TTC pour 7 sondes** (ou 149,40 € pour 6). Fonctionne sur pile CR2477 (autonomie ~2 ans) et remonte via le relais Bluetooth des Shelly 1PM Gen4 (**BTHome**).
  * **Option 3 — Bluetooth miniature sans écran (étanche IP54) : [`Shelly BLU H&T`](https://www.shelly.com/products/shelly-blu-h-t-zb-black)** ([Documentation](https://www.shelly.com/blogs/documentation/shelly-blu-h-t) | [Comparateur UE](https://www.hoteudeals.com/p/shelly-blu-ht-zb-ivory-bluetooth-zigbee-temp-luftfugtighedssensor-560392)) :
    * **Prix vérifié :** **18,15 € à 21,00 € TTC/unité** → **~127 à 147 € TTC pour 7 sondes** (ou ~109 à 126 € pour 6). Émet toutes les 1 min via **BTHome** (les Shelly Gen4 servant de relais Bluetooth).
  * *(Optionnel pour le salon)* : **1x [`Shelly Wall Display + sonde BLU H&T incluse`](https://www.shelly.com/products/shelly-wall-display-white)** ([Présentation](https://www.shelly.com/pages/wall-display)) : **131,90 € TTC** sur Shelly Europe (remplace la sonde du salon s'il est choisi ; version grand écran `Wall Display X2i` à ~158–177 € TTC).

#### C. Petit matériel électrique (Pour les 9 boîtes murales)
* **1x boîte de borniers `Wago 221-413`** (format compact, 3 entrées) + 2 m de fil silicone 1,5 mm² ou 2,5 mm² (Bleu et Rouge) + embouts de câblage, pour faire les petits ponts de 10 cm dans les boîtes murales : **~15 à 20 € TTC**.
  * Isolant résistant à la chaleur : la notice Shelly **recommande au minimum PVC T105 °C**. Le fil rigide courant (H07V-U) n'est donné que pour 70 °C → pour ces ponts, prenez du fil silicone (H05SJ-K, 180 °C) avec embouts de câblage.
  * Section : la notice imprimée accepte 0,2 à 2,5 mm² par borne (la fiche en ligne annonce jusqu'à 4 mm² : restez à 2,5 mm² max), et **un seul fil par borne**.
* **Boîtes d'encastrement profondes** (≥ 40–50 mm, ~2 à 4 €/unité) si les vôtres sont trop justes : le Shelly mesure 37 × 42 × 16 mm et doit rester sous 40 °C ambiant.
  * **Attention à la chaleur :** la boîte est juste derrière un radiateur à fluide qui chauffe le mur, et le Shelly y fait passer jusqu'à ~6,5 A en continu (1500 W — ou ~6,7 A si 1550 W ; ~4,3 A à 1000 W). **Relevez la température interne du Shelly en pleine chauffe** les premiers jours. Si le Shelly signale l'erreur `overtemp` (sa protection coupe alors la sortie) ou si sa température ne se stabilise pas, déplacez le Shelly dans une boîte voisine ou une boîte de dérivation à l'écart du radiateur.
* *(En option, uniquement si besoin a posteriori pour l'étage)* : **3x diodes `1N4007`** (ou 3 diodes fil pilote précâblées) : **1 € à 9 € TTC**.

#### D. Récapitulatif du Budget Total (en € TTC)

| Poste | Quantité | Tarif Public Officiel TTC | Prix remisé estimé (-25 à -35 % TTC) |
|---|---|---|---|
| **IRSAP Tesi 3 (1000 W, sans régulation `IR SRN`)** — Cuisine + Palier *(Blanc `01`)* | 2 | 2 × 1 004,10 € = 2 008,20 € | **~1 300 à 1 500 €** |
| **IRSAP Tesi 3 (1500 W, sans régulation `IR SVN`)** — Salle + Salon + Bureau *(Blanc `01`)* | 3 | 3 × 1 232,10 € = 3 696,30 € | **~2 400 à 2 760 €** |
| **Sèche-serviettes IRSAP (750 W)** — Salle de bain *(Blanc `01`, selon modèle)* | 1 | 702,90 à 927,42 € | **~455 à 695 €** |
| **Modules `Shelly 1PM Gen4`** *(tous les 9 radiateurs)* | 9 | 193,50 € *(Shelly Europe)* | **153 à 194 €** |
| **Sondes de température** *(7 zones : BLU H&T / BLU Display / H&T Gen3)* | 7 | 147 à 265 € | **127 à 265 €** |
| **Petit matériel électrique** *(Wago 221, fil silicone T180°C, embouts)* | 1 lot | 15 à 20 € | **15 à 20 €** |
| **TOTAL COMPLET (Radiateurs Blanc `01` + Domotique Shelly)** | — | **6 763 à 7 110 € TTC** *(tarif public)* | **~4 450 à 5 434 € TTC** *(prix remisé)* |
| *(Dont sous-total Domotique Shelly + câblage seul, hors radiateurs)* | — | — | *(~295 à 479 € TTC)* |

---

### 3. Le Branchement dans chacune des 9 boîtes murales

**Prérequis tableau électrique** (installation neuve, triphasé 12 kVA) :
* **Un circuit 16 A par radiateur (ou par groupe ≤ 3 680 W)** → conforme à l'exigence de la notice Shelly (disjoncteur EN 60898-1, **courbe B ou C, 16 A maximum**). Si le câblage physique regroupe deux radiateurs sur un même disjoncteur `C16` (ex. Salle 1500 W + Salon 1500 W = 3000 W, ou Cuisine 1000 W + 1× 1500 W = 2500 W) avec un repiquage empêchant de loger les modules dans les boîtes murales, un **[`Shelly Pro 1PM`](https://www.shelly.com/products/shelly-pro-1pm) sur rail DIN au tableau** deviendra inévitable pour ce circuit (ou un contacteur modulaire commandé par le Shelly si le circuit regroupe > 3 680 W sur un `C20`, comme Cuisine + Salle + Salon = 4000 W). En salle de bain, le sèche-serviettes (Classe II, IP64 en version S) et sa boîte de sortie de câble doivent être installés en **Volume 2** ou **Hors Volume** (jamais en Volume 0 ou 1) conformément à la NF C 15-100.
* **Pouvoir de coupure :** vos disjoncteurs sont des **Schneider Resi9 1P+N C16** : 3 kA (Icn 3000 A selon EN 60898-1, classe de limitation 3, d'après la fiche Schneider de la R9EFC616 ; la version peignable R9PFC616 est identique). C'est **conforme à la NF C 15-100**, qui se contente de 3 kA sur un branchement Enedis à puissance limitée, les fusibles AD en amont limitant le courant de court-circuit. La notice Shelly demande en plus **≥ 6 kA** : sur ce point précis, vos disjoncteurs ne la respectent pas. Ce n'est pas un défaut de votre installation. Les Resi9 C16 (XE comme XP) sont en 3 kA : pour être strictement conforme à la notice, il faudrait passer les circuits des radiateurs sur une gamme 6 kA (ex. Schneider **Acti9 iDT40N**, marquée 6000 A), en faisant vérifier par l'électricien la compatibilité avec votre tableau Resi9 (peigne, répartiteur XE).
* **Limite par phase :** en triphasé 12 kVA, le disjoncteur de branchement Enedis est réglé à **20 A par phase**, soit ~4,6 kW par phase. Il coupe dès qu'**une** phase dépasse, même si les deux autres sont peu chargées. Puissance totale de vos 9 radiateurs : 6 × 1500 W (3 Acova + Salle + Salon + Bureau) + 2 × 1000 W (Cuisine + Palier) + 750 W (Salle de bain, ou 500 W) = **11,75 kW en tout** (~51,1 A cumulés ; *11,85 kW / ~51,5 A si l'on compte 2 × 1550 W*).
  * **Attention : avec 11,75 kW de chauffage pour 12 kVA d'abonnement triphasé (3 × 4,6 kW), l'équilibrage des phases et le délestage deviennent indispensables !**
  * **Notez sur quelle phase (L1/L2/L3) est chaque circuit radiateur** : sur le schéma du tableau ou en regardant le peigne. Trois radiateurs de 1500 W sur la même phase (4,5 kW, ~19,6 A) saturent déjà à eux seuls la limite de 20 A (4,6 kW) de cette phase ! La **répartition idéale des 9 radiateurs** sur les 3 phases est :
    * **Phase 1 :** 2 × 1500 W + 1 × 1000 W (Cuisine) = **4,0 kW** (~17,4 A — marge restante ~600 W)
    * **Phase 2 :** 2 × 1500 W + 1 × 1000 W (Palier) = **4,0 kW** (~17,4 A — marge restante ~600 W)
    * **Phase 3 :** 2 × 1500 W + 1 × 750 W (Salle de bain) = **3,75 kW** (~16,3 A — marge restante ~850 W)
    *(Astuce : répartissez aussi les 3 radiateurs de la pièce de vie — Cuisine 1000 W, Salle 1500 W, Salon 1500 W — sur les 3 phases différentes pour qu'une demande de chauffe du RDC ne charge jamais une seule phase).*
  * Le Shelly mesure la tension et l'intensité : comparez les courbes de tension des 9 Shelly dans Home Assistant (les radiateurs sur la même phase ont des courbes quasi identiques) pour vérifier la répartition sans ouvrir le tableau.
  * **Délestage quasi obligatoire (ou passage à 15 kVA) :** même avec une répartition parfaite, chaque phase est chargée à 3,75–4,0 kW en pleine chauffe (il ne reste que 600 à 850 W de marge par phase pour le four, les plaques, le chauffe-eau, le lave-linge…). Activez impérativement le **délestage de Versatile Thermostat** (*configuration centrale → Gestion de la puissance*) — et profitez de l'étalement des cycles TPI entre les 3 radiateurs de la pièce de vie. Il faut un capteur de **consommation** et un capteur de **puissance maximale** (`input_number`). VT ne compare qu'une seule consommation à un seul maximum, pas phase par phase : donnez-lui la **puissance de la phase la plus chargée** (un module lisant la prise TIC du Linky fournit l'intensité par phase) et un maximum de ~4 kW (4,6 kW moins une marge). Ce n'est **pas une sécurité**, juste une optimisation : la protection reste assurée par le disjoncteur de branchement.

Derrière chaque radiateur (les 5 Tesi, le sèche-serviettes IRSAP et les 3 Acova), vous faites exactement le même branchement :

```
[MUR : Boîte d'encastrement]                 [Shelly 1PM Gen4]             [CÂBLE DU RADIATEUR]
                                           ┌───────────────────┐
• Fil Noir (Fil pilote) -> (Isolé Wago)    │                   │           • Fil Noir (Fil pilote, Acova uniquement) -> (Isolé Wago)
• Fil Vert/Jaune (Terre) -> (Isolé Wago)   │                   │             (classe II : pas de terre ; Tesi type S : 2 fils seulement)
• Fil Rouge (Phase 230V) ─────────────────►│ L (Phase entrée)  │
                                           │                   │
                                           │ O (Sortie 230V)   ├─────────► • Fil Marron (Phase radiateur)
                                           │                   │
• Fil Bleu (Neutre) ──────► [Wago 3] ─────►│ N (Neutre Shelly) │
                               │           └───────────────────┘
                               └─────────────────────────────────────────► • Fil Bleu (Neutre radiateur)
```
*(Gardez le Wago pour le neutre : la notice Shelly prévoit que le neutre de la charge rejoigne le fil de neutre, pas qu'il transite par le pont interne entre les bornes `N`. Avec ~6,5 A en continu, le Wago est le choix sûr).*

*(Acova : fil pilote isolé = mode Confort permanent, c'est le Shelly qui coupe/remet la phase. Tesi type S : pas de fil pilote — à confirmer sur la notice ou le câble du radiateur).*

**Avant de brancher :** les couleurs des fils au mur (rouge = phase, noir = fil pilote) sont supposées : identifiez-les au VAT (vérificateur d'absence de tension).

**Avant de raccrocher chaque radiateur :** vérifiez dans Home Assistant le signal Wi-Fi (RSSI) du Shelly — le radiateur en acier devant la boîte atténue fortement le signal (et le Bluetooth pour les BLU H&T).

---

### 4. Récapitulatif de la configuration Logicielle (Odroid-C2)

1. **Sous Arch Linux (eMMC) :**
   * Vous gardez votre **TVHeadend** en natif comme avant.
   * Vous installez Podman (`pacman -S podman`) et lancez Home Assistant :
     ```bash
     sudo podman run -d --name homeassistant --privileged --restart=always \
       -e TZ=Europe/Paris -v /home/user/ha_config:/config \
       -v /run/dbus:/run/dbus:ro --network=host \
       ghcr.io/home-assistant/home-assistant:stable
     sudo systemctl enable podman-restart.service
     ```
     *(Avec Podman, `--restart=unless-stopped` ne relance **pas** le conteneur après un redémarrage de l'Odroid : seul `always` est relancé par `podman-restart.service`. Le conteneur est lancé en **root** (`sudo`) : le service système ne relance que les conteneurs root (en rootless, il faudrait `systemctl --user enable podman-restart.service` + `sudo loginctl enable-linger $USER`). Alternative plus propre : une unité Quadlet `.container`).*

2. **Sur chaque `Shelly 1PM Gen4` (interface web locale) :**
   * **État au démarrage** : `Off`.
   * **Auto-off** (ex. 20 min) en filet de sécurité : si Home Assistant plante pendant une chauffe, le radiateur se coupe tout seul. Indispensable pour les Tesi **sans régulation** (pas de thermostat d'ambiance). *À tester : vérifier que chaque nouvel ordre « On » de Versatile Thermostat relance bien le décompte.* **Plan B si le test échoue :** par grand froid (demande à 100 %), le radiateur serait coupé toutes les 20 min → passez l'auto-off à 60 min ou plus (filet de sécurité moins serré, mais pas de coupure intempestive).
   * *(Les Acova à thermostat mécanique réglé au maximum gardent leur propre limite haute et leur réglage après coupure).*
   * Les deux réglages en une commande (API locale du Shelly) :
     ```bash
     curl -s -X POST http://IP_DU_SHELLY/rpc -d '{"id":1,"method":"Switch.SetConfig","params":{"id":0,"config":{"initial_state":"off","auto_off":true,"auto_off_delay":1200}}}'
     ```

3. **Dans Home Assistant :**
   * Vos **9x `Shelly 1PM Gen4`** : connectez d'abord chacun au Wi-Fi **2,4 GHz** (app Shelly, ou point d'accès du Shelly sur `http://192.168.33.1`) ; ils sont ensuite découverts automatiquement en local.
   * **Sondes `H&T Gen3`** : appuyez sur le bouton (sous le capot) pour les réveiller pendant l'ajout. Si elles ne remontent pas, activez dans leur interface web *Settings → Connectivity → Outbound WebSocket* avec `ws://IP_DE_L_ODROID:8123/api/shelly/ws`.
   * **Sondes `BLU H&T`** (si choisies) : dans les options de l'intégration Shelly de chaque Shelly 1PM, réglez **Bluetooth scanner mode** sur « Auto », puis ajoutez les sondes via **BTHome** (l'intégration Shelly ne gère pas les BLU H&T ; clé de chiffrement éventuelle depuis l'app Shelly).
   * Ajoutez l'intégration **Météo-France** puis **activez son entité `temperature`** (désactivée par défaut : *Paramètres → Appareils et services → Météo-France → entités → afficher les entités désactivées*). Versatile Thermostat a besoin d'une **température extérieure** (sinon il passe en mode sécurité).
     * Météo-France dépend d'internet : pour qu'une coupure internet ne mette pas vos thermostats en sécurité, ajoutez dans `configuration.yaml` puis redémarrez Home Assistant :
       ```yaml
       versatile_thermostat:
         safety_mode:
           check_outdoor_sensor: false
       ```
   * Vous installez **HACS** (en version Container : `sudo podman exec -it homeassistant bash`, puis `wget -O - https://get.hacs.xyz | bash -`, redémarrez Home Assistant, ajoutez l'intégration HACS et liez votre compte GitHub), puis **`Versatile Thermostat`** (algorithme **TPI** intégré, ou le plugin **SmartPI**, qui apprend l'inertie de la pièce).
     * SmartPI est une intégration séparée (HACS → « Versatile Thermostat SmartPI ») qui exige **Versatile Thermostat ≥ 10.6.2**. Après l'installation : ajoutez-la dans *Paramètres → Intégrations*, puis choisissez SmartPI comme algorithme à l'étape *Sous-jacents* de chaque thermostat (compatible `Over Switch`). Avec une sonde qui remonte rarement (H&T Gen3 sur piles), son apprentissage initial est plus long.
   * **Pour la Pièce de vie (RDC) :** Vous créez 1 thermostat virtuel (`Over Switch`) qui regroupe la sonde du salon + les **3 `Shelly 1PM Gen4` de la Cuisine (1000 W), de la Salle (1500 W) et du Salon (1500 W)** *(ou les 4 du RDC avec le Bureau 1500 W si l'espace est ouvert et que vous voulez une consigne unique)*. Un seul curseur de température pilote alors le groupe (Versatile Thermostat décale automatiquement les allumages des 3 ou 4 radiateurs dans le cycle TPI pour lisser la puissance appelée).
   * **Pour le Bureau (1500 W, si séparé), la Salle de bain (750 W), le Palier (1000 W) et les 3 Chambres de l'Étage (3 × 1500 W) :** **1 thermostat virtuel par pièce/zone** (1 sonde + 1 Shelly).
   * **Réglages conseillés dans chaque thermostat :**
     * **Durée de cycle** : 10–15 min (radiateurs à fluide = forte inertie, moins d'usure des relais).
     * **Keep-alive** : 300 s (renvoie régulièrement l'ordre au Shelly).
     * **Délai avant mode sécurité** (`safety_delay_min`) : 60 min par défaut convient aux sondes USB-C et BLU ; montez à 2–4 h pour une H&T Gen3 **sur piles** (préconisation de la doc VT : elle peut rester 2 h sans rien envoyer quand la température est stable). Si la sonde expose un attribut `last_seen`, renseignez-le dans VT : la détection est plus fiable.
   * **Suivi Énergie :** Vous ajoutez les 9 compteurs `kWh` des Shelly dans le tableau de bord *Énergie* de Home Assistant pour suivre la consommation exacte de chaque radiateur. Surveillez aussi la **température interne** de chaque Shelly (capteur intégré).

4. **Option fil pilote avec diode (étage, a posteriori) :**
   * **Principe :** dans la boîte murale, on isole le fil pilote venant du cellier. La phase du radiateur (marron) est reliée **directement** à la phase du mur (Wago 3 entrées : mur + `L` du Shelly + radiateur). La sortie `O` du Shelly est reliée au fil pilote du radiateur (noir) **à travers la diode**. Le Shelly ne commande plus que le fil pilote : **la mesure de consommation du radiateur est perdue**.
   * **Sens de la diode — choisir Hors-gel :** cathode (côté bague) **vers le Shelly**, anode vers le radiateur → seule la demi-alternance négative passe → **Shelly On = Hors-gel**. (À l'envers, bague vers le radiateur → demi-alternance positive → Shelly On = Arrêt.) Hors-gel est la meilleure position de repli : pas de surchauffe, et pas de gel si Home Assistant reste en panne plusieurs jours.
   * **Shelly Off = aucun signal = Confort** : c'est l'état « chauffe ». La logique de sécurité s'inverse donc par rapport au montage principal :

     | | Montage principal (Shelly coupe la phase) | Montage diode |
     |---|---|---|
     | Shelly On | chauffe | Hors-gel |
     | Shelly Off | arrêt | chauffe (Confort) |
     | État au démarrage | `Off` | **`On`** |
     | Minuteur de sécurité | Auto-off 20 min | **Auto-on 20 min** (auto-off désactivé) |
     | Versatile Thermostat | normal | **« Inverser la commande »** coché |

   * **Réglage du Shelly** (interface web, réglages de la sortie, ou en une commande) :
     ```bash
     curl -s -X POST http://IP_DU_SHELLY/rpc -d '{"id":1,"method":"Switch.SetConfig","params":{"id":0,"config":{"initial_state":"on","auto_off":false,"auto_on":true,"auto_on_delay":1200}}}'
     ```
   * **Comportement obtenu :** Home Assistant plante pendant une chauffe (Shelly Off) → 20 min plus tard l'auto-on remet le Shelly On → Hors-gel. Plantage pendant une pause → reste en Hors-gel. Coupure de courant → redémarrage en On → Hors-gel jusqu'au retour de Home Assistant.
   * **Même test qu'au § 4.2 :** vérifier que chaque nouvel ordre « Off » de Versatile Thermostat (keep-alive) relance le décompte de l'auto-on ; sinon, par grand froid, la chauffe serait interrompue toutes les 20 min → passez l'auto-on à 60 min ou plus.
   * **Test à la mise en service :** Shelly On → le radiateur doit passer en Hors-gel ; Shelly Off → Confort. À faire sur chaque Acova, la réaction de leur fil pilote n'étant pas documentée ici.
