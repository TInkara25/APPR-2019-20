# Analiza podatkov s programom R, 2019/20

# Analiza kriminalitete v Sloveniji

Avtor: Tinkara Žitko

Repozitorij z gradivi pri predmetu APPR v študijskem letu 2019/20

* [![Shiny](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=shiny/APPR-2019-20/projekt.Rmd) Shiny
* [![RStudio](http://mybinder.org/badge.svg)](http://mybinder.org/v2/gh/jaanos/APPR-2019-20/master?urlpath=rstudio) RStudio

## Tematika

V svoji projektni nalogi bom analizirala kriminaliteto v Sloveniji. 

Analizirala bom:
* količino ovadenih, obtoženih in obsojenih fizičnih oseb
* količine primerjala glede na kaznivo dejanje
* primerjala količine glede na sankcije, glavno kazen oziroma varnostni ukrep
* glede na spol in starost (mladletni, polnoletni)
* trende skozi zadnjih 5 let
* količino obsojenih oseb glede na statistične regije Slovenije

Tabele:
* Tabela 1: Obsojeni polnoletni in mladoletni po statističnih regijah - STATISTIČNA REGIJA, OBSOJENI, LETO
* Tabela 2: Obsojeni polnoletni in mladoletni po občinah stalnega prebivališča - OBČINA STALNEGA PREBIVALJIŠČA, OBSOJENI, LETO
* Tabela 3: Obsojene polnoletne osebe - KAZNIVO DEJANJE, GLAVNA KAZEN, SPOL, LETO
* Tabela 4: Obsojene polnoletne osebe - KAZNIVO DEJANJE, VARNOSTNI UKREP, SPOL, LETO
* Tabela 5: Obtožene mladoletne osebe - KAZNIVO DEJANJE, VRSTA ODLOČBE, SPOL, LETO
* Tabela 6: Obtožene polnoletne osebe - KAZNIVO DEJANJE, VRSTA ODLOČBE, SPOL, LETO
* Tabela 7: Ovadene mladoletne osebe - KAZNIVO DEJANJE, VRSTA ODLOČBE, SPOL, STAROST, LETO
* Tabela 8: Ovadene polnoletne osebe - KAZNIVO DEJANJE, VRSTA ODLOČBE, SPOL, STAROST, LETO

Viri:
* https://pxweb.stat.si/SiStatData/pxweb/sl/Data/-/1372202S.px
* https://pxweb.stat.si/SiStatData/pxweb/sl/Data/-/1372201S.px
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__13_kriminaliteta__01_statistika_toz_sodisc__03_13603_obsojene_poln_osebe/1360301S.px/
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__13_kriminaliteta__01_statistika_toz_sodisc__03_13603_obsojene_poln_osebe/1360303s.px/
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__13_kriminaliteta__01_statistika_toz_sodisc__05_13605_obtozene_mlad_osebe/1360501s.px/
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__13_kriminaliteta__01_statistika_toz_sodisc__02_13602_obtozene_poln_osebe/1360201s.px/
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__13_kriminaliteta__01_statistika_toz_sodisc__04_13604_ovadene_mlad_osebe/1360403s.px/
* https://pxweb.stat.si/SiStatDb/pxweb/sl/10_Dem_soc/10_Dem_soc__13_kriminaliteta__01_statistika_toz_sodisc__01_13601_ovadene_poln_osebe/1360106s.px/

## Program

Glavni program in poročilo se nahajata v datoteki `projekt.Rmd`.
Ko ga prevedemo, se izvedejo programi, ki ustrezajo drugi, tretji in četrti fazi projekta:

* obdelava, uvoz in čiščenje podatkov: `uvoz/uvoz.r`
* analiza in vizualizacija podatkov: `vizualizacija/vizualizacija.r`
* napredna analiza podatkov: `analiza/analiza.r`

Vnaprej pripravljene funkcije se nahajajo v datotekah v mapi `lib/`.
Podatkovni viri so v mapi `podatki/`.
Zemljevidi v obliki SHP, ki jih program pobere,
se shranijo v mapo `../zemljevidi/` (torej izven mape projekta).

## Potrebni paketi za R

Za zagon tega vzorca je potrebno namestiti sledeče pakete za R:

* `knitr` - za izdelovanje poročila
* `rmarkdown` - za prevajanje poročila v obliki RMarkdown
* `shiny` - za prikaz spletnega vmesnika
* `DT` - za prikaz interaktivne tabele
* `rgdal` - za uvoz zemljevidov
* `rgeos` - za podporo zemljevidom
* `digest` - za zgoščevalne funkcije (uporabljajo se za shranjevanje zemljevidov)
* `readr` - za branje podatkov
* `rvest` - za pobiranje spletnih strani
* `tidyr` - za preoblikovanje podatkov v obliko *tidy data*
* `dplyr` - za delo s podatki
* `gsubfn` - za delo z nizi (čiščenje podatkov)
* `ggplot2` - za izrisovanje grafov
* `mosaic` - za pretvorbo zemljevidov v obliko za risanje z `ggplot2`
* `maptools` - za delo z zemljevidi
* `extrafont` - za pravilen prikaz šumnikov (neobvezno)

## Binder

Zgornje [povezave](#analiza-podatkov-s-programom-r-201819)
omogočajo poganjanje projekta na spletu z orodjem [Binder](https://mybinder.org/).
V ta namen je bila pripravljena slika za [Docker](https://www.docker.com/),
ki vsebuje večino paketov, ki jih boste potrebovali za svoj projekt.

Če se izkaže, da katerega od paketov, ki ji potrebujete, ni v sliki,
lahko za sprotno namestitev poskrbite tako,
da jih v datoteki [`install.R`](install.R) namestite z ukazom `install.packages`.
Te datoteke (ali ukaza `install.packages`) **ne vključujte** v svoj program -
gre samo za navodilo za Binder, katere pakete naj namesti pred poganjanjem vašega projekta.

Tako nameščanje paketov se bo izvedlo pred vsakim poganjanjem v Binderju.
Če se izkaže, da je to preveč zamudno,
lahko pripravite [lastno sliko](https://github.com/jaanos/APPR-docker) z želenimi paketi.

Če želite v Binderju delati z git,
v datoteki `gitconfig` nastavite svoje ime in priimek ter e-poštni naslov
(odkomentirajte vzorec in zamenjajte s svojimi podatki) -
ob naslednjem zagonu bo mogoče delati commite.
Te podatke lahko nastavite tudi z `git config --global` v konzoli
(vendar bodo veljale le v trenutni seji).
