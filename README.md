(async function() {
    const resp = await fetch('https://api.deepai.org/api/search-and-replace', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
            'api-key': '1234567890abcdef'
        },
        body: JSON.stringify({
            image: "https://example.com/your-image.jpg",
            search_prompt: "Remove the tree",
            prompt: "Add a house instead",
        })
    });
    
    const data = await resp.json();
    console.log(data);
})();
