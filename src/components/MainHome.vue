<template>
  <div class="home">

    <div class="header">
      <figure class="image-logo">
        <img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0b8e1102-7ff4-4870-a39e-ef625253af75%2Flogo.png?table=block&id=d1419994-97c4-4690-b349-03db5eada926&spaceId=4c49ff97-016b-4669-8de5-4479dd1a86e1&width=480&userId=863850ea-3b24-4de8-b681-d214b9ffd42e&cache=v2" alt="">
      </figure>
    </div>

    <div class="footer">

      <div class="init-game" v-if="insertName == false">
        <h2>Benvenuto a chi vuol essere milionario!</h2>
        <p>Attenzione!! alcune domande potrebbero ripetersi, quindi ragionaci bene! 😉</p>
        <p>Inserisci il tuo nome qui sotto &Darr;</p>
        <input class="input-type" placeholder="Inserisci il tuo nome" type="text" v-model="name">
        <button class="button" @click="initGame()">Inizia</button>
      </div>

      <div class="init" v-else>
        <div v-if="cont < 7" class="question">
          <p>{{ questions[random()].question }}</p>
        </div>

        <div  class="answer">
          <ul class="list-item" v-if="cont < 7">
            <li  @click="correctFalse(el)" v-for="(el, i) in questions[rand].answer" :key="i" class="item">
              <p class="">{{ el }}</p>
            </li>
          </ul>
          <div v-else class="fix">
            <h3 class="text-uppercase">Hai terminato!!</h3>
            <p>Ecco i tuoi risultati {{ name }}</p>
            <p>Hai indovinato {{ correct }} domande</p>
            <p>Hai sbagliato {{ error }} domande</p>
          </div>
        </div>
      </div>


    </div>

  </div>
</template>

