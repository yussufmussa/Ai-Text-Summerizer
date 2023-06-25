<template>
    <div class="flex justify-center items-center min-h-screen">
      <div class="max-w-md w-full bg-white shadow-lg rounded-lg p-6">
        <h1 class="text-2xl font-bold mb-4">Shorten Your Text</h1>
        <textarea v-model="inputText" class="w-full h-40 mb-4 p-2 rounded-md" placeholder="Enter your text..."></textarea>
        <button @click="shortenText" class="w-full bg-teal-500 hover:bg-teal-700 text-white font-bold py-2 px-4 rounded">
        <span v-if="loading">Loading...</span>
        <span v-else>Shorten Text</span>
        </button>
        <div v-if="shortenedText" class="mt-4">
          <h2 class="text-xl font-bold mb-2">Shortened Text:</h2>
          <p>{{ shortenedText }}</p>
        </div>
      </div>
    </div>
  </template>

<script>
import axios from 'axios';

export default {
    data() {
        return {
            inputText: '',
            shortenedText: '',
            loading: false,
        };
    },
    methods: {
        async shortenText() {
            this.loading = true;
            try {
                const response = await axios.post('https://tldrthis.p.rapidapi.com/v1/model/abstractive/summarize-text/', {
                    text: this.inputText,
                    min_length: 100,
                    max_length: 300,
                }, {
                    headers: {
                        'content-type': 'application/json',
                        'X-RapidAPI-Key': '2efda3b728msh32adae685147d60p1e5ff5jsn03dabe02ac2f',
                        'X-RapidAPI-Host': 'tldrthis.p.rapidapi.com'
                    },
                });

                this.shortenedText = response.data.summary;
                console.log(response.data.summary);
            } catch (error) {
                console.error(error);
            }finally{
                this.loading = false;
            }
            
        },
    },
};
</script>


