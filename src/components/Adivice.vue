<template>
    <section>
        <div class="bg-Dark-Grayish-Blue rounded-lg p-5 m-5 flex flex-col justify-center items-center">
            <h2 class="text-center text-Neon-Green font-semibold text-[14px] tracking-[.2rem] uppercase mb-8">advice #{{ id }}</h2>
            <h1 class="text-center font-extrabold text-[24px] lg:w-[18vw]">"{{ conselho }}"</h1>
            <img src="/src/assets/images/pattern-divider-mobile.svg" alt="" class="mt-8">
            <button @click="gerarConselho" class="flex justify-center items-center relative translate-y-[90%] m-0 bg-Neon-Green rounded-full p-4 hover:shadow-[0px_0px_20px_1px] hover:shadow-Neon-Green ">
                <svg width="24" height="24" xmlns="http://www.w3.org/2000/svg"><path d="M20 0H4a4.005 4.005 0 0 0-4 4v16a4.005 4.005 0 0 0 4 4h16a4.005 4.005 0 0 0 4-4V4a4.005 4.005 0 0 0-4-4ZM7.5 18a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm4.5 4.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Zm0-9a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3Z" fill="#202733"/></svg>
            </button>
        </div>
    </section>
    
</template>

<script>
    export default {
        data(){
            return{
                id: null,
                conselho: null
            }
        },
        methods:{
            async gerarConselho(){
                const response = await fetch('https://api.adviceslip.com/advice')
                const conselho = await response.json()
                this.id = conselho.slip.id
                this.conselho = conselho.slip.advice
                
            }

        },
        mounted(){
            this.gerarConselho()
        }
    }
</script>

