<script>
export default {
  data() {
    return {
      targetDate: new Date("2023-12-20 00:00:00"),
      cards: [
        { value: 0, text: "DAYS" },
        { value: 0, text: "HOURS" },
        { value: 0, text: "MINUTES" },
        { value: 0, text: "SECONDS" },
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

      // Actualizar los valores en las tarjetas, formateando a dos dígitos
      this.cards[0].value = this.formatValue(days);
      this.cards[1].value = this.formatValue(hours);
      this.cards[2].value = this.formatValue(minutes);
      this.cards[3].value = this.formatValue(seconds);
    },
    formatValue(value) {
      return value < 10 ? `0${value}` : value;
    },
    cardTopTransform(value) {
      return value < 10;
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

            <div class="cardPadre">
              <div class="card">
                <div class="overlay-container">
                  <div class="top-overlay red-overlay"></div>
                  <div class="top-overlay blue-overlay"></div>
                </div>
                <div class="bottom">{{ cards[0].value }}</div>
              </div>
              <h5>DAYS</h5>
            </div>
            
            <div class="cardPadre">
              <div class="card">
                <div class="overlay-container">
                  <div class="top-overlay red-overlay"></div>
                  <div class="top-overlay blue-overlay"></div>
                </div>
                <div class="bottom">{{ cards[1].value }}</div>
              </div>    
              <h5>HOURS</h5>
            </div>

            <div class="cardPadre">
              <div class="card">
                <div class="overlay-container">
                  <div class="top-overlay red-overlay"></div>
                  <div class="top-overlay blue-overlay"></div>
                </div>
                <div class="bottom">{{ cards[2].value }}</div>
              </div>
              <h5>MINUTES</h5>
            </div>

            <div class="cardPadre">
              <div class="card">
                <div class="overlay-container">
                  <div class="top-overlay red-overlay"></div>
                  <div class="top-overlay blue-overlay"></div>
                </div>
                <div class="bottom">{{ cards[3].value }}</div>
              </div>
              <h5>SECONDS</h5>
            </div>
 
          </div>
         
          
        </div>
        
        <div class="iconos">
          <img src="/src/images/icon-facebook.svg" alt="">
          <img src="/src/images/icon-pinterest.svg" alt="">
          <img src="/src/images/icon-instagram.svg" alt="">
        </div>
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
  align-items: flex-end;
  width: 100%;
  height: 200px;
 
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
  width: 100%;
  height: 300px;
}

.counter .containerCards{
  display: flex;
}
.counter .containerCards .cardPadre{
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.counter .containerCards .cardPadre h5{
  font-family: var(--font-famly);
  letter-spacing: 3px;
  font-weight: 700;
  margin: 0;
  padding: 0;
  margin-top: 10px;
}
.card {
  width: 120px;
  height: 130px;
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
  box-shadow: 0 8px 4px rgba(0, 0, 0, 0.4);
  position: relative;
}

.bottom {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  position: relative;
  z-index: 0;
}
.overlay-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.top-overlay {
  flex: 1;
  background-color: transparent; /* Ajusta según sea necesario */
}

.red-overlay {
  background-color: rgba(43, 37, 48, 0.397); /* Rojo semitransparente */
}

.blue-overlay {
  background-color: transparent; /* Azul semitransparente */
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
.iconos{
  width: 100%;
  height: 250px;

  display: flex;
  justify-content: center;
  align-items: flex-end;
}

.iconos img{
  margin: 20px;
}


/* CODE PANTALLAS PEQUEÑAS */
@media (min-width: 375px) and (max-width: 470px){
  section .container .containerTimer .texto{
    display: flex;
    justify-content: center;
    align-items: flex-end;
    width: 100%;
    
  }
  section .container .containerTimer .texto h2{
    font-size: 20px;
    text-align: center;
  }
  .card{
    width: 55px;
    height: 55px;
    font-size: 40px;
  }
  .counter .containerCards .cardPadre h5{
    font-size: 10px;
  }

  .counter{
    height: 200px;
  }
  
}
</style>
