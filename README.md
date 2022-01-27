# Javascript Picture in Picture
```javascript
// Get Elements
const videoElement = document.getElementById("video");
const button = document.getElementById("button");

// Prompt to select media stream, pass to video element, then play
async function seleMedieaStream() {
  try {
    const mediaStream = await navigator.mediaDevices.getDisplayMedia();
    videoElement.srcObject = mediaStream;
    videoElement.onloadedmetadata = () => {
      videoElement.play();
    };
  } catch (error) {
    // catch errors
    console.log("Whoa, somthing is not right here", error);
  }
}

// Add Event Listener
button.addEventListener("click", async () => {
  // Disable button
  button.disabled = true;
  // Start Picture in Picture
  await videoElement.requestPictureInPicture();
  // Reset Button
  button.disabled = false;
});

// On Load
seleMedieaStream();
```