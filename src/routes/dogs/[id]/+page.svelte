<script>
    import { onMount } from 'svelte';
    import { page } from '$app/stores';
    

    let propList = ''
    let name = '' 
    let breed = ''
    let imgUrl = 'https://images.dog.ceo/breeds/'

    const fakeAddresses = [
        {
            fullAddress: '738 Boardman Rd SW, South Boardman, MI 49680',
            street: '738 Boardman Rd SW', 
            city: 'South Boardman',
            state: 'MI',
            zip: '49680',
            iframe: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2838.8775306866323!2d-85.19810982337557!3d44.6404199880237!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x881feb8317fc3dc7%3A0x867ca9d5d8f8be59!2s738%20Boardman%20Rd%20SW%2C%20South%20Boardman%2C%20MI%2049680!5e0!3m2!1sen!2sus!4v1683052482194!5m2!1sen!2sus'
        },
        {
            fullAddress: '2013 11th St, Port Neches, TX 77651',
            street: '2013 11th', 
            city: 'St Port Neches',
            state: 'TX',
            zip: '77651',
            iframe: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3455.802208269856!2d-93.96707872388194!3d29.98511382137838!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x863eb16b23957659%3A0x815d19540bc525f4!2s2013%2011th%20St%2C%20Port%20Neches%2C%20TX%2077651!5e0!3m2!1sen!2sus!4v1683052457822!5m2!1sen!2sus'
        },
        {
            fullAddress: '3934 Vistula Dr, Chipley, FL 32428',
            street: '3934 Vistula Dr', 
            city: 'Chipley',
            state: 'FL',
            zip: '32428',
            iframe: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3436.1732412015945!2d-85.62459182386625!3d30.544409094708865!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8893a0b571923793%3A0xdc01e1e175646234!2s3934%20Vistula%20Dr%2C%20Chipley%2C%20FL%2032428!5e0!3m2!1sen!2sus!4v1683052425245!5m2!1sen!2sus'
        },
        {
            fullAddress: '323 Julius St #B, Lead, SD 57754',
            street: '323 Julius St #B', 
            city: 'Lead',
            state: 'SD',
            zip: '57754',
            iframe: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2852.9910857938976!2d-103.76982932338743!3d44.3512343070049!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x5332a5aab9dcb7d3%3A0xa57e8452990c1f66!2s323%20Julius%20St%20b%2C%20Lead%2C%20SD%2057754!5e0!3m2!1sen!2sus!4v1683052404209!5m2!1sen!2sus'
        },
        {
            fullAddress: '131 Calton Dr, Sunset, SC 29685',
            street: '131 Calton Dr', 
            city: 'Sunset',
            state: 'SC',
            zip: '29685', 
            iframe: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3271.6145443563532!2d-82.81393012373364!3d34.91612147162307!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x885853fd3c2b87d9%3A0x8323371d457e8e03!2s131%20Calton%20Dr%2C%20Sunset%2C%20SC%2029685!5e0!3m2!1sen!2sus!4v1683052384186!5m2!1sen!2sus'
        },
        {
            fullAddress: '2013 11th St, Port Neches, TX 77651',
            street: '2013 11th', 
            city: 'St Port Neches',
            state: 'TX',
            zip: '77651',
            iframe: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3455.802208269856!2d-93.96707872388194!3d29.98511382137838!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x863eb16b23957659%3A0x815d19540bc525f4!2s2013%2011th%20St%2C%20Port%20Neches%2C%20TX%2077651!5e0!3m2!1sen!2sus!4v1683052343333!5m2!1sen!2sus'
        },
        {
            fullAddress: '7133 Askew Ave, Kansas City, MO 64132',
            street: '7133 Askew Ave', 
            city: 'Kansas City',
            state: 'MO',
            zip: '64132',
            iframe: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3100.8395056767754!2d-94.54771242359362!3d38.99615914087001!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x87c0e5e91c9ff7d1%3A0x14c76f703324fffe!2s7133%20Askew%20Ave%2C%20Kansas%20City%2C%20MO%2064132!5e0!3m2!1sen!2sus!4v1683052313223!5m2!1sen!2sus'
        },
        {
            fullAddress: '22522 NW 176th Ave, High Springs, FL 32643',
            street: '22522 NW 176th Ave', 
            city: 'High Springs',
            state: 'FL',
            zip: '32643',
            iframe: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3461.639152826606!2d-82.58609072388654!3d29.816967629311694!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x88e8c9b5f61ca6f9%3A0xe66f36d3cc60b982!2s22522%20NW%20176th%20Ave%2C%20High%20Springs%2C%20FL%2032643!5e0!3m2!1sen!2sus!4v1683052274135!5m2!1sen!2sus'
        },
        {
            fullAddress: '442 County Rd 2234, Goshen, AL 36035',
            street: '442 County Rd 2234', 
            city: 'Goshen',
            state: 'AL',
            zip: '36035',
            iframe: '<https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3394.738571638978!2d-86.02928942383313!3d31.69571403845701!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x888df17102429643%3A0xecdcd1c853cddfec!2s442%20County%20Rd%202234%2C%20Goshen%2C%20AL%2036035!5e0!3m2!1sen!2sus!4v1683052038675!5m2!1sen!2sus'
        },
        {
            fullAddress: '1690 Bruner Mill Rd, Ashford, AL 36312',
            street: '1690 Bruner Mill Rd', 
            city: 'Ashford',
            state: 'AL',
            zip: '36312',
            iframe: 'https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3413.0550312694663!2d-85.20723862384781!3d31.19148746331618!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x8892bf46b26d6617%3A0xc63b926bd24bbc04!2s1690%20Bruner%20Mill%20Rd%2C%20Ashford%2C%20AL%2036312!5e0!3m2!1sen!2sus!4v1683051963650!5m2!1sen!2sus'
        },
        
    ]
    const careInstructions = [
        "Feed my dog twice a day, one cup of kibble per meal. She's allergic to grains, so make sure the food is grain-free. She likes to eat in her crate. Give her a dental chew after each meal.",
        "Take my dog for a 30-minute walk twice a day, once in the morning and once in the evening. She's afraid of other dogs, so avoid areas where there are likely to be a lot of other dogs. Bring water and a collapsible bowl on the walk.",
        "My dog needs to take medication twice a day. Give her one pill with food in the morning and one with food in the evening. She's allowed to have a small amount of cheese with the pill if she won't take it on its own.",
        "Brush my dog's coat once a day with a slicker brush. She likes to be brushed while she's lying down. She hates baths, so don't bathe her unless it's absolutely necessary.",
        "Take my dog outside every four hours for a potty break. She's trained to use the backyard, but if you take her for a walk, make sure to clean up after her. Give her a treat and praise her when she goes potty outside.",
        "My dog is crate trained. She can be in the crate for up to four hours at a time during the day, and up to eight hours at night. She likes to have a blanket and a stuffed animal in the crate with her.",
        "My dog is scared of thunderstorms. If there's a storm while you're here, turn on the TV or the radio to drown out the noise. She also likes to have a weighted blanket on her during storms.",
        "If my dog gets anxious or stressed, give her a few drops of CBD oil. She's trained to use a puzzle toy to occupy herself when she's stressed. You can fill it with peanut butter or cheese.",
        "My dog is an escape artist. Make sure all doors and gates are securely closed and locked. She can't be off-leash outside of a fenced area. Keep a close eye on her during walks.",
        "My dog loves to play fetch. She has a favorite ball that she likes to chase. You can play fetch with her in the backyard or at the park. Be careful not to throw the ball too hard or too far."
    ]
    
    const selectedAddress = fakeAddresses[$page.params.id]
    const selectedCareInstruction = careInstructions[$page.params.id]

    onMount(() => {
        propList = $page.url.search
        propList = propList.split('&')
        for(let i = 0; i < propList.length; i++) {
            if(propList[i].includes('?')) {
                propList[i] = propList[i].slice(1)
            }
            propList[i] = propList[i].split('=')[1]
        }
        name = propList[0]
        breed = propList[1]
        if(breed.includes('-')) {
            breed = breed.split('-')[1] + ' ' + breed.split('-')[0]
        }
        imgUrl += propList[1] + '/' + propList[2]
    })

    
</script>
  
<div class="mx-5">
    <h1 class="text-3xl">
        {name}
        <span class="text-xl">{breed}</span>
    </h1>
        <p>{selectedCareInstruction}</p>
        <img src={imgUrl} alt="A picture of {name}"/>
        <div class="my-4">
            <p>{selectedAddress.fullAddress}</p>
            <iframe src={selectedAddress.iframe} width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
        </div>
</div>
