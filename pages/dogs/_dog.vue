<template>
    <section class="section">
        <article class="hero is-info">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">저는 {{dogName.toUpperCase()}}입니다.</h1>
                    <h2 class="subtitle">많이 사랑해주세요!</h2>
                </div>
            </div>
        </article>

    </section>
</template>
<script>
    export default {
        async asyncData({ params }) {
            const image = await axios.get(`'https://dog.ceo/api/breead/${parms.dog}/images/random');
            return {
                dogName: params.dog,
                image: image.data.message
            };
        }
    };
</script>