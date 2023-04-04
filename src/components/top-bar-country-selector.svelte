<script>
	import Arrow from "./arrow.svelte";
    import EnglandFlag from "./england-flag.svelte";
	import GermanyFlag from "./germany-flag.svelte";
    import PolandFlag from "./poland-flag.svelte";

    const countries = ["Polski",'English','Deuchland'];
    let selectedCountry = countries.at(0);
    let isOpen = false;

    function toggleOpen() {
        isOpen = !isOpen
    }
    /**
	 * @param {string | undefined} country
	 */
    function selectCountry(country) {
        selectedCountry = country;
    }
</script>

<div class="countrySelector">
    <button class="selectedCountry" on:click={toggleOpen}>
        {#if selectedCountry === "Polski"}
        <PolandFlag />
        {:else if selectedCountry === "English"}
        <EnglandFlag />
        {:else if selectedCountry === "Deuchland"}
        <GermanyFlag />
        {:else}
        Nie wspierany jezyk
        {/if}
        <Arrow />
    </button>
    {#if isOpen}
    <div class="modal">
        <p class="language">Wybierz język: </p> 
        {#each countries as country}
        <button class="country" on:click={()=>selectCountry(country)}> 
            {country}
        </button>
        {/each}
    </div>
    {/if}
</div>


<style>
    .countrySelector {
        position: relative;
    }
    
    .modal {
        position: absolute;
        display: flex;
        flex-direction: column;
        top: 50px;
        right: 0;
        padding: 8px;
        background-color: #fff;
        -webkit-box-shadow: 21px 1px 21px 1px rgba(66, 68, 90, 1);
        -moz-box-shadow: 21px 1px 21px 1px rgba(66, 68, 90, 1);
        box-shadow: 21px 1px 21px 1px rgba(66, 68, 90, 1);
    }
    
    .selectedCountry {
        color: #fff;
        background: inherit;
        border: none;
        height: 100%;
        aspect-ratio: 1 / 1;
    }
    
    .language {
        font-size: 16px;
        padding: 8px;
    }

</style>