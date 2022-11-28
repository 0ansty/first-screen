<script setup lang="ts">
import {d} from "vite-node/types-257c4f87";

const list: Array<object> = [
    {
        url: '/',
        name: 'Home',
    },
    {
        url: '/about',
        name: 'About',
        isActive: true,
    },
    {
        url: '/courses',
        name: 'Courses',
    },
    {
        url: '/blog',
        name: 'Blog'
    }
];

const mousePosition = reactive({
    clientX: 0,
    clientY: 0,
    width: 0,
    height: 0
});

onMounted(() => {
    mousePosition.width = window.innerWidth / 2;
    mousePosition.height = window.innerHeight / 2;
    window.document.addEventListener('mousemove', onMouseMove)
})

function onMouseMove(e: MouseEvent) {
    mousePosition.clientX = e.clientX;
    mousePosition.clientY = e.clientY;
}

const plateStyleList = computed(() => (pos: string) => {
    switch (pos) {
        case 'top':
            return {
                transform: `translate3d(${(mousePosition.clientX - mousePosition.width) * .01}px, ${(mousePosition.clientY - mousePosition.height) * .01}px, 0)`,
            };
        case 'bottom':
            return  {
                transform: `translate3d(-${(mousePosition.clientX - mousePosition.width) * .03}px, -${(mousePosition.clientY - mousePosition.height) * .03}px, 0)`,
            };
    }
});
</script>
<template>
    <div :class="$style.App">
        <header :class="$style.header">
            <div :class="$style.container">

                <div :class="$style.logo">Logo</div>

                <ul :class="$style.list">
                    <li v-for="item in list"
                        :key="item.url"
                        :class="$style.item"
                    >
                        <NuxtLink :to="item.url" :class="[$style.link, { [$style['--is-active']]: item.isActive }]">
                            {{ item.name }}
                        </NuxtLink>
                    </li>
                </ul>

                <div :class="$style.actions">
                    <UiButton color="yellow" outline>
                        Sign in
                    </UiButton>

                    <UiButton>
                        Start now
                    </UiButton>
                </div>
            </div>
        </header>

        <main :class="$style.main">
            <div :class="$style.container">
                <section :class="$style.first">

                    <aside :class="$style.aside">

                        <div :class="$style.label">
                            😁 Welcome to our school
                        </div>

                        <div :class="$style.title">
                            New way to learn English language
                        </div>

                        <div :class="$style.text">
                            Lörem ipsum melig dänesade, i stenoda i heminäbelt då negon. Polyfuss. Nende ejära i doledes ovis nes.
                            Ösade kotlettfrilla i fil. Paranade hiliga megalubel.
                        </div>

                        <div :class="$style.buttons">

                            <UiButton size="large">
                                Start now
                            </UiButton>

                            <UiButton color="yellow" size="large">
                                Explore Classes
                            </UiButton>

                        </div>

                    </aside>

                    <div :class="$style.banner">
                        <div :style="plateStyleList('top')" :class="[$style.plate, $style['--is-top']]">
                            <img src="/images/img_2.png" :class="$style.icon"/>

                            <div :class="$style.plateText">
                                Boost Methods
                                <span>Lörem ipsum melig</span>
                            </div>

                        </div>

                        <img src="/images/img.png" :class="$style.woman">

                        <div :style="plateStyleList('bottom')"  :class="[$style.plate, $style['--is-bottom']]">
                            <img src="/images/img_1.png" :class="$style.icon"/>

                            <div :class="$style.plateText">
                                Native learn
                                <span>Lörem ipsum melig</span>
                            </div>
                        </div>

                    </div>

                </section>
            </div>
        </main>
    </div>
</template>

<style lang="scss" module>
@import "normalize.css";

@font-face {
    font-family: 'Proxima Nova Bl';
    src: url('/fonts/proxima/ProximaNova-Black.woff2') format('woff2'),
    url('/fonts/proxima/ProximaNova-Black.woff') format('woff');
    font-weight: 900;
    font-style: normal;
    font-display: swap;
}

@font-face {
    font-family: 'Proxima Nova Rg';
    src: url('/fonts/proxima/ProximaNova-Bold.woff2') format('woff2'),
    url('/fonts/proxima/ProximaNova-Bold.woff') format('woff');
    font-weight: bold;
    font-style: normal;
    font-display: swap;
}

@font-face {
    font-family: 'Proxima Nova Rg';
    src: url('/fonts/proxima/ProximaNova-BoldIt.woff2') format('woff2'),
    url('/fonts/proxima/ProximaNova-BoldIt.woff') format('woff');
    font-weight: bold;
    font-style: italic;
    font-display: swap;
}

@font-face {
    font-family: 'Proxima Nova Bl';
    src: url('/fonts/proxima/ProximaNova-BlackIt.woff2') format('woff2'),
    url('/fonts/proxima/ProximaNova-BlackIt.woff') format('woff');
    font-weight: 900;
    font-style: italic;
    font-display: swap;
}

