<template>
      <div className="guiContainer">
            <div className="freeSpaces">
                  <label className="title">Status of parking spaces</label>
                  <label> small: {{ freeSpaces[1] }}</label>
                  <label> medium: {{ freeSpaces[2] }}</label>
                  <label> large: {{ freeSpaces[3] }}</label>
            </div>
            <div className="buttons">
                  <button
                        className="buttonToAdd"
                        @click="
                              addVehicle({
                                    size: 1,
                                    parked: 1,
                                    name: 'Motorcycle',
                                    img: 'https://res.cloudinary.com/facu9685/image/upload/v1610212289/r3mj6n1xgnu9q1xf12vs.png',
                                    queue: false,
                              })
                        "
                  >
                        Motorcycle
                  </button>
                  <button
                        className="buttonToAdd"
                        @click="
                              addVehicle({
                                    size: 2,
                                    parked: 2,
                                    name: 'Sedan',
                                    img: 'https://res.cloudinary.com/facu9685/image/upload/v1610212289/y8zv8sghpuu65pqrukog.png',
                                    queue: false,
                              })
                        "
                  >
                        Sedan
                  </button>
                  <button
                        className="buttonToAdd"
                        @click="
                              addVehicle({
                                    size: 3,
                                    parked: 3,
                                    name: 'Truck',
                                    img: 'https://res.cloudinary.com/facu9685/image/upload/v1610212289/o7w3fcja9zpmmzm5hkpq.png',
                                    queue: false,
                              })
                        "
                  >
                        Truck
                  </button>
            </div>
      </div>
</template>

<script>
export default {
      name: "GuiInterface",
      props: {
            msg: String,
            freeSpaces: Object,
            addVehicle: Function,
      },
};
</script>

<style scoped>
.guiContainer {
      height: 100%;
      width: 15%;
      display: flex;
      flex-direction: column-reverse;
      justify-content: center;
}
.buttons {
      display: flex;
      flex-direction: column;
}

.buttonToAdd {
      cursor: pointer;
      width: 85%;
      align-self: center;
      margin-top: 50px;
      margin-bottom: 25px;
      border: none;
      border-radius: 25px;
      height: 50px;
      background-color: rgb(82, 137, 255);
      transition: .4s;
      outline: none !important;
      font-weight: 500;
      -webkit-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
      -moz-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
      box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
}
.buttonToAdd:hover{
      background-color: rgb(182, 205, 255);
      transition: .4s;
}

.freeSpaces {
      display: flex;
      flex-direction: column;
      margin-top: 150px;
}

.freeSpaces > label {
      text-align: center;
      font-size: 25px;
      font-family: monospace;
}

.title{
      font-size: 35px !important;
      margin-bottom: 25px;
      text-decoration: underline;
}
</style>
