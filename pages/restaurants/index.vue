<template>
    <div>
        <Html lang="hu-HU">
        
        <Head>
            <Title>Top 50 restaurants</Title>
            <Meta name="description" content="My page is cool" />
            <Link rel="preload" href="https://cdn-icons-png.flaticon.com/512/3585/3585640.png" as="script" />
        </Head>
        
        </Html>
     <NuxtLayout name="custom">
        <div class="container">
            <RestaurantTable />
        </div>
     </NuxtLayout>
    </div>
</template>