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

<div class="flex items-center bg-white rounded-xl shadow-lg max-w-3xl p-6 mx-auto space-x-4 my-7">
    {#await allCountries then data}
        <ul class="list-inside">
            {#each data as country}
                <li class="py-6 text-center content-center">
                    <div class="py-2">
						<p class="font-medium text-2xl">{country.name.common}</p>
						<p class="text-m text-gray-600">({country.name.official})</p>
					</div>
                    <div class="py-2">
						<img class="px-56" src={country.flags.png} alt=""/>
					</div>
                </li>                
            {/each}
        </ul>
    {/await}
</div>
