<template lang='pug'>
#slides.eg-theme-agrume
  .eg-slideshow
    slide(enter='fadeIn' leave='bounceOutLeft')
      h3 KappaZeta veebikaart Sentinel-1 ja -2 aegridade sirvimiseks ja niitmise tuvastamise tulemuste näitamiseks
      h4.center Kaugseire seminar 17.10.2019
      h4.center Mihkel Oviir
      h4.center Sookolli Kaardid OÜ
    slide(:steps=7 enter='bounceInRight' leave='bounceOutLeft')
      h3 Projekt
      p(v-if='step >= 2') 01.2019 - 09.2019
      p(v-if='step >= 3') Eesmärgid:
      p(v-if='step >= 4') Peab töötama sujuvalt vähemalt 1.6 miljoni põlluga.
      p(v-if='step >= 5') Peab olema lihtsam üles seada uusi demorakendusi klientidele.
      p(v-if='step >= 6') Peab olema vähemalt algtasemel kasutajahaldus.
      p(v-if='step >= 7') Peab töötama kõikidel populaarsetel brauseritel nii arvutis kui mobiilis.
    slide(:steps=9 enter='bounceInRight' leave='bounceOutLeft')
      h3 Arhitektuur
      p(v-if='step >= 2') Nginx veebiserver
      p(v-if='step >= 3') PostgreSQL andmebaas
      p(v-if='step >= 4') KappaZeta REST API
      p(v-if='step == 5') Apache Tomcat server
      p(v-if='step == 6') Apache Tomcat server
      p(v-if='step == 6') Geoserver
      p.strikethrough(v-if='step >= 7') Apache Tomcat server
      p.strikethrough(v-if='step >= 7') Geoserver
      p(v-if='step >= 8') Tippecanoe tilegen
      p(v-if='step >= 9') Veebikaart
    slide(enter='bounceInRight' leave='bounceOutLeft')
      h3 Arhitektuur
      p.center
        img(src='graph.png')
    slide(:steps=6 enter='bounceInRight' leave='bounceOutLeft')
      h3 Põllud kaardile!
      p(v-if='step >= 2') Kuidas kuvada suurt andmehulka?
      p(v-if='step >= 3') Kuidas suure andmehulga ajalisi muutusi kuvada?
      p(v-if='step >= 4') Andmemaht on liiga suur, et seda korraga brauserisse laadida / renderdada
      p(v-if='step >= 5') WMS jääb ajatelje tõttu aeglaseks ja puudub interaktiivsus
      p(v-if='step >= 6') Eelgenereeritud raster tileset oleks vaja teha iga päeva kohta, jääks ajatelje tõttu aeglaseks ja puudub interaktiivsus
    slide(enter='bounceInRight' leave='bounceOutLeft')
      h3 Vektor tiles
      p.center
        img(src='vectortile.jpg')
    slide(enter='bounceInRight' leave='bounceOutLeft')
      h3 Vektor tiles
      p.center
        img(src='tiles-pyramid.png')
    slide(:steps=8 enter='bounceInRight' leave='bounceOutLeft')
      h3 Tilegen
      p(v-if='step >= 2') Eelgenereeritud vektor tilesetid
      p(v-if='step >= 3') Geoserver toetab aga seadistamine on võimatu
      p(v-if='step >= 4') Tippecanoe (Mapbox) käsurea programm
      p(v-if='step >= 5') Peenhäälestus parameetritega
      p(v-if='step >= 6') -Q -z 14 -an -pS -pt -ab -S 8 -g 2 -aG -M 50000 --force -P
      p(v-if='step >= 7') PRIA põldude genereerimine ~400 sekundit
      p(v-if='step >= 8') Croniga perioodiline uuendamine
    slide(enter='bounceInRight' leave='bounceOutLeft')
      h3 Tilegen
      p.center
        img(src='tile.jpg')
    slide(:steps=9 enter='bounceInRight' leave='bounceOutLeft')
      h3 Veebikaart
      p(v-if='step >= 2') Webpack + Babel + ES6
      p(v-if='step >= 3') Vue + Bulma
      p(v-if='step >= 4') OpenLayers + Proj4.js
      p(v-if='step >= 5') Front-end-only SPA
      p(v-if='step >= 6') Autentimine vastu REST APIt
      p(v-if='step >= 7') Suhtleb REST API'ga üle AJAX päringute
      p(v-if='step >= 8') Multikeelsuse tugi
      p(v-if='step >= 9') Kõik komponendid on konfigureeritavad
    slide(:steps=4 enter='bounceInRight' leave='bounceOutLeft')
      h3 Veebikaardi ajatelg
      p(v-if='step >= 2') Põllul on atribuudina muutuste kuupäevad unix-ajatemplina ja muutuste väärtused
      p(v-if='step >= 3') Vaikimisi värvitakse põld selle väärtusega, mille ajatempel on viimane enne ajatelje hetkeväärtust
      p(v-if='step >= 4') Ajatelje väärtust muutes toimub igas kaadris iga põllu kohta eelmise punkti arvutus
    slide(:steps=4 enter='bounceInRight' leave='bounceOutLeft')
      h3 Veebikaardi graafikud
      p(v-if='step >= 2') Chart.js
      p(v-if='step >= 3') Lisatud kohandatud legend, traktori ikoon, klikatavad väärtused ja tähtaegade jooned
      p(v-if='step >= 4') Põllu vaade Sentineli piltide aegrea taustal
    slide(:steps=6 enter='bounceInRight')
      h3 Kokkuvõte
      p(v-if='step >= 2') Töötab sujuvalt 1.6 miljoni põlluga ka telefonis.
      p(v-if='step >= 3') Uutele klientidele lihtsam üles seada - nii ja naa. Lisandus tilegen, mida enne ei olnud. Samas on kõik liigutused skriptitud.
      p(v-if='step >= 4') Kasutajahaldus on REST APIga sama.
      p(v-if='step >= 5') Kasutajaliides töötab kõikidel populaarsetel brauseritel nii arvutis kui mobiilis.
      h3(v-if='step >= 6') Aitäh!
</template>

<script>
import eagle from 'eagle.js'
export default {
  mixins: [ eagle.slideshow ],
  data () {
    return {
      preloadedImages: {}
    }
  }
}
</script>

<style lang='scss'>
@import 'node_modules/eagle.js/dist/themes/agrume/agrume';
.pad {
  padding: 0.5rem
}
.codeblock .code-box {
  box-shadow: none;
  border: 1px solid #ddd
}
.quote {
  font-family: "Pompiere", cursive
}
.strikethrough {
  text-decoration: line-through;
}
img {

}

</style>
