---
title: "SOMED-geo project"
subtitle: "Geocoding SOMED data"
description: |
  Geocoding BAG data using two providers.
date: "2021-02-23"
author:
  - name: Radoslaw Panczak 
    url: https://github.com/RPanczak
    affiliation: ISPM
    affiliation_url: https://www.ispm.unibe.ch/
    orcid_id: 0000-0001-5141-683X
# bibliography: biblio.bib
output:
  distill::distill_article:
    highlight: pygments
    toc: true
    toc_depth: 1
    keep_md: yes
editor_options: 
  chunk_output_type: console
---

<!-- ------------------------------------------------------------ --> 



# Addresses 

<div class="layout-chunk" data-layout="l-body">


</div>


Raw file consists of dataset of 1,553 institutions.  

Few example addresses, illustrating one case with no street address given (`NA`).

<div class="layout-chunk" data-layout="l-body">
<table class="table table-striped table-hover table-condensed" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:left;"> institution </th>
   <th style="text-align:left;"> strasse </th>
   <th style="text-align:left;"> ort </th>
   <th style="text-align:left;"> kanton </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:left;font-style: italic;"> PFLEGEHEIM SENNHOF </td>
   <td style="text-align:left;"> ALTE ST.URBANSTRASSE 1 </td>
   <td style="text-align:left;"> 4803 VORDEMWALD </td>
   <td style="text-align:left;"> AG </td>
  </tr>
  <tr>
   <td style="text-align:left;font-style: italic;"> ALTERS- UND PFLEGEHEIM PFAUEN </td>
   <td style="text-align:left;"> PFAUENGASSE 2 </td>
   <td style="text-align:left;"> 5330 BAD ZURZACH </td>
   <td style="text-align:left;"> AG </td>
  </tr>
  <tr>
   <td style="text-align:left;font-style: italic;"> ALTERS- &amp; PFLEGEHEIM </td>
   <td style="text-align:left;"> LINDENSTR. 6 </td>
   <td style="text-align:left;"> 4310 RHEINFELDEN </td>
   <td style="text-align:left;"> AG </td>
  </tr>
  <tr>
   <td style="text-align:left;font-style: italic;"> ALTERS- &amp; PFLEGEHEIM BIFANG </td>
   <td style="text-align:left;"> BIFANGSTR. 8 </td>
   <td style="text-align:left;"> 5610 WOHLEN AG </td>
   <td style="text-align:left;"> AG </td>
  </tr>
  <tr>
   <td style="text-align:left;font-style: italic;"> PFLEGEZENTRUM BARMELWEID </td>
   <td style="text-align:left;"> NA </td>
   <td style="text-align:left;"> 5017 BARMELWEID </td>
   <td style="text-align:left;"> AG </td>
  </tr>
</tbody>
</table>

</div>


# GeoAdmin 

## Info

