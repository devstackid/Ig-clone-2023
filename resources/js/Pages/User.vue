<script setup>
    import { reactive, toRefs } from 'vue'
    import { Head, Link, router } from '@inertiajs/vue3';
    import MainLayout from '@/Layouts/MainLayout.vue';

    import Cog from 'vue-material-design-icons/Cog.vue';
    import Grid from 'vue-material-design-icons/Grid.vue';
    import PlayBoxOutline from 'vue-material-design-icons/PlayBoxOutline.vue';
    import BookmarkOutline from 'vue-material-design-icons/BookmarkOutline.vue';
    import AccountBoxOutline from 'vue-material-design-icons/AccountBoxOutline.vue';

    let data = reactive({ post: null })
    const form = reactive({ file: null })

    const props = defineProps({ postByUser: Object, user: object })
    const { postByUser, user } = toRefs(props)

    const getUploadedImage = (e) => {
    form.file = e.target.files[0]
    router.post('/users', form, {
        preserveState: false
    })
}
</script>

<template>
    <Head title="Ig" />

    <MainLayout>
        <div class="pt-2 md:pt-6"></div>
        <div class="max-w-[880px] lg:ml-0 md:ml-[80px] md:pl-20 px-4 2-[100vw]">

            <label for="fileUser">
                <img class="rounded-full object-fit md:w-[200px] w-[100px] cursor-pointer" src="http://picsum.photos/id/8/300/320" >
            </label>
            <input 
                id="fileUser"
                class="hidden"
                type="file"
                @input="$event => getUploadedImage($event)"
            >

        </div>
    </MainLayout>
</template>





