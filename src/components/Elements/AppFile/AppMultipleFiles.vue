<template>
  <div class="container">
    <div class="large-12 medium-12 small-12 cell">
      <label>Files
        <input type="file" id="files" ref="files" multiple @change="handleFilesUploads()"/>
      </label>
      <div class="large-12 medium-12 small-12 cell">
        <button @click="addFiles()">Add Files</button>
      </div>
      <div class="large-12 medium-12 small-12 cell">
        <div v-for="(file, index) in files" :key="file.name" class="file-listing">
          {{ file.name }}
          <span class="remove-file" @click="removeFile(index)">Remove</span>
        </div>
      </div>
      <br>
      <button @click="submitFiles()">Submit</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppMultipleFiles",
  data(){
    return {
      files: []
    }
  },
  methods: {
    addFiles(){
      this.$refs.files.click();
    },
    handleFilesUploads(){
      let uploadedFiles = this.$refs.files.files;
      for( let i = 0; i < uploadedFiles.length; i++ ){
        this.files.push(uploadedFiles[i]);
      }
    },
    submitFiles() {
      let formData = new FormData();
      formData.append('file', this.file);
      console.log('formData', formData)
      for( let i = 0; i < this.files.length; i++ ){
        let file = this.files[i];
        formData.append('files[' + i + ']', file);
      }
    },
    removeFile( index ){
      console.log('key', index)
      console.log('this.files', this.files.length)
      this.files.splice( index, 1 );
    }
  }
}
</script>

<style scoped>
input[type="file"]{
  position: absolute;
  top: -500px;
}
</style>
