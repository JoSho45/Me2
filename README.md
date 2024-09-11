// Example posting a image URL:
(async function() {
    const resp = await fetch('https://api.deepai.org/api/search-and-replace', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'api-key': 'YOUR_API_KEY'
        },
        body: JSON.stringify({
            image: "YOUR_IMAGE_URL",
            search_prompt: "YOUR_IMAGE_URL",
            prompt: "YOUR_IMAGE_URL",
        })
    });
    
const data = await resp.json();
console.log(data);
})()


// Example posting file picker input image (Browser only):
document.getElementById('yourFileInputId').addEventListener('change', async function() {
       const formData = new FormData();
       formData.append('image', this.files[0]);
       formData.append('search_prompt', this.files[1]);
       formData.append('prompt', this.files[2]);

   const resp = await fetch('https://api.deepai.org/api/search-and-replace', {
       method: 'POST',
       headers: {
           'api-key': 'YOUR_API_KEY'
       },
       body: formData
   });

   const data = await resp.json();
   console.log(data);
});

// Example posting a local image file (Node.js only):
const fs = require('fs');
(async function() {
       const formData = new FormData();
       const jpgFileStream = fs.createReadStream("/path/to/your/file.jpg"),
       formData.append('image', jpgFileStream);
       const txtFileStream = fs.createReadStream("/path/to/your/file.txt"),
       formData.append('search_prompt', txtFileStream);
       const txtFileStream = fs.createReadStream("/path/to/your/file.txt"),
       formData.append('prompt', txtFileStream);

   const resp = await fetch('https://api.deepai.org/api/search-and-replace', {
       method: 'POST',
       headers: {
           'api-key': 'YOUR_API_KEY'
       },
       body: formData
   });

   const data = await resp.json();
   console.log(data);
});
