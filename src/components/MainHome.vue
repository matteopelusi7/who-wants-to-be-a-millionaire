<template>
  <div class="home">

    <div class="header">
      <figure class="image-logo">
        <img src="https://www.notion.so/image/https%3A%2F%2Fs3-us-west-2.amazonaws.com%2Fsecure.notion-static.com%2F0b8e1102-7ff4-4870-a39e-ef625253af75%2Flogo.png?table=block&id=d1419994-97c4-4690-b349-03db5eada926&spaceId=4c49ff97-016b-4669-8de5-4479dd1a86e1&width=480&userId=863850ea-3b24-4de8-b681-d214b9ffd42e&cache=v2" alt="">
      </figure>
    </div>

    <div class="footer">

      <div v-if="cont < 10" class="question">
        <p>{{ questions[random()].question }}</p>
      </div>

      <div  class="answer">
        <ul class="list-item" v-if="cont < 10">
          <li @click="correctFalse(el)" v-for="(el, i) in questions[rand].answer" :key="i" class="item">
            <p :class=" (questions[rand].done == true) ? 'correct' : '' ">{{ el }}</p>
          </li>
        </ul>
        <div v-else class="fix">
          <h3 class="text-uppercase">Hai terminato!!</h3>
          <p>Hai indovinato {{ correct }} domande</p>
          <p>Hai sbagliato {{ error }} domande</p>
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
      cont: 0,
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
      ]
    }
  },
  methods: {
    random: function () {
      const res = Math.floor(Math.random()*10);
      // console.log( res )
      this.rand = res
      return res
    },
    correctFalse: function(el) {

      if( this.cont < 10 ) {

        if(el == this.questions[this.rand].answercorrect) {
          console.log('corretto')
          // this.questions[this.rand].done == true
          this.rand = null

          this.correct++
          this.cont++
        } else {
          console.log('errato')
          // this.questions[this.rand].done == false
          this.rand = null

          this.error++
          this.cont++
        }

      } else {
        this.finish == true
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

.fix {
  color: white;
  display: flex;
  flex-direction: column;
  align-items: center;
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
      border: 1px solid white;
      width: 600px;
      margin-top: 70px;
      display: flex;
      justify-content: center;
      align-items: center;
      margin-bottom: 100px;

      p{
        
      }
      
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

</style>