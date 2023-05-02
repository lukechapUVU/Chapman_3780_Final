<script>
    import { onMount } from 'svelte'
    import { goto } from '$app/navigation'

    const NUM_IMAGES = 10
  
    let dogArr = []
    let dataDogArr = []
    let breedList = []
    let isLoading = true
  
    onMount(async () => {
      const imgResponse = await fetch(`https://dog.ceo/api/breeds/image/random/${NUM_IMAGES}`)
      const imgData = await imgResponse.json()

      for(let i = 0; i < imgData.message.length; i++) {
        const urlParts = imgData.message[i].split('/')
        const breed = urlParts[urlParts.length - 2]
        const breedSplit = breed.split('-')
        const breedFilterValue =  breedSplit[0]
        imgData.message[i] = imgData.message[i] + '~~' + breedFilterValue
      }

      const breedResponse = await fetch(`https://dog.ceo/api/breeds/list/all`)
      const breedData = await breedResponse.json()
      breedList = Object.keys(breedData.message)
      
  
      const nameResponse = await fetch('https://api.api-ninjas.com/v1/babynames', {
        method: 'GET',
        headers: { 'X-Api-Key': 'GPs3c3WNBdtYLIQ79vDV2Q==F9CnGTANOcWp5lj5' },
      })
      const nameData = await nameResponse.json()
  
      for (let i = 0; i < NUM_IMAGES; i++) {
        const dog = { id: i, image: imgData.message[i].split('~~')[0], name: nameData[i], breed: imgData.message[i].split('~~')[1] }
        dataDogArr.push(dog)
      }
      dogArr = [...dataDogArr]
      isLoading = false
    })

    const filterAttributes = () => {
        dogArr = [...dataDogArr]
        for (let i = 0; i < breedList.length; i++) {
            const breedStatus = document.querySelector(`#${breedList[i]}Status`);
            if(!breedStatus.checked) {
                dogArr = dogArr.filter((dog) => dog.breed != breedList[i])
            }
        }
    }
  </script>
  
  <div class="container">
    {#if isLoading}
        <p>Loading...</p>
    {:else if dogArr.length > 0}
        <div class="grid grid-cols-4 gap-12">
            {#each dogArr as dog}
                <div on:click={goto(`dogs/${dog.id}?name=${dog.name}&breed=${dog.image.split('/')[4]}&url=${dog.image.split('/')[5]}`)} class="card cursor-pointer w-96 bg-base-100 shadow-xl image-full rounded-lg border">
                    <div class="card-body items-center text-center">
                        <h2 class="card-title">{dog.name} ({dog.breed})</h2>
                        <img src={dog.image} alt="Picture of a dog">
                    </div>
                </div>
            {/each}
        </div>
    {:else}
        <p>Failed to fetch data</p>
    {/if}

    <div class="fixed-content text-accent border border-neutral-400 shadow-2xl bg-gray-600 rounded-xl p-10 mt-4 mr-2 ">
        <div class="flex">
            <h1 class="text-3xl">Filter by breed</h1>
            <!-- <button class="btn btn-primary btn-sm ml-auto" 
                class:btn-disabled="{characters.length === dataCharacters.length}" 
                on:click={resetFilter}>
                Reset
            </button> -->
        </div>
        {#each breedList as breed}
        <div>
            <label class="cursor-pointer">
                <input id="{breed}Status" type="checkbox" checked="checked" on:click={filterAttributes} class="checkbox checkbox-xs checkbox-primary" />
                <span class="label-text"> {breed}</span>
            </label>
        </div>
        {/each}
        
    </div>
  </div>
  
  <style>
    img {
        width: 20vw; 
        height: 20vw;
        object-fit: cover;
    }

    .container {
        margin-left: 20px;
        margin-right: 20px;
    }
    
    .fixed-content {
        position: fixed;
        top: 0;
        right: 0;
        height: 100%;
        overflow: auto;
    }
  
  </style>
  