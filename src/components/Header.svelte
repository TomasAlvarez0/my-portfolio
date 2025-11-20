<script>
    import { base } from '$app/paths';
    import { onMount } from 'svelte';
    import { fly, fade } from 'svelte/transition';
    
    export let y;

    export let tabs = [
        { name: "Projects ", link: "#projects" },
        { name: "About me", link: "#about" },
    ];
    
    let menuOpen = false;
    
    function toggleMenu() {
        menuOpen = !menuOpen;
        // Prevenir scroll del body cuando el menú está abierto
        if (menuOpen) {
            document.body.style.overflow = 'hidden';
        } else {
            document.body.style.overflow = '';
        }
    }
    
    function closeMenu() {
        menuOpen = false;
        document.body.style.overflow = '';
    }
    
    // Cerrar menú al hacer clic en un enlace
    function handleLinkClick() {
        closeMenu();
    }
    
    // Cerrar menú al cambiar el tamaño de la ventana
    onMount(() => {
        const handleResize = () => {
            if (window.innerWidth >= 640 && menuOpen) {
                closeMenu();
            }
        };
        window.addEventListener('resize', handleResize);
        return () => window.removeEventListener('resize', handleResize);
    });
</script>

<header
    class={"sticky z-[10] top-0 duration-200 px-6 flex items-center justify-between border-b border-solid " +
        (y > 0
            ? " py-4 bg-slate-950 border-violet-950"
            : " py-6 bg-transparent border-transparent")}
>
    <a href="#introPage" class="font-medium hover:opacity-80 transition-opacity">
        <b class="font-bold poppins">Tomas</b> <span class="">Alvarez</span>
    </a>
    
    <!-- Desktop Navigation -->
    <nav class="sm:flex items-center gap-4 hidden">
        {#each tabs as tab, index}
            <a
                href={tab.link}
                class="duration-200 hover:text-violet-400 transition-colors"
                aria-label={`Navigate to ${tab.name}`}
            >
                <p>{tab.name}</p>
            </a>
        {/each}
        <a
            href="{base}/AlvarezMartinTomas_IngSistemas.pdf"
            target="_blank"
            rel="noopener noreferrer"
            class="blueShadow relative overflow-hidden px-5 py-2 group rounded-full bg-violet-600 text-white"
            aria-label="Download Resume PDF"
        >
            <div class="absolute top-0 right-full w-full h-full bg-violet-400 opacity-20 group-hover:translate-x-full z-0 duration-200"></div>
            <h4 class="relative z-9">Resume</h4>
        </a>
        <a
            href="https://wa.link/vqi4tk"
            target="_blank"
            rel="noopener noreferrer"
            class="blueShadow relative overflow-hidden px-5 py-2 group rounded-full bg-white text-slate-950"
            aria-label="Contact me via WhatsApp"
        >
            <div class="absolute top-0 right-full w-full h-full bg-violet-400 opacity-40 group-hover:translate-x-full z-0 duration-200"></div>
            <h4 class="relative z-9">Contact me</h4>
        </a>
    </nav>
    
    <!-- Mobile Menu Button -->
    <button
        class="sm:hidden p-2 text-white hover:text-violet-400 transition-colors duration-200 focus:outline-none focus:ring-2 focus:ring-violet-400 rounded"
        aria-label="Toggle menu"
        aria-expanded={menuOpen}
        on:click={toggleMenu}
    >
        {#if menuOpen}
            <i class="fa-solid fa-xmark text-2xl"></i>
        {:else}
            <i class="fa-solid fa-bars text-2xl"></i>
        {/if}
    </button>
    
    <!-- Mobile Menu Overlay -->
    {#if menuOpen}
        <div
            class="fixed inset-0 bg-slate-950/95 backdrop-blur-sm z-[20] sm:hidden"
            role="dialog"
            aria-modal="true"
            aria-label="Mobile navigation menu"
            transition:fade={{ duration: 200 }}
        >
            <nav class="flex flex-col items-center justify-center h-full gap-8 px-6">
                {#each tabs as tab}
                    <a
                        href={tab.link}
                        class="text-2xl font-medium text-white hover:text-violet-400 transition-colors duration-200"
                        on:click={handleLinkClick}
                    >
                        {tab.name}
                    </a>
                {/each}
                <a
                    href="{base}/AlvarezMartinTomas_IngSistemas.pdf"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="px-6 py-3 rounded-full bg-violet-600 text-white font-medium hover:bg-violet-700 transition-colors duration-200"
                    on:click={handleLinkClick}
                >
                    Resume
                </a>
                <a
                    href="https://wa.link/vqi4tk"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="px-6 py-3 rounded-full bg-white text-slate-950 font-medium hover:bg-slate-100 transition-colors duration-200"
                    on:click={handleLinkClick}
                >
                    Contact me
                </a>
            </nav>
        </div>
    {/if}
</header>