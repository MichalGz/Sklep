<script>
	import Arrow from "./arrow.svelte";
    import EnglandFlag from "./england-flag.svelte";
	import GermanyFlag from "./germany-flag.svelte";
    import PolandFlag from "./poland-flag.svelte";
    const countries = ["Polski",'English','Deuchland'];
    let selectedCountry = countries.at(0);
    let isOpen = false;
    const flags = [PolandFlag, EnglandFlag, GermanyFlag]
    let selectedFlags = flags.at(1);

    function toggleOpen() {
        isOpen = !isOpen
    }
    /**
	 * @param {string | undefined} country
	 */
    function selectCountry(country) {
        selectedCountry = country;
    }

    /**
	 * @param {any} _flag
	 */
    function selectFlag(_flag) {
        selectedFlags = _flag;
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
            <div class ="flags">
                {#if country === "Polski"}
                <PolandFlag />
                {:else if country === "English"}
                <EnglandFlag />
                {:else if country === "Deuchland"}
                <GermanyFlag />
                {/if}
            </div>
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
        border: none;
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

    .country {
        border: none;
        padding: 8px;
    }

    .country:hover {
        background-color:rgb(150, 149, 149);
    }

    .flags {
        padding: 4px;
    }
</style>
