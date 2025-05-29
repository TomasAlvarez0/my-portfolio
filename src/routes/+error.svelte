<script>
    import { page } from '$app/stores';
    import { base } from '$app/paths';
</script>

<div class="min-h-screen flex flex-col justify-center items-center text-center p-4">
    <h1 class="text-6xl font-bold text-violet-400 mb-4">404</h1>
    <h2 class="text-2xl font-semibold mb-4">Página no encontrada</h2>
    <p class="text-lg text-gray-300 mb-8">Lo siento, la página que buscas no existe.</p>
    
    <a 
        href="{base}/"
        class="blueShadow relative overflow-hidden px-6 py-3 group rounded-full bg-violet-600 text-white hover:bg-violet-700 transition-colors duration-200"
    >
        <div class="absolute top-0 right-full w-full h-full bg-violet-400 opacity-20 group-hover:translate-x-full z-0 duration-200"></div>
        <span class="relative z-9">Volver al inicio</span>
    </a>
</div> 