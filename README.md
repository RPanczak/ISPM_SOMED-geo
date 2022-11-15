# ISPM_SOMED-geo

Geocoding data on care facilities in Switzerland. 

Using [BAG data](https://www.bag.admin.ch/bag/de/home/zahlen-und-statistiken/zahlen-fakten-zu-pflegeheimen/kennzahlen.html) on **Kennzahlen der Schweizer Pflegeheime**:

 - ~~[2018 Flat File (Excel, deutsch, 1MB)](https://somed.bagapps.ch/data/download/archiv/2018_Flat_File_de.xlsx?v=1616748312).~~
 
 - [2019 Flat File (Excel, deutsch, 1MB)](https://somed.bagapps.ch/data/download/2019_Flat_File_de.xlsx?v=1616748489). 

([opendata.swiss link](https://opendata.swiss/de/dataset/kennzahlen-der-schweizer-pflegeheime))

This file should present:  

> Die Zahlen basieren auf den definitiven Daten 2019

First round of geocoding using [map.geo.admin.ch](https://map.geo.admin.ch/); second round with Google (via `ggmap` package) plus manual corrections.

![overview](figures/overview.png)

[![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa]

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png