<script>
	import TopBarCountrySelector from "./top-bar-country-selector.svelte";
    import TopBarInfo from "./top-bar-info.svelte";
	import TopBarNavigation from "./top-bar-navigation.svelte";
	import TopBarUserAction from "./top-bar-user-action.svelte";
</script>

<div class="topbar">
    <div class="left">
        <TopBarInfo />
    </div>
    <div class="right">
        <TopBarNavigation />
        <TopBarUserAction />
        <TopBarCountrySelector />
    </div>
</div>

<style>
    .topbar {
        background-color: black;
        padding: 0px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
    
    .right {
        display: flex;
    }
</style>
