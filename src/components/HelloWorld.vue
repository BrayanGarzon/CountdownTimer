<script>
export default {
  data() {
    return {
      targetDate: new Date("2023-12-31 00:00:00"),
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
                  <div class="circle-half left-half"></div>
                  <div class="circle-half right-half"></div>
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
                  <div class="circle-half left-half"></div>
                  <div class="circle-half right-half"></div>
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
                  <div class="circle-half left-half"></div>
                  <div class="circle-half right-half"></div>
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
                  <div class="circle-half left-half"></div>
                  <div class="circle-half right-half"></div>
                </div>
                <div class="bottom">{{ cards[3].value }}</div>
              </div>
              <h5>SECONDS</h5>
            </div>

 
          </div>
         
          
        </div>
        
        <div class="iconos">
          <a href=""><i class="fa-brands fa-square-facebook"></i></a>
          <a href=""><i class="fa-brands fa-pinterest"></i></a>
          <a href=""><i class="fa-brands fa-instagram"></i></a>
          
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
  overflow: hidden;
}

.top-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 50%;
  z-index: 1;
}

.red-overlay {
  background-color: rgba(43, 37, 48, 0.46);
  border-bottom: 1px solid rgba(68, 68, 68, 0.721);
}

.blue-overlay {
  background-color: transparent;
}
.circle-half {
  position: absolute;
  top: 50%;
  width: 5%;
  height: 7%;
  background-color: hsla(235, 18%, 12%, 0.704);
  overflow: hidden;
  transform: translateY(-50%);
  z-index: 2; /* Asegúrate de tener un z-index mayor que los overlays red y blue */
}


.left-half {
  border-radius: 0 50% 50% 0;
  left: 0;
}

.right-half {
  border-radius: 50% 0 0 50%;
  right: 0;
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
.iconos a{
  text-decoration: none;
}
.iconos a i{
  color: hsl(237, 18%, 59%);
  font-size: 30px;
  margin: 10px;
  cursor: pointer;
}

.iconos a i:hover{
  color: hsl(345, 95%, 68%);
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
