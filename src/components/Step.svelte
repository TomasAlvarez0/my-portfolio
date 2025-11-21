<script>
    export let step;
    export let linkUrl = null; // Prop opcional para cualquier enlace
    export let linkText = "View Details"; // Texto del botón
    export let linkType = "website"; // Tipo: "website", "pdf", "github", etc.
    
    // Icono según el tipo de enlace
    function getLinkIcon(type) {
        switch(type) {
            case "pdf":
                return "fas fa-file-pdf";
            case "github":
                return "fab fa-github";
            case "website":
            default:
                return "fas fa-external-link-alt";
        }
    }
</script>

<div class="flex flex-col gap-4 p-6 rounded-lg border border-solid border-slate-700 text-center group cursor-pointer hover:border-violet-700 duration-200">
    <div class="bg-slate-950 text-white rounded-full mx-auto grid place-items-center w-12 h-12 text-2xl group-hover:bg-violet-700 duration-200">
        <i class={step.icon}></i>
    </div>
    <h4 class="text-xl md:text-2xl">{step.name}</h4>
    <div class="text-base sm:text-lg opacity-70 group-hover:opacity-100 duration-200">
        <slot />
    </div>
    
    <!-- Botón de enlace si está disponible -->
    {#if linkUrl}
        <div class="mt-4">
            <a 
                href={linkUrl} 
                target="_blank" 
                rel="noopener noreferrer"
                class="inline-flex items-center gap-2 px-4 py-2 bg-violet-600 hover:bg-violet-700 text-white text-sm font-medium rounded-lg transition-colors duration-200"
                on:click|stopPropagation
            >
                <i class={getLinkIcon(linkType)}></i>
                {linkText}
            </a>
        </div>
    {/if}
</div>
