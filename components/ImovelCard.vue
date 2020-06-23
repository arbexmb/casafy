<template>
    <div class="card">
        <div class="relative">
            <img class="w-full" :src='checkThumbnail(thumbnail)' alt="Casafy">
        </div>
        <div class="p-3">
            <div class="border-b pb-3">
                <div class="flex flex-wrap items-center">
                    <h5 class="w-3/5 text-base text-gray-700 font-bold leading-none">{{ (price !== null) ? 'R$ ' + priceFormatter(price) : 'Preço indefinido' }}</h5>
                    <h5 class="w-2/5 valid text-right">{{ title }}</h5>
                    <br>
                </div>
                <p class="text-xs text-red-500 font-semibold uppercase leading-none">{{ property_type }}</p>
                <p class="text-base text-gray-600 font-semibold mb-2">{{ page_title }}</p>
                <div class="flex items-center text-sm text-gray-600 font-light italic">
                    <span class="material-design-icon material-icons">place</span>
                    <span>{{ addThreeDots(full_address) }}</span>
                </div>
            </div>
        </div>
        <div class="flex flex-row justify-start items-center px-3 pb-3">
            <p class="flex items-center text-sm text-gray-600 font-light mr-4" v-if="surface_area !== null && surface_area[0] !== 0">
                <span class="material-design-icon material-icons">house</span>
                &nbsp;{{ surface_area[0] }}m²
            </p>
            <p class="flex items-center text-sm text-gray-600 font-light" v-if="bedrooms !== null && bedrooms[0] !== 0">
                <span class="material-design-icon material-icons">airline_seat_flat</span>
                &nbsp;{{ bedrooms[0] }} quarto{{ typeof bedrooms[0] !== 'undefined' && bedrooms[0] > 1 ? 's' : '' }}
            </p>
        </div>
    </div>
</template>

<script>
export default {
    props: ['thumbnail', 'price', 'title', 'property_type', 'page_title', 'full_address', 'surface_area', 'bedrooms'],
    methods: {
        priceFormatter (num) {
            if(num !== null) {
                const arr = num.toFixed(0).split('');
                const rev = arr.reverse().join('');
                const points = rev.replace(/(.{3})/g, "$1.");
                let formatted;
                (points.substring(points.length-1) == '.') ? formatted = points.replace(/.$/, '') : formatted = points;
                const arr2 = formatted.split('');
                return arr2.reverse().join('');
            } else {
                return null;
            }
        },
        addThreeDots(str) {
            return str.substring(0, 50) + '...';
        },
        checkThumbnail(url) {
            if(!url) {
                return '/no_img.jpg';
            }
            return url;
        }
    }
}
</script>

<style scoped>
    .card {
        max-width: 18rem;
        min-height: 100%;
        width: 100%;
        box-shadow: 0 2px 2px rgba(0,0,0,.2);
        border-radius: .25rem;
        --bg-opacity: 1;
        background-color: #fff;
        background-color: rgba(255,255,255,var(--bg-opacity));
        overflow: hidden;
        cursor: pointer;
    }

    img {
        height: 198px;
        object-fit: cover;
        object-position: center;        
    }

    .valid {
        letter-spacing: 0;
        line-height: 1;
        --text-opacity: 1;
        color: #3ea7a7;
        color: rgba(62,167,167,var(--text-opacity));
        padding: 0;
        font-size: .75rem;
        text-transform: uppercase;
        font-weight: 600;
    }
    
    .material-icons {
        font-size: 36px;
    }

    .material-design-icon {
        display: inline-flex;
        align-self: center;
        position: relative;
        height: 1em;
        width: 1em;
    }
</style>