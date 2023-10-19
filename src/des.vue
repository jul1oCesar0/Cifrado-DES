<template>
    <div>
      <center>
        <div>
          <fieldset id="container" class="small-container">
            <legend>Cifrado de Escítala</legend>
            <label class="label" for="text">Texto a cifrar</label>
            <input v-model="text" id="text" class="input" placeholder="Ingrese el texto">
            <br><br>
            <label class="label" for="key">Clave de cifrado</label>
            <input v-model="key" id="key" class="number" placeholder="Clave de cifrado">
            <br><br>
            <button @click="encrypt" class="custom-button">Cifrar</button>
            <button @click="decrypt" class="custom-button descifrar">Descifrar</button>
            <h2 class="subtitle">Resultado:</h2>
            <p class="result">{{ result }}</p>
          </fieldset>
        </div>
      </center>
    </div>
  </template>
  
  
  <script>
  import CryptoJS from 'crypto-js';
  
  export default {
    data() {
      return {
        text: "",
        key: "",
        result: "",
      };
    },
    methods: {
      encrypt() {
        if (this.text && this.key) {
          const encrypted = CryptoJS.DES.encrypt(this.text, this.key);
          this.result = encrypted.toString();
        }
      },
      decrypt() {
        if (this.text && this.key) {
          const decrypted = CryptoJS.DES.decrypt(this.text, this.key);
          this.result = decrypted.toString(CryptoJS.enc.Utf8);
        }
      },
    },
  };
  </script>
  
  <style>
  .title {
    font-size: 40px;
  }

  .label {
    display: block;
    font-weight: bold;
    margin-bottom: 25px;
  }

  .input {
    width: 50%;
    padding: 8px;
    margin-bottom: 9px;
    border: 1px solid #ccc;
    border-radius: 5px;
    font-size: 16px;
    text-align: center;
  }

  .custom-button {
    background-color: #007BFF;
    color: #fff;
    padding: 10px 20px;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-right: 10px;
  }

  .custom-button.descifrar {
    background-color: red;
  }

  .custom-button:hover {
    background-color: #0056b3;
  }

  .subtitle {
    font-size: 24px;
    font-weight: bold;
    margin-bottom: 20px;
  }


  .small-container {
  width: 80%; 
  max-width: 400px; 
  padding: 20px;
  border: 2px solid #07080a;
  border-radius: 10px;
  text-align: center;
  margin: 0 auto;
  background-color: #32c6f7;
}
</style>
