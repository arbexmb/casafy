<template>
    <div class="relative">
        <div class="glide glide--ltr glide--slider glide--swipeable">
            <div data-glide-el="track" class="glide__track">
                <ul class="glide__slides">
                    <li class="glide__slide" v-for="picture in pictures">
                        <div class="stamp" v-if='property_status && property_status == 3'>
                            <img src="https://image.casafy.com/site/v1.1/gold.svg" class="symbol">
                            <p class="gold">100% verificado</p>
                        </div>
                        <div class="stamp" v-if='property_status && property_status == 2'>
                            <img src="https://image.casafy.com/site/v1.1/silver.svg" class="symbol">
                            <p class="silver">Matrícula verificada</p>
                        </div>
                        <div class="stamp" v-if='property_status && property_status == 8'>
                            <img src="https://image.casafy.com/site/v1.1/initial.svg" class="symbol">
                            <p class="initial">Em validação</p>
                        </div>
                        <img class="w-full slider-img" :src='picture.url' alt="Casafy">
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
    props: ['pictures', 'property_status'],
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
        max-width: 100%;   
    }

    .slider-img {
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

    .stamp {
        position: absolute;
        opacity: .85;
        width: 13rem;
    }

    .stamp p {
        font-weight: 600;
        --text-opacity: 1;
        color: #fff;
        color: rgba(255,255,255,var(--text-opacity));
        font-size: .75rem;
        text-align: right;
        letter-spacing: .05em;
        text-transform: uppercase;
        padding: .5rem;
        height: 2.0625rem;
    }

    .stamp .gold {
        --bg-opacity: 1;
        background-color: #87632e;
        background-color: rgba(135,99,46,var(--bg-opacity));
        padding-right: 2rem;
    }

    .stamp .silver {
        --bg-opacity: 1;
        background-color: #555;
        background-color: rgba(85,85,85,var(--bg-opacity));
    }

    .stamp .initial {
        --bg-opacity: 1;
        background-color: #fc6360;
        background-color: rgba(252,99,96,var(--bg-opacity));
        padding-right: 2.25rem;
    }

    .symbol {
        position: absolute;
        margin-top: .5rem;
        margin-left: .5rem;
        width: 39px;
    }
</style>