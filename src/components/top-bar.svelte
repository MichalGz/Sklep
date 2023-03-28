<script>
	import TopBarInfo from "./top-bar-info.svelte";
</script>

<div class="topbar">
    <div class="left">
        <TopBarInfo />
    </div>
    <div class="right">
        inne
    </div>
</div>

<style>
    .topbar {
        background-color: black;
        padding: 16px;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

    .left, .right {
        color: beige;
    }
</style>