<script>
export default {
  name: 'MainHome',
  data() {
    return {
      rand: null,
      insertName: false,
      cont: 0,
      name: '',
      error: 0,
      correct: 0,
      finish: false,
      questions: [
        {
          question: 'Quanti fusi orari ci sono in Russia?',
          answer: {
            answ1 : '9',
            answ2 : '5', 
            answ3 : '11',
            answ4 : '8',
          },
          answercorrect: '11',
        },
        {
          question: 'Qual è il fiore nazionale del Giappone?',
          answer: {
            answ1: 'Fiore di ciliegio',
            answ2: 'Fiore di pesche',
            answ3: 'Fiore di fichi',
            answ4: 'Fiore di fragola',
          },
          answercorrect: 'Fiore di ciliegio'
        },
        {
          question: 'Quante strisce ci sono sulla bandiera americana?',
          answer: {
            answ1: '10',
            answ2: '15',
            answ3: '21',
            answ4: '13',
          },
          answercorrect: '13',
        },
        {
          question: 'Qual è il paese più piccolo del mondo?',
          answer: {
            answ1: 'Gibilterra',
            answ2: 'Il Vaticano',
            answ3: 'San Marino',
            answ4: 'Andorra',
          },
          answercorrect: 'Il Vaticano',
        },
        {
          question: 'Quando ha aperto la metropolitana di Londra?',
          answer: {
            answ1: '1871',
            answ2: '1926',
            answ3: '1863',
            answ4: '1861',
          },
          answercorrect: '1863',
        },
        {
          question: 'Da quale città provengono i Beatles?',
          answer: {
            answ1: 'Manchester',
            answ2: 'Liverpool',
            answ3: 'Scozia',
            answ4: 'Londra',
          },
          answercorrect: 'Liverpool',
        },
        {
          question: 'La serie di libri più venduti del XXI secolo?',
          answer: {
            answ1: 'Harry Potter',
            answ2: 'Signore degli anelli',
            answ3: 'Star Wars',
            answ4: 'The Mandalorian',
          },
          answercorrect: 'Harry Potter',
        },
        {
          question: 'Quale dei seguenti imperi non aveva una lingua scritta:',
          answer: {
            answ1: 'Inca',
            answ2: 'Azteco',
            answ3: 'Egiziano',
            answ4: 'Romano',
          },
          answercorrect: 'Inca',
        },
        {
          question: 'Qual è la capitale del Canada?',
          answer: {
            answ1: 'Los Angeles',
            answ2: 'Toronto',
            answ3: 'Ottawa',
            answ4: 'New York',
          },
          answercorrect: 'Ottawa',
        },
        {
          question: 'Quale giocatore ha vinto più palloni d oro?',
          answer: {
            answ1: 'Cristiano Ronaldo',
            answ2: 'Maradona',
            answ3: 'Messi',
            answ4: 'Pelè',
          },
          answercorrect: 'Messi',
        },
        {
          question: 'L’Italia è',
          answer: {
            answ1: 'Una Repubblica presidenziale',
            answ2: 'Una Repubblica angioplastica',
            answ3: 'Una Repubblica parlamentare ',
            answ4: 'Una Monarchia costituzionale',
          },
          answercorrect: 'Una Repubblica parlamentare ',
        },
        {
          question: 'Il participio passato del verbo esigere è',
          answer: {
            answ1: 'Esigito',
            answ2: 'Esigiuto',
            answ3: 'Esagitato',
            answ4: 'Esatto',
          },
          answercorrect: 'Esatto',
        },
        {
          question: 'Cos’è un neologismo?',
          answer: {
            answ1: 'Una tecnica chirurgica per la rimozione degli angiomi benigni',
            answ2: 'Uno strappo muscolare al gomito, tipico del giocatore di tennis',
            answ3: 'Una parola od espressione entrata recentemente nella lingua',
            answ4: 'Una parola inutile e superflua all’interno di una frase',
          },
          answercorrect: 'Una parola od espressione entrata recentemente nella lingua',
        },
        {
          question: 'Quale fra i seguenti nomi non appartiene ad un noto designer?',
          answer: {
            answ1: 'Achille Castiglioni',
            answ2: 'Richard Sapper',
            answ3: 'Renato Soru',
            answ4: 'Paolo Ulian',
          },
          answercorrect: 'Renato Soru',
        },
        {
          question: 'In quale anno il Fascismo emanò le cosiddette leggi razziali?',
          answer: {
            answ1: '1915',
            answ2: '1933',
            answ3: '1938',
            answ4: '1968',
          },
          answercorrect: '1938',
        },
        {
          question: 'Emmanuel Macron è',
          answer: {
            answ1: 'L’inventore degli obiettivi usati per la macrofotografi',
            answ2: 'L’attuale Presidente della Repubblica Ceca',
            answ3: 'L’autore, insieme a D’Alembert, della famosa Encyclopédie',
            answ4: 'L’attuale Presidente della Repubblica Francese',
          },
          answercorrect: 'L’attuale Presidente della Repubblica Francese',
        },
        {
          question: 'La semiotica è',
          answer: {
            answ1: 'La disciplina che studia i segni, per mezzo dei quali avviene la comunicazione',
            answ2: 'La disciplina che studia i sogni e le loro conseguenze nella psicanalisi',
            answ3: 'Una branca della botanica che studia il modo di riprodursi delle piante',
            answ4: 'Una branca della psicanalisi, che si occupa delle persone con deficit da accudimento',
          },
          answercorrect: 'La disciplina che studia i segni, per mezzo dei quali avviene la comunicazione',
        },
        {
          question: 'Quale dei seguenti nomi è fuori posto rispetto gli altri tre?',
          answer: {
            answ1: 'Primo Levi',
            answ2: 'Carlo Levi',
            answ3: 'Rita Levi Montalcini',
            answ4: 'Italo Calvino',
          },
          answercorrect: 'Rita Levi Montalcini',
        },
        {
          question: 'Dei delitti e delle pene è un’opera di:',
          answer: {
            answ1: 'Cesare Beccaria',
            answ2: 'Alessandro Verri',
            answ3: 'Francesco Saverio Borrelli',
            answ4: 'Giuseppe Parini',
          },
          answercorrect: 'Cesare Beccaria',
        },
        {
          question: 'Quale dei seguenti noti quotidiani si occupa in particolare di notizie economiche legate al mondo del lavoro?',
          answer: {
            answ1: 'La Repubblica',
            answ2: 'Il Corriere della Sera',
            answ3: 'Il Sole 24 Ore ',
            answ4: 'Il Fatto Quotidiano',
          },
          answercorrect: 'Il Sole 24 Ore ',
        },
      ]
    }
  },
  methods: {
    random: function () {
      const res = Math.floor(Math.random()*20);
      this.rand = res
      return res
    },
    correctFalse: function(el) {

      if( this.cont < 7 ) {

        if(el == this.questions[this.rand].answercorrect) {
          console.log('corretto')
          this.rand = null

          this.correct++
          this.cont++
        } else {
          console.log('errato')
          this.rand = null

          this.error++
          this.cont++
        }

      } else {
        this.finish == true
      }

    },
    initGame: function() {
      if(this.name != '') {
        this.insertName = true
      } else {
        alert('Inserisci il tuo nome')
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

.home {
  height: 100vh;
  display: flex;
  flex-direction: column;
}

.init-game {
  margin: 60px 15px;
  color: white;
  display: flex;
  flex-direction: column;
  gap: 15px;
}

.input-type {
  width: 50%;
  border: 1px solid blue;
  border-radius: 5px;
  padding: 6px 5px;
  margin-bottom: 5px;
}

.button {
  width: 20%;
  padding: 5px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid blue;
  cursor: pointer;
}

.init {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.fix {
  color: white;
  display: flex;
  flex-direction: column;
  justify-content: center;
  margin: 60px 0;
}

.header {
  height: 40%;
  background-color: blue;
  display: flex;
  justify-content: center;
  align-items: center;

  .image-logo {
    img {
      width: 300px;
    }
  }
}

.correct {
  background-color: green;
}

.false {
  background-color: red;
}

.footer {
  height: 60%;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgb(1, 1, 77);

    .question {
      color: white;
      border-radius: 10px;
      border: 1px solid white;
      width: 600px;
      margin-top: 70px;
      padding: 0 15px;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-bottom: 100px;
    }

    .answer{
      display: flex;
      justify-content: center;
      align-items: center;
      width: 80%;
    }

    .list-item {
      padding: 0;
      border-radius: 10px;
      list-style: none;
      display: flex;
      color: white;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;

      .item {
        width: calc(100% / 4);
        border-radius: 10px;
        margin: 20px 30px;
        padding: 10px 20px;
        display: flex;
        justify-content: center;
        border: 1px solid white;
        cursor: pointer;
      }
    }

}

@media all and (max-width: 600px) {

.fix {
  color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.header {
  background-color: blue;

  .image-logo {
    img {
      width: 200px;
    }
  }
}

.correct {
  background-color: green;
}

.false {
  background-color: red;
}

.footer {
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: rgb(1, 1, 77);

    .question {
      width: 80%;
      color: white;
      border: 1px solid white;
      margin-top: 70px;
      // margin-left: 70px;
      // margin-right: 70px;
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      align-items: center;
      margin-bottom: 100px;

    }

    .answer{
      display: flex;
      justify-content: center;
      align-items: center;
      width: 80%;
    }

    .list-item {
      padding: 0;
      list-style: none;
      display: flex;
      flex-wrap: wrap;
      color: white;
      justify-content: center;
      align-items: center;
      flex-wrap: wrap;

      .item {
        width: calc(100% / 4);
        margin: 20px 30px;
        padding: 10px 20px;
        display: flex;
        justify-content: center;
        border: 1px solid white;
        cursor: pointer;
      }
    }
}
  
}

</style>