Working with search service of [GeoAdmin API](http://api3.geo.admin.ch/services/sdiservices.html?highlight=geocode#search). 
It doesn't require API sign up. It does however require 'fair use'. [Comment](https://groups.google.com/g/geoadmin-api/c/T9uHlYD28Hc) from swisstopo staff defined it as staying below 2000 req/hour.

<aside>
Pausing for 2s after each query should do the job in case of working with large dataset.
</aside>

## Addresses with street names

<div class="layout-chunk" data-layout="l-body">


</div>


Using 1,526 addresses that have some information on the name of the street. 




## Results

<div class="layout-chunk" data-layout="l-body">


</div>


1,319 addresses have been geocoded. Unfortunately the dataset consists of  2,793 records since some of the adrresses have multiple entries. 

1,005 addresses have clean, one geocode. 

314 addresses have between 2 or more hits. Mostly these are listing various addresses on same street locations

<div class="layout-chunk" data-layout="l-body">
<table class="table table-striped table-hover table-condensed" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:right;"> link </th>
   <th style="text-align:left;"> attrs_label </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;font-style: italic;"> 5 </td>
   <td style="text-align:left;"> Golattenmattgasse 37 &lt;b&gt;5000 Aarau&lt;/b&gt; </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 5 </td>
   <td style="text-align:left;"> Golattenmattgasse 37.1 &lt;b&gt;5000 Aarau&lt;/b&gt; </td>
  </tr>
</tbody>
</table>

</div>


In such cases first address (with bigger geocoding 'weight') is preserved. 

In extreme cases, where address is imprecise, up to 50 (*sic!*) geocodes can be returned, for instance in case of:

<div class="layout-chunk" data-layout="l-body">
<table class="table table-striped table-hover table-condensed" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:right;"> link </th>
   <th style="text-align:left;"> institution </th>
   <th style="text-align:left;"> strasse </th>
   <th style="text-align:left;"> ort </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;font-style: italic;"> 596 </td>
   <td style="text-align:left;"> ALTERS- &amp; PFLEGEHEIM SERNFTAL </td>
   <td style="text-align:left;"> WIESE </td>
   <td style="text-align:left;"> 8767 ELM </td>
  </tr>
</tbody>
</table>

</div>


These addresses will be geocoded again with alternative method.

<div class="layout-chunk" data-layout="l-body">
<table class="table table-striped table-hover table-condensed" style="width: auto !important; margin-left: auto; margin-right: auto;">
 <thead>
  <tr>
   <th style="text-align:right;"> link </th>
   <th style="text-align:left;"> institution </th>
   <th style="text-align:left;"> strasse </th>
   <th style="text-align:left;"> ort </th>
  </tr>
 </thead>
<tbody>
  <tr>
   <td style="text-align:right;font-style: italic;"> 77 </td>
   <td style="text-align:left;"> ASANA GRUPPE SPITAL LEUGGERN KRANKEN- UND PFLEGEHEIM </td>
   <td style="text-align:left;"> KOMMENDEWEG </td>
   <td style="text-align:left;"> 5316 LEUGGERN </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 123 </td>
   <td style="text-align:left;"> HAUS LINDENBÜHL </td>
   <td style="text-align:left;"> NEUSCHWENDI </td>
   <td style="text-align:left;"> 9043 TROGEN </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 329 </td>
   <td style="text-align:left;"> CHALET STAMPACH PFLEGEWOHNUNG </td>
   <td style="text-align:left;"> ALLEESTR. 165B </td>
   <td style="text-align:left;"> 3703 AESCHI BEI SPIEZ </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 352 </td>
   <td style="text-align:left;"> PFLEGEFAMILIE HOHGANTBLICK </td>
   <td style="text-align:left;"> SCHEIDBACH </td>
   <td style="text-align:left;"> 6197 SCHANGNAU </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 596 </td>
   <td style="text-align:left;"> ALTERS- &amp; PFLEGEHEIM SERNFTAL </td>
   <td style="text-align:left;"> WIESE </td>
   <td style="text-align:left;"> 8767 ELM </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 624 </td>
   <td style="text-align:left;"> OPERA MATER CHRISTI CENTRO ANZIANI </td>
   <td style="text-align:left;"> SCIMA GRON </td>
   <td style="text-align:left;"> 6537 GRONO </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 635 </td>
   <td style="text-align:left;"> ALTERSZENTRUM AROSA </td>
   <td style="text-align:left;"> ALTEINSTRASSE </td>
   <td style="text-align:left;"> 7050 AROSA </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 636 </td>
   <td style="text-align:left;"> PFLEGEZENTRUM GLIENDA </td>
   <td style="text-align:left;"> TRANTER FLIMMA </td>
   <td style="text-align:left;"> 7440 ANDEER </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 646 </td>
   <td style="text-align:left;"> RESIDENZA DELLE ROSE SA </td>
   <td style="text-align:left;"> VIA CANTONALE </td>
   <td style="text-align:left;"> 6537 GRONO </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 667 </td>
   <td style="text-align:left;"> BEGEGNUNGSZENTRUM ST. ULRICH </td>
   <td style="text-align:left;"> INNERMOOS </td>
   <td style="text-align:left;"> 6156 LUTHERN </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 682 </td>
   <td style="text-align:left;"> SONNMATT LUZERN AG RESIDENZ &amp; SENIORENABTEILUNG </td>
   <td style="text-align:left;"> HEMSCHLENSTRASSE </td>
   <td style="text-align:left;"> 6006 LUZERN </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 687 </td>
   <td style="text-align:left;"> ALTERS- &amp; PFLEGEHEIM FLÄCKEMATTE </td>
   <td style="text-align:left;"> FLÄCKEMATTE </td>
   <td style="text-align:left;"> 6023 ROTHENBURG </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 703 </td>
   <td style="text-align:left;"> ALTERS-UND PFLEGEHEIM IBENMOOS </td>
   <td style="text-align:left;"> IBENMOOS </td>
   <td style="text-align:left;"> 6277 KLEINWANGEN </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 708 </td>
   <td style="text-align:left;"> ALTERSWOHNZENTRUM RUSWIL </td>
   <td style="text-align:left;"> SCHLOSSMATTE; POSTFACH 313 </td>
   <td style="text-align:left;"> 6017 RUSWIL </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 759 </td>
   <td style="text-align:left;"> HOME MÉDICALISÉ DU VAL-DE-RUZ </td>
   <td style="text-align:left;"> RTE DE LANDEYEUX </td>
   <td style="text-align:left;"> 2046 FONTAINES NE </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 776 </td>
   <td style="text-align:left;"> CNP - LES THUYAS ET LA RAMÉE </td>
   <td style="text-align:left;"> PRÉFARGIER </td>
   <td style="text-align:left;"> 2074 MARIN-ÉPAGNIER </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 777 </td>
   <td style="text-align:left;"> CNP - LA TÈNE, ACACIAS ET PERNOD </td>
   <td style="text-align:left;"> PRÉFARGIER </td>
   <td style="text-align:left;"> 2074 MARIN-ÉPAGNIER </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 787 </td>
   <td style="text-align:left;"> RESIDENZ AM SCHÄRME </td>
   <td style="text-align:left;"> FLUEELISTRASSE </td>
   <td style="text-align:left;"> 6060 SARNEN </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 884 </td>
   <td style="text-align:left;"> IM HORB WOHNEN IM ALTER </td>
   <td style="text-align:left;"> HORB </td>
   <td style="text-align:left;"> 9656 ALT ST. JOHANN </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1093 </td>
   <td style="text-align:left;"> CASA PER ANZIANI ALTO VEDEGGIO </td>
   <td style="text-align:left;"> VIA LA ROGGIA </td>
   <td style="text-align:left;"> 6805 MEZZOVICO-VIRA </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1120 </td>
   <td style="text-align:left;"> RÉSIDENCE PRAZ-JORET </td>
   <td style="text-align:left;"> RTE DE SERVION </td>
   <td style="text-align:left;"> 1083 MÉZIÈRES VD </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1123 </td>
   <td style="text-align:left;"> EMS LE SIGNAL </td>
   <td style="text-align:left;"> RTE DU SIGNAL </td>
   <td style="text-align:left;"> 1080 LES CULLAYES </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1131 </td>
   <td style="text-align:left;"> EPSM FONDATION CHAMP FLEURI </td>
   <td style="text-align:left;"> RTE DE CHAMP-FLEURI </td>
   <td style="text-align:left;"> 1823 GLION </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1132 </td>
   <td style="text-align:left;"> EMS LES CERISIERS </td>
   <td style="text-align:left;"> RUE DES CERISIERS </td>
   <td style="text-align:left;"> 1530 PAYERNE </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1136 </td>
   <td style="text-align:left;"> FONDATION COMMANDANT BAUD </td>
   <td style="text-align:left;"> RTE DE PAMPIGNY </td>
   <td style="text-align:left;"> 1143 APPLES </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1139 </td>
   <td style="text-align:left;"> EMS LA VEILLÉE SA </td>
   <td style="text-align:left;"> RTE DE VULLIERENS </td>
   <td style="text-align:left;"> 1304 SENARCLENS </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1144 </td>
   <td style="text-align:left;"> EPSM PENSION THONNEY SA </td>
   <td style="text-align:left;"> EN SALAGNON </td>
   <td style="text-align:left;"> 1418 VUARRENS </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1149 </td>
   <td style="text-align:left;"> EMS L'ESCAPADE </td>
   <td style="text-align:left;"> RUE MARTINET </td>
   <td style="text-align:left;"> 1188 GIMEL </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1156 </td>
   <td style="text-align:left;"> EMS LA RÉSIDENCE (DIABLERETS) FONDATION DES MAISONS DE RETRAITE DU DISTRICT D'AIGLE </td>
   <td style="text-align:left;"> RTE DU PILLON </td>
   <td style="text-align:left;"> 1865 LES DIABLERETS </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1168 </td>
   <td style="text-align:left;"> EMS LA GENTILHOMMIÈRE </td>
   <td style="text-align:left;"> CARRA BORRE </td>
   <td style="text-align:left;"> 1145 BIÈRE </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1175 </td>
   <td style="text-align:left;"> EMS LE CHÂTEAU DE CORCELLES </td>
   <td style="text-align:left;"> CLOS CHÂTEAU </td>
   <td style="text-align:left;"> 1426 CORCELLES-PRÈS-CONCISE </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1191 </td>
   <td style="text-align:left;"> FONDATION JOLI-BOIS FONDATION LA PRIMEROSE </td>
   <td style="text-align:left;"> CORNAUX </td>
   <td style="text-align:left;"> 1832 CHAMBY </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1193 </td>
   <td style="text-align:left;"> MAISON D'ACCUEIL PRAZ-SOLEIL </td>
   <td style="text-align:left;"> L'ÉTAMBEAU </td>
   <td style="text-align:left;"> 1660 CHÂTEAU-D'OEX </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1204 </td>
   <td style="text-align:left;"> EMS LA RENAISSANCE SA </td>
   <td style="text-align:left;"> CH. DE LA CÔTE-MALHERBE </td>
   <td style="text-align:left;"> 1188 ST-GEORGE </td>
  </tr>
  <tr>
   <td style="text-align:right;font-style: italic;"> 1264 </td>
   <td style="text-align:left;"> ÉTABLISSEMENT MÉDICO-SOCIAL ZAMBOTTE CASE POSTALE 123 </td>
   <td style="text-align:left;"> GRANOIS </td>
   <td style="text-align:left;"> 1965 SAVIÈSE </td>
  </tr>
</tbody>
</table>

</div>



<div class="layout-chunk" data-layout="l-body">


</div>


Clean dataset at this stage consists of 1,284 addresses. 

<div class="layout-chunk" data-layout="l-body">


</div>


242 addresses failed to be geocoded despite having address and will be attempted with next method. 

# Google

## Info

Working via `ggmap` [package](https://github.com/dkahle/ggmap). 
It requires [API sign up](https://cran.r-project.org/web/packages/ggmap/readme/README.html) 

<aside>
... so please be careful with reruns of large batches of data!
</aside>



## Addresses with incomplete info 

<div class="layout-chunk" data-layout="l-body">


</div>




<div class="layout-chunk" data-layout="l-body">


</div>


Rescued 62 addresses with Google and manual searches.

## Addresses that failed on geoadmin 

<div class="layout-chunk" data-layout="l-body">


</div>




<div class="layout-chunk" data-layout="l-body">


</div>


Rescued 240 addresses with Google and manual searches.

# Combined results

<div class="layout-chunk" data-layout="l-body">


</div>


Source of address:

<div class="layout-chunk" data-layout="l-body">

```

source <character>
# total N=1586  valid N=1586  mean=1.20  sd=0.43

Value    |    N | Raw % | Valid % | Cum. %
------------------------------------------
geoadmin | 1284 | 80.96 |   80.96 |  80.96
google   |  282 | 17.78 |   17.78 |  98.74
manual   |   20 |  1.26 |    1.26 | 100.00
<NA>     |    0 |  0.00 |    <NA> |   <NA>
```

</div>


<div class="layout-chunk" data-layout="l-page">

```{=html}
<div id="htmlwidget-880d8cbf9369760f4f3d" style="width:900px;height:700px;" class="leaflet html-widget"></div>
```

</div>


```{.r .distill-force-highlighting-css}
```