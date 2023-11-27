<template>
    <header class="header">
        <LogoIcon :class="{cursor_pointer: isIconActive}" @click="toLanding"/>
        <div class="header__actions">
            <Button :type="BUTTON_TYPE.TETRARY" label="Войти" @on-click="toLogin" />
            <Button :type="BUTTON_TYPE.SECONDARY" label="Регистрация" @on-click="toSignup" />
        </div>
    </header>
</template>

<script setup>
    import { Button } from '@/components/UI';
    import { LogoIcon } from '@/components/Icons';
    import BUTTON_TYPE from '@/constants/buttonTypes';
    import ROUTES_NAMES from "@/constants/routesNames";
    import { useRouter, useRoute } from 'vue-router';
    import { computed } from 'vue';

    const router = useRouter();
    const route = useRoute();
    
    function toLogin() {
        router.push({ name: ROUTES_NAMES.LOGIN });
    }
    function toSignup() {
        router.push({ name: ROUTES_NAMES.SIGN_UP });
    }
    function toLanding() {
        if (isIconActive.value) { window.open("https://soloteam.io")}
    }
    const isIconActive = computed(() => {
        return route.name === ROUTES_NAMES.FREELANCER_PROFILE_PUBLIC
    })
</script>

<style lang="scss" scoped>
    .header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        width: 100%;
        padding: 16px 24px 0px;
        min-height: 36px;

        &__actions {
            display: flex;
            gap: 12px;
        }
    }
</style>