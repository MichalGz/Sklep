<script>
	import Arrow from "./arrow.svelte";
    import EnglandFlag from "./england-flag.svelte";
	import GermanyFlag from "./germany-flag.svelte";
    import PolandFlag from "./poland-flag.svelte";

    const countries = [
        {
            name: "Polski",
            flag: PolandFlag
        },
        {
            name: "English",
            flag: EnglandFlag
        },
        {
            name: "Deuchland",
            flag: GermanyFlag
        }
    ]

    let isOpen = false;
    let selectedCountry = countries.at(0);

    function toggleOpen() {
        isOpen = !isOpen
    }

    /**
	 * @param {any | undefined} country
	 */
    function selectCountry(country) {
        selectedCountry = country;
    }
</script>

<div class="countrySelector">
    <button class="selectedCountry" on:click={toggleOpen}>
        {#if selectedCountry}
            <svelte:component this={selectedCountry.flag} />
        {:else}
            Nie wspierany jezyk
        {/if}
        <div class:isOpen class="arrow"><Arrow /></div>
    </button>

    {#if isOpen}
        <div class="modal">
            <p class="language">Wybierz język: </p>
            {#each countries as country}
                <button class="country" on:click={()=>selectCountry(country)}> 
                    {country.name}
                    <div class ="flags">
                        <svelte:component this={country.flag} />
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
        display: flex;
        align-items: center;
        justify-content: space-between;
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
        background-color: rgb(150, 149, 149);
    }

    .flags {
        padding: 4px;
    }

    .isOpen {
        transform: rotate(180deg);
    }

    .arrow {
        margin-top: 4px;
        transition: 420ms;
    }
</style>
