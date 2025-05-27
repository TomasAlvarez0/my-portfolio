<script>
    export let step;
</script>

<div class="flex flex-col gap-4 p-6 rounded-lg border border-solid border-slate-700 text-center group cursor-pointer hover:border-violet-700 duration-200">
    <div class="bg-slate-950 text-white rounded-full mx-auto grid place-items-center w-12 h-12 text-2xl group-hover:bg-violet-700 duration-200">
        <i class={step.icon}></i>
    </div>
    <h4 class="text-xl md:text-2xl">{step.name}</h4>
    <div class="text-base sm:text-lg opacity-70 group-hover:opacity-100 duration-200">
        <slot />
    </div>
</div>
