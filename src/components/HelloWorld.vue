<script>
export default {
  data() {
    return {
      targetDate: new Date("2023-12-31 00:00:00"), // Cambia esta fecha a tu fecha objetivo
      cards: [
        { value: 0, text: "DAYS", marginLeft: "10px" },
        { value: 0, text: "HOURS", marginLeft: "15px" },
        { value: 0, text: "MINUTES", marginLeft: "0px" },
        { value: 0, text: "SECONDS", marginLeft: "0px" },
      ],
    };
  },
  methods: {
    updateCounter() {
      const now = new Date();
      const timeDiff = this.targetDate - now;
      const totalSeconds = Math.floor(timeDiff / 1000);
      
      // Calcular días, horas, minutos y segundos
      const days = Math.floor(totalSeconds / 86400);
      const hours = Math.floor((totalSeconds % 86400) / 3600);
      const minutes = Math.floor((totalSeconds % 3600) / 60);
      const seconds = totalSeconds % 60;

      // Actualizar los valores en las tarjetas
      this.cards[0].value = days;
      this.cards[1].value = hours;
      this.cards[2].value = minutes;
      this.cards[3].value = seconds;
    },
    cardTopTransform(value) {
      if (value < 10) {
        return "translateY(0)";
      }
      return "translateY(-50px)";
    },
  },
  mounted() {
    setInterval(this.updateCounter, 1000);
    this.updateCounter();
  },
};
</script>



<template>
  <section>
    <div class="container"> <!--fondo con la gradiente-->
      <div class="containerTimer">

        <div class="texto">
          <h2>WE´RE LAUNCHING SOON</h2>
        </div>
        
        <div class="counter">

          <div class="containerCards">
            <div class="card" v-for="(card, index) in cards" :key="index">
              <div class="bottom">{{ card.value }}</div>
            </div>
          </div>
          
          
          <div class="texCards">
            <div class="text-cards">
              <div v-for="(card, index) in cards" :key="index" :style="{marginLeft: card.marginLeft }" class="text">{{ card.text }}</div>
            </div>
          </div>
         
          
        </div>
        
        <div class="iconos"></div>
      </div>
    </div>
  </section>
</template>

<style scoped>
section {
  width: 100%;
  height: 100vh;
  background: linear-gradient(to bottom, hsla(237, 18%, 59%, 0.062), hsla(345, 95%, 68%, 0.072)), url('/src/images/pattern-hills.svg');
  background-repeat: no-repeat;
  background-position: bottom center;
  background-size: 100% auto;
  display: flex;
  justify-content: center;
  align-items: center;    
}



section .container .containerTimer{
  height: 100vh;
  width: auto;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}


section .container .containerTimer .texto{
  display: flex;
  justify-content: center;
  align-items: center;
}
section .container .containerTimer .texto h2{
    margin: 0;
    padding: 0;
    color: var(--color-text); 
    letter-spacing: 10px;
    font-size: 20px;
}


.counter {
  display: flex;
  justify-content: center;
  align-content: center;
  flex-direction: column;
}
.counter .containerCards{
  display: flex;
}



.card {
  width: 120px;
  height: 120px;
  display: flex;
  flex-direction: column;
  align-items: center;
  margin: 10px;
  background-color: var(--color-background-cards);
  padding: 10px;
  border-radius: 5px;
  overflow: hidden;
  animation: cardSlide 1s ease-in-out;
  color: var(--color-text-second);
  font-size: 60px;
}


.bottom {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.counter .texCards{
  display: flex;
  justify-content: center;
  align-items: center;
} 

.text-cards{
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 100px;
}

</style>
