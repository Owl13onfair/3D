
<template id=alles>



  <div id="grid"> 
    <!-- <div id="info"> <meInfo /> </div> info   -->
    <div id="bilderundtxt" >
      <txtundpng style="width: 100%;"/>
    </div>

    <div id="Liste">
      <nliste @gedrueckt="gedruecktzwischenspeicher" style="width: 25%;" />
      <!--übergabe von NLliste zu app.vue(datenübertragung zu Main-Body)-->
    </div>
    <div id="Mainbody">
      <mainbody :gedruektunduebergeben="gedruecktübergabe" style="width: 75%;" />
      <!--übergabe nach Main body nach überschreibung-->
    </div>
  </div>
</template>



<script>
import { ref } from "vue";



import txtundpng from "./components/bilder-txt.vue"; //noch Ändern
import mainbody from "./components/Main-body.vue";
import nliste from "./components/NL-iste.vue";

const gedruecktübergabe = ref();
export default {
  name: "App",
  components: { nliste, mainbody, txtundpng },
  emits: ["gedrueckt"], //dieses element emitirt  'gedruekt'    da es kein dom Dockument Objekt Model   oder kurtz ein objekt welches einen teil an der graphischen oberfleche hat
  methods: {
    gedruecktzwischenspeicher(gedrueckt) {
      this.gedruecktübergabe = gedrueckt;
      
    },
  },
  data() {
    return {
      gedruecktübergabe: gedruecktübergabe,
    };
  },
  //meInfo
};

// eslint-disable-next-line
const info = ref(false);
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#navigationsliste {
  font-family: Avenir, Helvetica, A, "Gill Sans", "Gill Sans MT", Calibri,
    "Trebuchet MS", sans-serif ns-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: left;
  color: #2c3e50;
  margin-top: 60px;
}
#bilderundtxt {
  grid-area: bild;
}

#Liste {
  grid-area: liste;
}
#Mainbody {
  grid-area: main;
}
#grid {
  box-sizing: border-box;
  width: 100%;
  display: grid;
  grid-template-areas:
    "bild bild bild bild bild bild"
    "bild bild bild bild bild bild"
    "liste main main main right right"
    "liste footer footer footer footer footer";
  gap: 10px;
  padding: 0px;
  margin: 0px;
}

#alles{
   padding: 0px;
  margin: 0px;
}


</style>
