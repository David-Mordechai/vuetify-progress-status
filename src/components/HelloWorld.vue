<template>
  <v-container>
    <v-card>
      <v-progress-linear :model-value="progress" height="10" location="top" absolute color="primary" />
      <v-card-item>
        <div>
          <div class="text-h6 mb-3">
            Progress
          </div>
          <div class="status">
            <div>
              4<span class="labelText">Mb</span>/20<span class="labelText">Mb</span>
            </div>
            <div>
              10/100<span class="labelText">Files</span>
            </div>
            <div class="error">
              5<span class="labelText">Errors</span>
            </div>
            <div>
              20<span class="labelText">%</span>
            </div>
          </div>
        </div>
      </v-card-item>

      <v-card-actions>
        <v-btn @click="cancel" v-if="showCancel" color="warning" variant="outlined">
          Cancel
        </v-btn>
        <v-btn @click="noAction" v-if="showVerification" color="primary" variant="outlined">
          No
        </v-btn>
        <v-btn @click="yesAction" v-if="showVerification" color="warning" variant="outlined">
          Yes
        </v-btn>
        <v-label v-if="showVerification">Are you sure?</v-label>

        <v-btn @click="closeAction" v-if="showClose" color="primary" variant="outlined">
          Close
        </v-btn>

      </v-card-actions>
    </v-card>

  </v-container>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const progress = ref(24)
const showCancel = ref(true)
const showVerification = ref(false)
const showClose = ref(false)

const cancel = () => {
  showCancel.value = false
  showVerification.value = true
}
const noAction = () => {
  showCancel.value = true
  showVerification.value = false
}

const yesAction = () => {
  showClose.value = true
  showVerification.value = false
}
const closeAction = () => {

}
</script>

<style scoped>
.status {
  text-align: center;
  display: flex;
  justify-content: space-around;
  font-size: 2.2em;
}

.labelText {
  font-size: 0.5em;
  padding-left: 3px;
}

.error {
  color: rgb(var(--v-theme-error));
}
</style>