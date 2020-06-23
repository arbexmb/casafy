<template>
    <header class="header-main lg:relative">
        <div class="flex flex-wrap lg:flex-no-wrap justify-between items-center">
            <div class="flex justify-between items-center w-1/3 md:w-custom-70">
                <div>
                    <nuxt-link to="/">
                        <img src="https://s3-sa-east-1.amazonaws.com/casafy.static/site/v1.1/fiqueemcasa.png" alt="Casafy" class="hidden lg:block lg:h-10 lg:w-auto">
                        <img src="https://s3-sa-east-1.amazonaws.com/casafy.static/site/v1.1/fiqueemcasa.png" alt="Casafy" class="h-8 w-auto lg:hidden">
                    </nuxt-link>
                </div>
                <div class="w-3/5 absolute right-26 hidden md:block">
                    <form>
                        <div class="flex">
                            <div class="w-full max-w-custom flex flex-wrap relative">
                                <div class="vue-tags-input flex-shrink flex-grow flex-auto search-bar">
                                    <input type="text" class="bg-gray-200 appearance-none border-2 border-gray-200 rounded w-full py-2 px-2 text-gray-700 leading-tight focus:outline-none focus:bg-white focus:border-purple-500">
                                </div>
                            </div>
                            <button type="submit" class="btn-search">Buscar</button>
                        </div>
                    </form>
                </div>
            </div>
            <div class="flex justify-between items-center w-2/3 md:w-3/5">
                <div class="z-0 w-full inset-x-0 opacity-90 lg:block hidden text-gray-600">
                    <nav class="text-base md:text-sm font-normal md:font-semibold">
                        <ul class="lg:flex lg:justify-end items-center">
                            <li class="pt-3 pb-1 lg:pt-0 lg:pb-0">
                                <a href="#" class="uppercase no-underline ml-4">sobre casify</a>
                            </li>
                            <li class="pt-3 pb-1 lg:pt-0 lg:pb-0">
                                <a href="#" class="uppercase no-underline ml-4">busca</a>
                            </li>
                            <li class="pt-3 pb-1 lg:pt-0 lg:pb-0">
                                <a href="#" class="uppercase no-underline ml-4">blog</a>
                            </li>
                            <li class="pt-3 pb-1 lg:pt-0 lg:pb-0">
                                <a href="#" class="uppercase no-underline ml-4">ajuda</a>
                            </li>
                            <li class="hidden lg:block">
                                <a href="#" class="red-bg-btn-menu ml-4 bg-red-500 text-white font-semibold">anuncie seu imóvel</a>
                            </li>
                            <li class="pt-3 pb-1 lg:pt-0 lg:pb-0">
                                <a href="#" class="uppercase no-underline ml-4">cadastre-se</a>
                            </li>
                            <li class="pt-3 pb-1 lg:pt-0 lg:pb-0">
                                <a href="#" class="uppercase no-underline ml-4">entrar</a>
                            </li>
                        </ul>
                    </nav>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    
}
</script>

<style>
    img {
        max-width: 100%;
    }

    .header-main {
        transition: all .1s ease-out;
        transform: translateZ(0);
        position: fixed;
        top: 0;
        right: 0;
        left: 0;
        --bg-opacity: 1;
        background-color: #fff;
        background-color: rgba(255,255,255,var(--bg-opacity));
        box-shadow: 0 3px 6px rgba(0,0,0,.16078);
        padding: .25rem .75rem;
        z-index: 50;
    }

    .right-26 {
        right: 26rem;
    }

    .lg\:h-10 {
        height: 2.5rem;
    }

    .btn-search {
        left: -5px;
        z-index: 999!important;
        display: flex;
        justify-content: center;
        align-items: center;
        --text-opacity: 1;
        color: #fff;
        color: rgba(255,255,255,var(--text-opacity));
        font-size: .875rem;
        --bg-opacity: 1;
        background-color: #fc6360;
        background-color: rgba(252,99,96,var(--bg-opacity));
        border-width: 1px;
        --border-opacity: 1;
        border-color: #fc6360;
        border-color: rgba(252,99,96,var(--border-opacity));
        padding-left: .75rem;
        padding-right: .75rem;
        border-top-right-radius: .5rem;
        border-bottom-right-radius: .5rem;
        font-family: Open Sans,-apple-system,BlinkMacSystemFont,Segoe UI,Roboto,Helvetica Neue,Arial,Noto Sans,sans-serif,Apple Color Emoji,Segoe UI Emoji,Segoe UI Symbol,Noto Color Emoji;
        text-transform: uppercase;
        font-weight: 600;
    }

    .max-w-custom {
        max-width: 25rem;
    }

    .red-bg-btn-menu {
        padding: .25rem .5rem;
        border-radius: .25rem;
        text-transform: uppercase;
    }

    .text-white {
        --text-opacity: 1;
        color: #fff;
        color: rgba(255,255,255,var(--text-opacity));
    }
</style>