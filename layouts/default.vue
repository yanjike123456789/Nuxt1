<template>
<div>
    <Header></Header>
  <nuxt/>
    <Footer></Footer>
</div>
</template>

<script>
import Footer from '@/components/footer'
import Header from '@/components/header'
export default {
    components:{
        Header,
        Footer
    }
}
</script>

<style>

</style>