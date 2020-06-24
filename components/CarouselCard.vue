<template>
    <div class="relative">
        <div class="glide glide--ltr glide--slider glide--swipeable">
            <div data-glide-el="track" class="glide__track">
                <ul class="glide__slides">
                    <li class="glide__slide" v-for="picture in pictures">
                        <img class="w-full" :src='picture.url' alt="Casafy">
                    </li>
                </ul>
            </div>
            <div data-glide-el="controls">
                <button data-glide-dir="<" class="glide-control-prev"></button>
                <button data-glide-dir=">" class="glide-control-next"></button>
            </div>
        </div>
    </div>
</template>

<script>
import Glide from '@glidejs/glide';
import "~/node_modules/@glidejs/glide/dist/css/glide.core.min.css";

export default {
    props: ['pictures'],
    mounted () {
        var sliders = document.querySelectorAll('.glide');

        for (var i = 0; i < sliders.length; i++) {
            var glide = new Glide(sliders[i], {
                gap: 15,
            });
            
            glide.mount();
        }
    }
}
</script>

<style>
    img {
        height: 198px;
        object-fit: cover;
        object-position: center;        
    }

    .glide-control-next, .glide-control-prev {
        top: 4.75rem;
        background-color: transparent;
    }

    .glide-control-prev {
        left: 0;
    }

    .glide-control-next {
        right: 0;
    }

    .glide-control-prev:before {
        content: url('https://www.casafy.com.br/back.svg');
    }

    .glide-control-next:before {
        content: url('https://www.casafy.com.br/next.svg');
    }

    .glide-control-next, .glide-control-prev {
        border: none;
        width: 32px;
        height: 60px;
        background: $primary-color;
        position: absolute;
        top: 42%;
    }
</style>