<template>
  <div class="flex items-center justify-center">
    <h2>Download File in Vue Js using Axios</h2>
  </div>
  <div class="p-4 m-4">
    <button class="bg-blue-500 text-white p-4" @click="downloadFile()">
      DownLoad
    </button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "DownloadFile",
  methods: {
    downloadFile() {
      axios({
        url: "/media/one%20/home/Eupatridae/pdf_preview/media/92/one%20/one_.pdf", // download file link goes here
        method: "GET",
        headers: {
          "Content-Type": "application/x-www-form-urlencoded",
          "Access-Control-Allow-Origin": "http://localhost:8080/",
        },
        responseType: "blob",
      }).then((res) => {
        var FILE = window.URL.createObjectURL(new Blob([res.data]));

        var docUrl = document.createElement("a");
        docUrl.href = FILE;
        docUrl.setAttribute("download", "sample.pdf");
        document.body.appendChild(docUrl);
        docUrl.click();
      });
    },
  },
};
</script>
