<template>
  <div class="about">
    <!-- <h1>REGISTER</h1> -->
    <div class="register">
      <form id="form2" action="" method="post">
        <label for="matric"> MATRIC NO*</label>

        <input
          name="Matric"
          id="matric"
          type="text"
          placeholder="Your answer"
        />
        <br />

        <label for="name"> FULL NAME*</label>

        <input
          name="fullname"
          id="name"
          type="text"
          placeholder="lastname      firstname"
        />
        <br />
        <label for="mail2"> YOUR EMAIL*</label>

        <input
          name="email"
          id="mail2"
          type="email"
          placeholder="johndoe@gmail.com"
        />
        <br />
        <label for="lvl">LEVEL*</label>
        <br />

        <select name="level" id="lvl">
          <option value="100">100</option>
          <option value="200">200</option>
          <option value="300">300</option>
          <option value="400">400</option>
          <option value="500">500</option>
        </select>
        <br />

        <video id="player" autoplay></video>
        <br />
        <a id="download">Download</a>
        <button id="stop">Stop</button>

        <!-- <button id="submitBtn">submit</button>
        <button>yayyyy</button> -->
      </form>
    </div>
  </div>
</template>

<script>
// const player = document.getElementById("#player");

// const handleSuccess = function (stream) {
//   player.srcObject = stream;
// };

// navigator.mediaDevices
//   .getUserMedia({ audio: true, video: true })
//   .then(handleSuccess);

// context.drawImage(myVideoElement, 0, 0);
// export default {
//   mounted() {
//     this.initVideoRecorder();
//   },
//   methods: {
//     async initVideoRecorder() {
//       const player = document.getElementById("player");

//       if (!player) {
//         console.error('Could not find element with ID "player"');
//         return;
//       }

//       try {
//         const stream = await navigator.mediaDevices.getUserMedia({
//           audio: true,
//           video: true,
//         });
//         player.srcObject = stream;
//       } catch (error) {
//         console.error("Error accessing media devices:", error);
//       }
//     },
//   },
// };
// let shouldStop = false;
// let stopped = false;
// const downloadLink = document.getElementById("download");
// const stopButton = document.getElementById("stop");

// stopButton.addEventListener("click", function () {
//   shouldStop = true;
// });

// var handleSuccess = function (stream) {
//   const options = { mimeType: "video/webm" };
//   const recordedChunks = [];
//   const mediaRecorder = new MediaRecorder(stream, options);

//   mediaRecorder.addEventListener("dataavailable", function (e) {
//     if (e.data.size > 0) {
//       recordedChunks.push(e.data);
//     }

//     if (shouldStop === true && stopped === false) {
//       mediaRecorder.stop();
//       stopped = true;
//     }
//   });

//   mediaRecorder.addEventListener("stop", function () {
//     downloadLink.href = URL.createObjectURL(new Blob(recordedChunks));
//     downloadLink.download = "acetest.webm";
//   });

//   mediaRecorder.start();
// };

// navigator.mediaDevices
//   .getUserMedia({ audio: true, video: true })
//   .then(handleSuccess);

// const player = document.getElementById("player");

// if (!player) {
//   console.error('Could not find element with ID "player"');
// } else {
//   console.log('Element with ID "player" exists.');
// }

export default {
  mounted() {
    this.initVideoRecorder();
  },
  methods: {
    async initVideoRecorder() {
      const player = document.getElementById("player");
      const downloadLink = document.getElementById("download");
      const stopButton = document.getElementById("stop");

      if (!player) {
        console.error('Could not find element with ID "player"');
        return;
      }

      // Check if stopButton and downloadLink exist
      if (!stopButton) {
        console.error('Could not find element with ID "stop"');
        return;
      }
      if (!downloadLink) {
        console.error('Could not find element with ID "download"');
        return;
      }

      try {
        const stream = await navigator.mediaDevices.getUserMedia({
          audio: true,
          video: true,
        });

        console.log(stream);
        player.srcObject = stream;

        // Setup video recording
        let shouldStop = false;
        let stopped = false;
        let mediaRecorder;

        stopButton.addEventListener("click", function () {
          shouldStop = true;
        });

        const handleSuccess = function (stream) {
          const options = { mimeType: "video/webm" };
          const recordedChunks = [];
          mediaRecorder = new MediaRecorder(stream, options);

          mediaRecorder.addEventListener("dataavailable", function (e) {
            if (e.data.size > 0) {
              recordedChunks.push(e.data);
            }

            if (shouldStop === true && stopped === false) {
              mediaRecorder.stop();
              stopped = true;
            }
          });

          mediaRecorder.addEventListener("stop", function () {
            const blob = new Blob(recordedChunks, { type: "video/webm" });
            const url = URL.createObjectURL(blob);
            downloadLink.href = url;
            downloadLink.download = "recorded-video.webm";
          });

          mediaRecorder.start();
        };

        handleSuccess(stream);
      } catch (error) {
        console.error("Error accessing media devices:", error);
      }
    },
  },
};
</script>

<style>
#form2 label {
  display: inline-block;
  /* margin: 1em; */
}

#form2 input {
  width: 60%;
  padding: 1.5em 3em;
  margin: 1em;
  border-radius: 1em;
  background-color: rgba(255, 255, 255, 0.236);
  outline: none;
  border: none;
}

#lvl {
  display: inline-block;
}
#scan {
  margin: 1em;
  width: 15%;
  padding: 1em;
  border-radius: 2em;
  border: none;
  background-color: rgba(255, 255, 255, 0.241);
}

#submitBtn {
  margin: 1em;
}
</style>
