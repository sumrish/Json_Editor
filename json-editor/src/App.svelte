
<script>
  let jsonString = `{
    "name": "John Doe",
    "age": 25,
    "email": "johndoe@example.com"
  }`;

  let isValidJson = true;
  let uploadedFileName = '';

  function handleFileUpload(event) {
    const file = event.target.files[0];
    uploadedFileName = file.name;
    const reader = new FileReader();

    reader.onload = (event) => {
      const contents = event.target.result;
      jsonString = contents;
      validateJson();
    };

    reader.readAsText(file);
  }

  function updateJson(event) {
    jsonString = event.target.value;
    validateJson();
  }

  function validateJson() {
    try {
      JSON.parse(jsonString);
      isValidJson = true;
      jsonString = JSON.stringify(JSON.parse(jsonString), null, 2);
    } catch (error) {
      isValidJson = false;
    }
  }

  function downloadJson() {
    // Check if JSON is valid before downloading
    if (isValidJson) {
      const fileContent = jsonString;
      const blob = new Blob([fileContent], { type: 'application/json' });
      const url = URL.createObjectURL(blob);

      const a = document.createElement('a');
      a.href = url;
      a.download = 'data.json';
      a.click();

      URL.revokeObjectURL(url);
    } else {
      alert('Invalid JSON! Please enter a valid JSON string.');
    }
  }
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Bangers&display=swap');

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 92vh;
    font-family: Arial, sans-serif;
  }

  h1 {
    font-family: 'Bangers', cursive;
    color: #ea0a8e;
	font-size: 48px;
	letter-spacing: 2px;
  }

  .editor-container {
    display: flex;
    align-items: center;
    margin-bottom: 2px;
  }

  .editor {
    width: 400px;
    height: 500px;
    font-family: monospace;
    font-size: 14px;
    padding: 10px;
    border: 2px solid black;
    border-radius: 10px;
    outline: none;
    resize: none;
    box-sizing: border-box;
	margin: 0;
	margin-right: 10px;
  }

  .display {
    width: 400px;
    height: 500px;
    padding: 10px;
    border: 2px solid black;
    border-radius: 10px;
    overflow: auto;
    background-color: #f8f8f8;
    font-family: monospace;
    font-size: 14px;
    white-space: pre-wrap;
	box-sizing: border-box;
	margin: 0;
  }

  .button-container {
    display: flex;
    justify-content: center;
    margin-top: 10px;
	margin-bottom: 10px;

  }

  .upload-button,
  .download-button {
    padding: 10px 20px;
    font-size: 30px;
    background-color: #ea0a8e;
    color: white;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    outline: none;
    margin: 0 5px;
	font-family: 'Bangers', cursive;
	letter-spacing: 2px;
  }

  .upload-label {
    margin-top: 10px;
    color: #ea0a8e;
  }
</style>

<main>

  <div class="container">
    <h1>JSONify</h1>
    <div class="editor-container">
      <textarea class="editor" style="border-color: {isValidJson ? 'inherit' : '#ea0a8e'};" bind:value={jsonString} on:input={updateJson}></textarea>
      <pre class="display">{jsonString}</pre>
    </div>
    <div class="button-container">
      <div>
        <label for="fileInput" class="upload-button">Upload</label>
        <input type="file" id="fileInput" accept=".json" style="display: none" on:change={handleFileUpload} />
      </div>
      <button class="download-button" on:click={downloadJson}>Ready!</button>
    </div>
  </div>
</main>