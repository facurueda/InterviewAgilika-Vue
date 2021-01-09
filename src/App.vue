<template>
      <GuiInterface
            msg="TEST COMPONENTE"
            :freeSpaces="freeSpaces"
            :addVehicle="addVehicle"
      />
      <ParkedVehicles
            :vehicleParked="vehicleParked"
            :deleteVehicleParked="deleteVehicleParked"
      />

      <QueueVehicles
            :deleteVehicleQueue="deleteVehicleQueue"
            :vehicleQueue="vehicleQueue"
      />
      <div>{{ this.uploadVehiclesQueue() }}</div>
</template>
<script>
import GuiInterface from "./components/GuiInterface.vue";
import ParkedVehicles from "./components/ParkedVehicles.vue";
import QueueVehicles from "./components/QueueVehicles.vue";

export default {
      name: "App",
      components: {
            GuiInterface,
            ParkedVehicles,
            QueueVehicles,
      },
      data() {
            return {
                  freeSpaces: { 1: 5, 2: 5, 3: 5 },
                  vehicleParked: [],
                  vehicleQueue: [],
            };
      },
      methods: {
            addVehicle(e) {
                  if (!e.queue && this.vehicleQueue.length > 0) {
                        e.queue = true;
                        return (this.vehicleQueue = [...this.vehicleQueue, e]);
                  }
                  while (e.parked < 4) {
                        if (this.freeSpaces[e.parked] > 0) {
                              if (e.queue) {
                                    e.queue = false;
                                    return (
                                          (this.freeSpaces = {
                                                ...this.freeSpaces,
                                                [e.parked]:
                                                      this.freeSpaces[
                                                            e.parked
                                                      ] - 1,
                                          }),
                                          (this.vehicleParked = [
                                                ...this.vehicleParked,
                                                e,
                                          ]),
                                          (this.vehicleQueue = this.vehicleQueue.splice(
                                                1
                                          ))
                                    );
                              } else {
                                    return (
                                          (this.freeSpaces = {
                                                ...this.freeSpaces,
                                                [e.parked]:
                                                      this.freeSpaces[
                                                            e.parked
                                                      ] - 1,
                                          }),
                                          (this.vehicleParked = [
                                                ...this.vehicleParked,
                                                e,
                                          ])
                                    );
                              }
                        } else {
                              e.parked = e.parked + 1;
                              return this.addVehicle(e);
                        }
                  }

                  if (e.queue) {
                        e.parked = e.size;
                        return;
                  } else {
                        e.parked = e.size;
                        e.queue = true;
                        return (this.vehicleQueue = [...this.vehicleQueue, e]);
                  }
            },
            deleteVehicleParked(vehicle, ind) {
                  (this.freeSpaces = {
                        ...this.freeSpaces,
                        [vehicle.parked]: this.freeSpaces[vehicle.parked] + 1,
                  }),
                        (this.vehicleParked = this.vehicleParked.filter(
                              (e, index) => {
                                    return index !== ind;
                              }
                        ));
            },
            deleteVehicleQueue(ind) {
                  this.vehicleQueue = this.vehicleQueue.filter((e, index) => {
                        return index !== ind;
                  });
            },
            uploadVehiclesQueue() {
                  if (this.vehicleQueue.length > 0)
                        this.addVehicle(this.vehicleQueue[0]);
            },
      },
};
</script>

<style>
#app {
      width: 100%;
      height: 98vh;
      display: flex;
}
</style>
