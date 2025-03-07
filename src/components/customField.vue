<template>
    <v-container>
        <v-card>
            <v-progress-linear :model-value="progress" height="20" location="top" absolute color="primary">
                20%
            </v-progress-linear>

            <v-card-item style="background-color: rgba(var(--v-theme-background),0.7);">
                <div class="text-h6" style="padding-top: 10px;">
                    Progress
                </div>
                <div class="status text-h6">

                    <v-card class="item" elevation="2">
                        <div style="font-size: .7em; color: rgb(var(--v-theme-on-code));">
                            Transferred
                        </div>
                        <div>
                            4<span class="labelText">Mb</span>
                        </div>
                        <div style="font-size: .8em;color: rgba(var(--v-theme-info), 0.8);">
                            Total size 20<span class="labelText">Mb</span>
                        </div>
                    </v-card>

                    <v-card class="item" elevation="2">
                        <div style="font-size: .7em; color: rgb(var(--v-theme-on-code));">
                            Transferred
                        </div>
                        <div>
                            10 <span class="labelText">Files</span>
                        </div>
                        <div style="font-size: .8em;color: rgba(var(--v-theme-info), 0.8);">
                            Total files 100
                        </div>
                    </v-card>

                    <v-card class="item error" elevation="2">
                        <div style="font-size: .7em;">
                            Errors
                        </div>
                        <div>
                            10
                        </div>
                    </v-card>

                    <v-card class="item" style="min-width: 320px;" elevation="2">
                        <div style="font-size: .7em; color: rgb(var(--v-theme-on-code));">
                            External storage device Free Space
                        </div>
                        <div>
                            100<span class="labelText">Mb</span>
                        </div>
                        <div style="font-size: .8em;color: rgba(var(--v-theme-info), 0.8);">
                            Usb drive (E:) total size 100<span class="labelText">Mb</span>
                        </div>

                    </v-card>
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
    justify-content: space-evenly;
    flex-wrap: wrap;
    gap: 20px;
    /* font-size: 2.2em; */
}

.item {
    padding: 10px;
    min-width: 120px;
    max-width: 50%;
    text-align: center;
    height: 100px;
}

.labelText {
    font-size: 0.7em;
    padding-left: 3px;
}

.error {
    color: rgb(var(--v-theme-error));
}

.no-select {
    user-select: none;
    pointer-events: none;
}
</style>