@font-face {
    font-family: 'Proxima Nova Lt';
    src: url('/fonts/proxima/ProximaNova-Light.woff2') format('woff2'),
    url('/fonts/proxima/ProximaNova-Light.woff') format('woff');
    font-weight: 300;
    font-style: normal;
    font-display: swap;
}

@font-face {
    font-family: 'Proxima Nova Bl';
    src: url('/fonts/proxima/ProximaNova-Black.woff2') format('woff2'),
    url('/fonts/proxima/ProximaNova-Black.woff') format('woff');
    font-weight: 900;
    font-style: normal;
    font-display: swap;
}

@font-face {
    font-family: 'Proxima Nova Rg';
    src: url('/fonts/proxima/ProximaNova-Regular.woff2') format('woff2'),
    url('/fonts/proxima/ProximaNova-Regular.woff') format('woff');
    font-weight: normal;
    font-style: normal;
    font-display: swap;
}

@font-face {
    font-family: 'Proxima Nova';
    src: url('/fonts/proxima/ProximaNova-ExtraBold.woff2') format('woff2'),
    url('/fonts/proxima/ProximaNova-ExtraBold.woff') format('woff');
    font-weight: bold;
    font-style: normal;
    font-display: swap;
}

:root {
    --header-height: 80px;
    --blue: #3A5173;
    --red: #F53161;
    --yellow: #F5D03C;
    --white: #FDFEFF;
    --black: #000000;
}

.App {
    width: 100%;
    min-height: 100vh;
    height: 100%;
    display: flex;
    flex-direction: column;
    color: var(--white);
    background-color: var(--blue);
}

.container {
    width: 1280px;
    margin: 0 auto;
}

.header {
    width: 100%;
    flex-shrink: 0;
    background-color: var(--blue);
    box-shadow: 0 5px 19px rgba(0, 0, 0, .25);

    .container {
        display: flex;
        align-items: center;
        column-gap: 32px;
        height: var(--header-height);
    }
}

.main {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
}

.logo {
    font-weight: bold;
    font-size: 30px;
    font-family: 'Proxima Nova Rg', sans-serif;
}

.list {
    display: flex;
    align-items: center;
    column-gap: 38px;
    margin: 0;
    padding: 0;

    li {
        list-style: none;
    }
}

.link {
    position: relative;
    font-family: 'Proxima Nova Rg', sans-serif;
    font-weight: normal;
    font-size: 20px;
    text-decoration: none;
    color: var(--white);
    transition: color .3s ease;

    &:after {
        content: '';
        position: absolute;
        bottom: 0;
        left: 0;
        width: 0;
        opacity: 0;
        height: 2px;
        background-color: var(--white);
        transition: all .3s ease;
    }

    &:hover {
        color: rgba(var(--white), .48);

        &:after {
            width: 100%;
            opacity: 1;
        }
    }

    &.--is-active {
        &:after {
            width: 100%;
            opacity: 1;
        }
    }
}

.actions {
    margin-left: auto;
    display: flex;
    align-items: center;
    column-gap: 24px;
}

.first {
    width: 100%;
    height: 100%;
    display: flex;
    padding: 40px 0;
}

.aside {
    width: 426px;
    display: flex;
    flex-direction: column;
}

.label {
    font-size: 16px;
    line-height: 160%;
    font-family: 'Proxima Nova Bl', sans-serif;
    color: var(--red);
}

.title {
    font-size: 64px;
    font-family: 'Proxima Nova Bl', sans-serif;
    line-height: 1;
    margin-top: 4px;
}

.text {
    font-family: 'Proxima Nova Rg', sans-serif;
    font-size: 16px;
    line-height: 24px;
    margin-top: 46px;
}

.buttons {
    margin-top: 86px;
    display: flex;
    align-items: center;
    column-gap: 16px;
}

.banner {
    width: 550px;
    height: 550px;
    position: relative;
    border-radius: 50%;
    margin-left: auto;
    margin-right: 32px;
}

.woman {
    width: 500px;
    object-fit: contain;
}

.plate {
    position: absolute;
    display: flex;
    align-items: center;
    padding: 24px 14px;
    column-gap: 8px;
    background-color: var(--white);
    border-radius: 10px;
    box-shadow: 0 10px 14px rgba(1, 17, 41, 0.15);
    color: var(--black);

    &.--is-top {
        top: 80px;
        left: -85px;
    }

    &.--is-bottom {
        right: -32px;
        bottom: 52px;
    }
}

.icon {
    width: 32px;
    height: 32px;
}

.plateText {
    display: flex;
    flex-direction: column;
    font-family: 'Proxima Nova Bl', sans-serif;
    font-size: 20px;
    line-height: 24px;

    span {
        letter-spacing: 0.045em;
        font-family: 'Proxima Nova Rg', sans-serif;
        font-size: 16px;
    }
}
</style>
