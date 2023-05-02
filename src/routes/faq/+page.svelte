<script>
    const faqData = [
        {
            question: "What should I do if a dog I'm sitting becomes ill or injured?",
            answer: "Contact the dog's owner immediately and follow their instructions. If necessary, seek veterinary care.",
        },
        {
            question: "How should I introduce myself to a new dog I'm sitting?",
            answer: "Approach the dog slowly and calmly, let the dog come to you, and avoid making direct eye contact.",
        },
        {
            question: "What should I do if a dog I'm sitting gets loose or runs away?",
            answer: "Immediately notify the dog's owner and begin searching the area. If the dog is microchipped, notify local shelters and animal control.",
        },
        {
            question: "How often should I feed a dog I'm sitting?",
            answer: "Follow the feeding schedule and instructions provided by the dog's owner.",
        },
        {
            question: "What if a dog I'm sitting has separation anxiety?",
            answer: "Work with the dog's owner to develop a plan to alleviate separation anxiety, such as leaving the dog with a familiar item or having someone check on the dog regularly.",
        },
        {
            question: "How often should I take a dog I'm sitting for walks?",
            answer: "Follow the dog's usual walking schedule and instructions provided by the owner.",
        },
        {
            question: "What should I do if a dog I'm sitting is aggressive towards other dogs?",
            answer: "Avoid contact with other dogs and follow the dog's usual routine.",
        },
        {
            question: "What should I do if a dog I'm sitting is aggressive towards people?",
            answer: "Avoid contact with people and follow the dog's usual routine.",
        },
        {
            question: "How should I handle a dog I'm sitting that is afraid of thunderstorms or fireworks?",
            answer: "Follow the dog's usual routine and try to create a calm environment, such as closing windows and playing music or white noise.",
        },
        {
            question: "What should I do if a dog I'm sitting has a history of biting?",
            answer: "Consult with the dog's owner about their biting history and follow any safety precautions they recommend.",
        },
        {
            question: "How should I handle a dog I'm sitting that is afraid of going to the vet?",
            answer: "Follow the dog's usual routine and try to make the vet visit as calm and stress-free as possible.",
        },
        {
            question: "What should I do if a dog I'm sitting is showing signs of illness or injury but the owner cannot be reached?",
            answer: "Seek veterinary care for the dog and notify the owner as soon as possible.",
        },
        {
            question: "Should I administer any medication or supplements to a dog I'm sitting?",
            answer: "Only administer medication or supplements that the owner has provided and follow their instructions.",
        },
        {
            question: "What if a dog I'm sitting has never been left alone before?",
            answer: "Work with the dog's owner to develop a plan to acclimate the dog to being alone and gradually increase the amount of time the dog is left alone.",
        },
        {
            question: "What should I do if a dog I'm sitting has a history of escaping from the yard?",
            answer: "Keep a close eye on the dog and ensure that all gates and fences are secure.",
        },
        {
            question: "Should I groom a dog I'm sitting?",
            answer: "Only groom the dog if the owner has provided specific instructions and grooming tools.",
        },
        {
            question: "What if a dog I'm sitting is not house-trained?",
            answer: "Follow the dog's usual routine and work with the owner to develop a plan to improve the dog's house-training.",
        },
        {
            question: "What if a dog I'm sitting has a history of destroying things?",
            answer: "Keep valuables out of the dog's reach and follow any precautions or instructions provided by the owner.",
        }
    ]
</script>

<div class="container grid grid-cols-2 gap-12">
    {#each faqData as faq}
        <div tabindex="0" class="collapse collapse-arrow border border-base-300 bg-base-100 rounded-box">
            <div class="collapse-title text-xl font-medium">
                Q. {faq.question}
            </div>
            <div class="collapse-content">
                <p>A. {faq.answer}</p>
            </div>
        </div>
    {/each}
</div>


<style>
    .container {
        margin-left: 20px;
        margin-right: 20px;
    }
</style>