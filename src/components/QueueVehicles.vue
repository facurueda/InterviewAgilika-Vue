<template>
      <div className="queue-container">
            <label className="queue-title">VEHICLES QUEUE</label>
            <div className="queue-vehicles-container">
                  <div
                        v-for="(vehicle, index) in vehicleQueue"
                        v-bind:key="index"
                  >
                        <div className="vehicle">
                              <img v-bind:src="vehicle.img" alt="vehicle-img" />
                              <label className="vehicle-name">
                                    {{ vehicle.name }}
                              </label>
                              <button
                                    className="button-delete-vehicle-parked queue-button"
                                    @click="deleteVehicleQueue(index)"
                              >
                                    DELETE
                              </button>
                        </div>
                  </div>
            </div>
      </div>
</template>

<script>
export default {
      name: "QueueVehicles",
      props: {
            deleteVehicleQueue: Function,
            vehicleQueue: Array,
      },
};
</script>
<style scoped>
.queue-container{
       display: flex;
      width: 15%;
      flex-direction: column;
      overflow-y: scroll;
      background-color: #fcc;
}
.queue-title {
      font-size: 35px;
      font-family: monospace;
      text-align: center;
      text-decoration: underline;
      margin-top: 25px;
      margin-bottom: 25px;
}
.queue-vehicles-container {
      display: flex;
      flex-wrap: wrap;
      place-content: space-around;
}

.parked-title{
      font-size: 50px;
      font-family: monospace;
      text-align: center;
      text-decoration: underline;
      margin-top: 50px;
      margin-bottom: 50px;
}


.vehicle{
      display: flex;
      flex-direction: column;
      align-items: center;
      margin: 25px;
}

.vehicle-name{
      font-size: 20px;
      font-weight: 500;
}
.button-delete-vehicle-parked {
      cursor: pointer;
      width: 85%;
      align-self: center;
      border: none;
      border-radius: 25px;
      height: 35px;
      background-color: rgb(255, 46, 81);
      transition: 0.4s;
      outline: none !important;
      font-weight: 500;
      -webkit-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
      -moz-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
      box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
}

.button-delete-vehicle-parked:hover {
      background-color: rgb(255, 116, 139);
      transition: 0.4s;
}
.queue-button {
      width: 50% !important;
}
</style>
