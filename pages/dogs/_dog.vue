<template>
        <section class="section">
            <article class="hero is-info">
                <div class="hero-body">
                    <div class="container">
                        <h1 class="title">규호는 {{dogName.toUpperCase()}}입니다.</h1>
                        <h2 class="subtitle">잠이 많이부족합니다 재워주세요.</h2>
                    </div>
                </div>
            </article>
            <article class="notification is-success">
                <div class="columns">
                    <div v-for="image in images" :key="image" class="column">
                        <figure class="image is-square">
                            <img :src="image" alt="">
                        </figure>
                    </div>
    
                </div>
            </article>
        </section>
    </template>
    <script>
        import axios from 'axios';
        export default {
            async asyncData({ params }) {
                let maxImg = 4;
                let images = [];
                for (let i = 0; i < maxImg; i++) {
                    const image = await axios.get(`https://dog.ceo/api/breed/${params.dog}/images/random`);
                    images.push(image.data.message);
                }

                const list = axios.get('http://dog.ceo/api/breed/${params.dog}/');
                return {
                    dogName: params.dog,
                    images: images,
                    dogList : list.data.message
                };
            }
        };
    </script>