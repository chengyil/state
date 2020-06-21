<template>
  <v-sheet width="70vw" elevation="4" class="d-flex mx-auto mt-8">
    <v-container>
      <v-row>
        <v-col>
          <h1 class="text-center">Upload Files</h1>
        </v-col>
      </v-row>
      <v-row
        align="stretch"
        class="file-action"
        @drop.prevent="addFile"
        @dragover.prevent
      >
        <v-col cols="6">
          <v-simple-table>
            <template>
              <thead>
                <td class="text-center">
                  File Name
                </td>
                <td class="text-center">
                  File Size
                </td>
              </thead>
              <tbody>
                <tr v-for="(item, index) in files" :key="index">
                  <td>{{ item.name }}</td>
                  <td>{{ item.size }} Bytes</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
        </v-col>
        <v-col cols="6">
          <div class="drop">
            <p class="message text-center">Upload your file here</p>
          </div>
        </v-col>
      </v-row>
    </v-container>
  </v-sheet>
</template>
}
<script>
export default {
  name: "Home",
  methods: {
    addFile(e) {
      const droppedFiles = e.dataTransfer.files;
      if (!droppedFiles) {
        return;
      }

      droppedFiles.forEach(file => {
        this.files.push(file);
      });
    }
  },
  data() {
    return {
      files: []
    };
  }
};
</script>

<style lang="scss" scoped>
.drop {
  border: 3px dashed black;
  height: 100%;
  width: 100%;
  position: relative;
}
.message {
}
.file-action {
  min-height: 80px;
}
</style>
