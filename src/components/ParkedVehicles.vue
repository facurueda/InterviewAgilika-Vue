<template>
      <div className="parked-container">
            <label className="parked-title">VEHICLES PARKED</label>
            <div className="parked-vehicles-container">
                  <div
                        v-for="(vehicles, index) in vehicleParked"
                        v-bind:key="index"
                  >
                        <div className="vehicle">
                              <img v-bind:src='vehicles.img' alt="vehicle-img" />
                              <label className="vehicle-name">
                                    {{ vehicles.name }}
                              </label>
                              <label className="vehicle-name">
                                    Parking Size {{ vehicles.parked }}
                              </label>
                              <button
                                    className="button-delete-vehicle-parked"
                                    @click="
                                          deleteVehicleParked(vehicles, index)
                                    "
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
      name: "ParkedVehicles",
      props: {
            vehicleParked: Array,
            deleteVehicleParked: Function,
      },
};
</script>

<style scoped>
.parked-container {
      display: flex;
      width: 70%;
      flex-direction: column;
      background-color: #ffe1b9;
}

.parked-title{
      font-size: 50px;
      font-family: monospace;
      text-align: center;
      text-decoration: underline;
      margin-top: 50px;
      margin-bottom: 50px;
}

.parked-vehicles-container {
      display: flex;
      flex-wrap: wrap;
      place-content: space-around;
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
.button-delete-vehicle-parked{
      cursor: pointer;
      width: 85%;
      align-self: center;
      border: none;
      border-radius: 25px;
      height: 35px;
      background-color: rgb(255, 46, 81);
      transition: .4s;
      outline: none !important;
      font-weight: 500;
      -webkit-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
      -moz-box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
      box-shadow: 10px 10px 5px 0px rgba(0, 0, 0, 0.75);
}

.button-delete-vehicle-parked:hover{
      background-color: rgb(255, 116, 139);
      transition: .4s;
}
</style>
