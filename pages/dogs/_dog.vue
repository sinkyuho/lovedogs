<template>
    <section class="section">
        <article class="hero">
            <div class="hero-body">
                <div class="container">
                    <h1 class="title">규호는 {{dogName}} 입니다.</h1>

                </div>
            </div>
        </article>
        {{dogName}}
    </section>
</template>
<script>
    export default {
        asyncDate({ params }) {
            return {
                dogName: params.dog
            };
        }
    }
</script>