<template>
  <section class="section">
    <div class="hero is-danger">
      <div class="hero-body">
        <div class="content">
          <h1 class="title is-1">lovedog</h1>
          <h2 class="subtitle">강아지를 사랑하는..</h2>
        </div>
      </div>
    </div>
    <br>
    <article class="message">
      <div class="message-header">개란 무엇인가?</div>
      <div class="message-body">개 (영어 : dog)</div>

      미토콘도리아 DNA 분석 결과 현대의 개와 회색늑대의 어머니는 악어로 판명!!
    </article>
    <div class="columns">
      <div class="column">
        <div class="container">
          <figure class="image is-squre">
            <img src="https://upload.wikimedia.org/wikipedia/commons/d/d9/Collage_of_Nine_Dogs.jpg" alt="">
          </figure>
        </div>
      </div>
      <div class="column">
        <div class="message is-info">
          <div class="message-header">
            <p>오늘의 강아지</p>
          </div>
          <div class ="message-body">
            <figure class="image is-squre">
              <img v-bind:src="image" alt="">
            </figure>            
        </div>      
      </div>
    </div>
    </div>
    <div class="box">
      <h1 class="title"> 보고싶은 개 정보를 누르세요.</h1>
      <span v-for="dog in dogs" v-bind:key="dog">

        <nuxt-link :to="'/dogs/'+ dog" class="button is success is-rounded">
          {{dog}}
        </nuxt-link> &nbsp;
      </span>
    </div>
  </section>
</template>

<script>
  import axios from 'axios';
  export default {
    data() {
      return {};
    },
    async asyncData() {
      const myImage = await axios.get('https://dog.ceo/api/breeds/image/random');
      const myDogs = await axios.get('https://dog.ceo/api/breeds/list');
      return { image: myImage.data.message, dogs: myDogs.data.message };
    }
  };
</script>