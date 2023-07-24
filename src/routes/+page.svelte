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

<div>
    {#await allCountries then data}
        <ul>
            {#each data as country}
                <li>
                    <div class="py-2">
						<p class="text-2xl">{country.name.common}</p>
						<p class="text-m">({country.name.official})</p>
					</div>
                </li>                
            {/each}
        </ul>
    {/await}
</div>
