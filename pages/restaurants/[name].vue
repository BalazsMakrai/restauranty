<template>
    <div>
        <Html lang="hu-HU">

        <Head>
            <Title>{{ title }}</Title>
            <Meta name="description" content="My page is cool" />
            <Link rel="preload" href="https://cdn-icons-png.flaticon.com/512/3585/3585640.png" as="script" />
        </Head>

        </Html>
        <NuxtLayout name="custom" v-if="restaurant">
            <div class="restaurant-container">
                <div class="image-container">
                    <img :src="restaurant?.imageUrl">
                </div>
                <div class="info-container">
                    <h1>{{ restaurant?.name }}</h1>
                    <div class="stats-container">
                        <h5>Revenue (in billions)</h5>
                        <p>$ {{ restaurant?.revenue }}</p>
                    </div>
                    <div class="stats-container">
                        <h5>Number of stores</h5>
                        <p>{{ restaurant?.numberOfStores }}</p>
                    </div>
                    <p class="content">{{ restaurant?.content }}</p>
                </div>
            </div>
        </NuxtLayout>
        <div v-else class="restaurant-not-found">
            <h1>Restaurant not found</h1>
        </div>
    </div>
</template>

<script setup lang="ts">
import restaurants from '@/data.json';
const route = useRoute();
const name = route.params.name;
const restaurant = restaurants.find(r => r.name === name);
const title = ref(name);
if (!restaurant) {
    title.value = 'Restaurant not found';
}

</script>

<style scoped>
.restaurant-container {
    display: flex;
}

.image-container {
    height: 95vh;
    width: 75%
}

.image-container img {
    width: 100%;
    height: 100%;
}

.restaurant-not-found {
    height: 75vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

.info-container {
    padding: 3rem;
    width: 50%;
}

.info-container h1 {
    text-transform: uppercase;
    font-size: 6rem;
    margin-bottom: 3rem;
}

.stats-container h5 {
    width: 20rem;
    font-size: 2rem;
    margin: 0;
    margin-right: 5rem;
}

.stats-container p {
    margin: 0;
    font-size: 2rem;
}

.content {
    font-size: 1.5rem;
    margin-top: 4rem;
}
</style>