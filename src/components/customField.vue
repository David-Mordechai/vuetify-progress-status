<template>
    <v-container>
        <v-card>
            <v-progress-linear :model-value="progress" height="20" location="top" color="primary">
                20%
            </v-progress-linear>

            <v-card-item class="wrapper">
                <div class="items text-h6">

                    <v-card class="item" elevation="1">
                        <div class="itemTitle">
                            Transferred
                        </div>
                        <div>
                            4<span class="measure">Mb</span>
                        </div>
                        <div class="itemInfo">
                            Total 20<span class="measure">Mb</span>
                        </div>
                    </v-card>

                    <v-card class="item" elevation="1">
                        <div class="itemTitle">
                            Transferred
                        </div>
                        <div>
                            10 <span class="measure">Files</span>
                        </div>
                        <div class="itemInfo">
                            Total 100
                        </div>
                    </v-card>

                    <v-card class="item" elevation="1">
                        <div class="itemTitle">
                            External storage free space
                        </div>
                        <div>
                            100<span class="measure">Mb</span>
                        </div>
                        <div class="itemInfo">
                            Total 100<span class="measure">Mb</span>
                        </div>
                    </v-card>

                    <v-card class="item" elevation="1">
                        <div class="itemTitle">
                            Errors
                        </div>
                        <div class="error">
                            10
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
.wrapper {
    background-color: rgba(var(--v-theme-background), 0.7);
}

.items {
    text-align: center;
    display: flex;
    justify-content: space-around;
    flex-wrap: wrap;
    gap: 10px;
}

.item {
    padding: 10px 5px;
    min-width: 200px;
    text-align: center;
    height: 100px;
}

.itemTitle {
    font-size: .7em;
    color: rgb(var(--v-theme-on-code));
}

.itemInfo {
    font-size: .8em;
    color: rgba(var(--v-theme-info), 0.8);
}

.measure {
    font-size: 0.7em;
    padding-left: 3px;
}

.error {
    color: rgb(var(--v-theme-error));
}
</style>