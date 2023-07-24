<script lang="ts">
    interface Country{
        name: {
            common: string,
            official: string
        },
        flags: {
            png: string
        }
    }

    let allCountries : Promise<Country[]> = fetch('https://restcountries.com/v3.1/all').then( (result) => result.json());
</script>

<div class="flex items-center bg-white rounded-xl shadow-lg max-w-3xl">
    {#await allCountries then data}
        <ul class="list-inside">
            {#each data as country}
                <li class="font-medium py-6 text-center content-center">
                    <div class="py-2">
						<p class="text-2xl">{country.name.common}</p>
						<p class="text-m">({country.name.official})</p>
					</div>
                    <div class="py-2">
						<img class="px-56" src={country.flags.png} alt=""/>
					</div>
                </li>                
            {/each}
        </ul>
    {/await}
</div>
