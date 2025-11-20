<script>
    import { base } from '$app/paths';
    import Step from "./Step.svelte";

    let steps = [
        {
            name: "Conectando corazones",
            icon: "fa-solid fa-hands-helping",
            description:
                "A platform for connecting people in need with those who can help. Built as a final project with collaborative features to facilitate community support and assistance.",
        },
        {
            name: "Smart Marketing",
            icon: "fa-solid fa-list-check",
            description:
                "Using a dataset of past customers, we applied various classification and prediction tools to implement smart marketing strategies. The goal was to offer different products tailored to the characteristics of potential clients.",
        },
        {
            name: "Strategic Analysis of URG",
            icon: "fa-solid fa-diagram-project",
            description:
                "Augment your datasets with our filters and dataset manipulations to ensure your models are trained on the highest quality datasets (coming soon).",
        },
    ];

    let benefits = [
        {
            metric: "10x",
            name: "Systems Engineering Student",
            description:
                "Currently pursuing a degree in Systems Engineering (expected graduation: Dec. 2025) with a strong passion for technology and sports. I'm constantly learning new technologies, improving my programming skills, and seeking opportunities to apply my knowledge in real-world projects.",
        },
        {
            name: "Academic Excellence",
            description:
                "Maintaining a strong academic performance with a General Average of 8.12 (eight point twelve) as of February 19, 2025. This reflects my dedication to academic excellence and continuous improvement in my engineering studies.",
            pdfUrl: `${base}/ANALITICO 2025.pdf`,
            pdfButtonText: "View Academic Record"
        },
        {
            name: "Passionate About Technology and Sports",
            description:
                "I find the perfect balance between my love for technology and sports. Whether I'm coding a new application or playing my favorite sport, I bring the same dedication, teamwork, and strategic thinking to everything I do. This combination gives me a unique perspective on problem-solving and collaboration.",
        },
        {
            name: "Committed to Continuous Learning",
            description:
                "As a student, I'm always eager to learn and grow. I actively participate in academic projects, contribute to open-source initiatives, and stay updated with the latest technology trends. My goal is to make a meaningful impact in the tech industry while maintaining an active and healthy lifestyle.",
        },
    ];

    // Lógica para el contador de visitas con CountAPI
    import { onMount } from 'svelte';
    
    let visitCount = 0;
    let isLoading = true;
    
    // Animaciones de scroll reveal
    function observeElements() {
        if (typeof IntersectionObserver === 'undefined' || typeof document === 'undefined') return;
        
        const observer = new IntersectionObserver(
            (entries) => {
                entries.forEach((entry) => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('animate-fade-in');
                        observer.unobserve(entry.target);
                    }
                });
            },
            { threshold: 0.1, rootMargin: '0px 0px -50px 0px' }
        );
        
        // Observar elementos después de que el DOM esté listo
        setTimeout(() => {
            const elementsToObserve = document.querySelectorAll('.scroll-reveal');
            elementsToObserve.forEach((el) => observer.observe(el));
        }, 100);
    }
    
    onMount(async () => {
        try {
            // Delay para mostrar la animación de carga
            await new Promise(resolve => setTimeout(resolve, 1000));
            
            // Incrementar el contador (esto creará el namespace si no existe)
            // CountAPI automáticamente crea el namespace y la clave si no existen
            const res = await fetch('https://api.countapi.xyz/hit/tomi-portfolio/visits', {
                method: 'GET',
                headers: {
                    'Accept': 'application/json'
                },
                mode: 'cors',
                cache: 'no-store'
            });
            
            if (!res.ok) {
                throw new Error(`HTTP error! status: ${res.status}`);
            }
            
            const data = await res.json();
            
            // Verificar que la respuesta tenga el valor
            if (data.value !== undefined && typeof data.value === 'number') {
                isLoading = false;
                const targetCount = data.value;
                
                // Animación de conteo progresivo
                const duration = 2000; // 2 segundos
                const steps = 60;
                const increment = targetCount / steps;
                
                let currentCount = 0;
                const counter = setInterval(() => {
                    currentCount += increment;
                    if (currentCount >= targetCount) {
                        currentCount = targetCount;
                        clearInterval(counter);
                    }
                    visitCount = Math.floor(currentCount);
                }, duration / steps);
            } else {
                throw new Error('Invalid API response format');
            }
            
        } catch (e) {
            console.error('Error loading visit counter:', e);
            isLoading = false;
            visitCount = 0;
        }
    });
    
    // Inicializar observador de scroll
    onMount(() => {
        observeElements();
    });
</script>

<main class="flex flex-col flex-1 p-4 ">
    <!-- HERO-INTRO -->
    <section
        id="introPage"
        class="grid grid-cols-1 lg:grid-cols-2 gap-10 py-0 sm:py-14">
        <div 
            class="flex flex-col lg:justify-center text-center lg:text-left gap-6 md:gap-8 lg:gap-10"
        >
            <h2 class="font-semibold text-4xl sm:text-5xl md:text-6xl">
                Hi! I'm <span class="poppins text-violet-400">Tomas</span>Alvarez
                <br />systems 
                <span class="poppins text-violet-400">engineer</span>
            </h2>
            <p class="text-base sm:text-lg md:text-xl">
                Systems Engineering student passionate about <span class="text-violet-400">technology</span> and <span class="text-violet-400">sports</span>. Currently learning and exploring the world of programming, software development, and system analysis. Always eager to take on new challenges and grow professionally.
            </p>
            <a
                href="https://wa.link/vqi4tk"
                target="_blank"
                rel="noopener noreferrer"
                class="blueShadow mx-auto lg:mr-auto lg:ml-0 text-base sm:text-lg md:text-xl poppins relative overflow-hidden px-6 py-3 group rounded-full bg-white text-slate-950 transition-all duration-200 hover:scale-105 focus:outline-none focus:ring-2 focus:ring-violet-400"
                aria-label="Contact me via WhatsApp"
            >
                <div
                    class="absolute top-0 right-full w-full h-full bg-violet-400 opacity-20 group-hover:translate-x-full z-0 duration-200"
                ></div>
                <h4 class="relative z-9">Contact me &rarr;</h4>
            </a>
        </div>
        <div class="relative shadow-2xl grid place-items-center ">
            <img
                src={"images/profile.png"}
                alt="Tomás Álvarez - Systems Engineering Student"
                loading="lazy"
                class="object-cover z-[2] max-h-[70vh]"
                width="500"
                height="600"
            />
        </div>
        <!-- <div  class="flex p-0.5 relative max-w-[700px] w-full mx-auto">
            <div
                class="absolute inset-0 overflow-hidden rounded-md flex items-center justify-center"
            >
                <div
                    class="bg-gradient-to-r absolute inset-[-20px]  from-violet-800 to-indigo-800 specialSpin"
                />
            </div>

            <img
                src={"images/zetane-engine.jpeg"}
                alt="Zetane Engine"
                class="w-full h-full object-cover z-[2]"
            />
        </div> -->
    </section>
    <!-- PROJECTS -->
    <section class="py-20 lg:py-32 flex flex-col gap-24" id="projects">
        <div class="flex flex-col gap-2 text-center">
            <h6 class="text-large sm:text-xl md:text-2xl">
                A few of my creative endeavors.
            </h6>
            <h3 class="font-semibold text-3xl sm:text-4xl md:text-5xl">
                Curious to <span class="poppins text-violet-400">see</span> my work?
            </h3>
        </div>
        
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-12 lg:gap-10">
            <div class="scroll-reveal opacity-0 translate-y-8 transition-all duration-700 ease-out">
                <Step step={steps[0]} pdfUrl="https://conectando-corazones.vercel.app/" pdfButtonText="Visit Website">
                    <p>
                        {steps[0].description} Using:<strong
                            class="text-violet-400"> Svelte, TailwindCSS, SvelteKit, PostgreSQL </strong
                        >   Final project of the career, in a group with 2 collaborators</p>
                </Step>
            </div>
            <div class="scroll-reveal opacity-0 translate-y-8 transition-all duration-700 ease-out" style="transition-delay: 100ms">
                <Step step={steps[1]} pdfUrl="#" pdfButtonText="View Project Details">
                    <p>
                        Data Mining with <strong
                            class="text-violet-400">Python</strong
                        >,
                        <strong class="text-violet-400">RapidMiner & SPSS Statistics</strong
                        >
                        Using a dataset of past customers, we applied various classification and prediction tools to implement smart marketing strategies. The goal was to offer different products tailored to the characteristics of potential clients.
                    </p>
                </Step>
            </div>
            <div class="scroll-reveal opacity-0 translate-y-8 transition-all duration-700 ease-out" style="transition-delay: 200ms">
                <Step step={steps[2]} pdfUrl="{base}/TPI-Gerencial-2025.pdf" pdfButtonText="View Details (PDF)">
                    <p>
                        Final Project for the Management Course. We conducted a comprehensive analysis of the company in its three main dimensions. We used tools such as <strong class="text-violet-400"
                           > PESTLE, Porter's Five Forces, and the Value Chain</strong
                        >
                        . The project included identifying a key problem and proposing a viable solution, including 
                        <strong class="text-violet-400">feasibility analysis, budgeting, and solution implementation</strong>.                    
                    </p>
                </Step>
            </div>
        </div>
    </section>
    <!-- ABOUT ME-->
    <section
        id="about"
        class=" py-20 pt-10 lg:pt-16 lg:py-32 flex flex-col gap-16 sm:gap-20 md:gap-24 relative"
    >
        <!-- <div class="z-[-1] bg-violet-950 w-screen left-1/2 -translate-x-1/2 top-0 h-full absolute"> </div> -->
        <div
            class="flex flex-col gap-2 text-center relative before:absolute before:top-0 before:left-0 before:w-2/3 before:h-1.5 before:bg-violet-700 after:absolute after:bottom-0 after:right-0 after:w-2/3 after:h-1.5 after:bg-violet-700 py-4"
        >
            <h6 class="text-large sm:text-xl md:text-2xl">
                Want to know more?
            </h6>
            <h3 class="font-semibold text-3xl sm:text-4xl md:text-5xl">
                A bit <span class="poppins text-violet-400">about</span> me.
            </h3>
        </div>
        <p class="mx-auto poppins font-semibold text-lg sm:text-xl md:text-2xl">
            I am . . .
        </p>
        <div class="flex flex-col gap-20 w-full mx-auto max-w-[800px]">
            {#each benefits as benefit, index}
                <!-- <div class="flex flex-col gap-2 mx-auto">
                    <div class="flex items-end gap-4">
                        <p
                            class="poppins text-6xl sm:text-7xl md:text-8xl text-slate-500 font-medium"
                        >
                            {benefit.metric}
                        </p>
                        <p
                            class="text-xl sm:text-2xl md:text-3xl capitalize pb-2"
                        >
                            {benefit.name}
                        </p>
                    </div>
                    <p class="text-center italic">- {benefit.description}</p>
                </div> -->
                <div class="flex gap-6 sm:gap-8">
                    <p
                        class="poppins text-4xl sm:text-5xl md:text-6xl text-slate-500 font-semibold"
                    >
                        0{index + 1}
                    </p>
                    <div class="flex flex-col gap-6 sm:gap-8">
                        <h3 class="text-2xl sm:text-3xl md:text-5xl">
                            {benefit.name}
                        </h3>
                        <p>{benefit.description}</p>
                        
                        <!-- Botón PDF si está disponible -->
                        {#if benefit.pdfUrl}
                            <div class="mt-2">
                                <a 
                                    href={benefit.pdfUrl} 
                                    target="_blank" 
                                    rel="noopener noreferrer"
                                    class="inline-flex items-center gap-2 px-4 py-2 bg-violet-600 hover:bg-violet-700 text-white text-sm font-medium rounded-lg transition-colors duration-200"
                                >
                                    <i class="fas fa-file-pdf"></i>
                                    {benefit.pdfButtonText || "View PDF"}
                                </a>
                            </div>
                        {/if}
                    </div>
                </div>
            {/each}
        </div>
        <h5 class={" text-2xl sm:text-3xl font-semibold text-center poppins "}>
            The <span class="text-violet-400">Complete</span> Package
        </h5>
        <div
            class="flex flex-col overflow-x-auto gap-10 max-w-[900px] mx-auto w-full"
        >
            <div class="bg-gradient-to-br from-slate-50 to-slate-100 rounded-2xl shadow-2xl overflow-hidden border border-slate-200">
                <table class="w-full text-center">
                    <thead class="bg-gradient-to-r from-slate-800 to-slate-900">
                        <tr>
                            <th class="py-4 px-6 text-left text-slate-300 font-medium text-sm tracking-wider"></th>
                            <th class="py-4 px-6 text-slate-300 font-medium text-sm tracking-wider">Candidate #1</th>
                            <th class="py-4 px-6 text-slate-300 font-medium text-sm tracking-wider">Candidate #2</th>
                            <th class="py-4 px-6 text-slate-300 font-medium text-sm tracking-wider">Candidate #3</th>
                            <th class="py-4 px-8 bg-gradient-to-r from-violet-600 to-purple-600 text-white font-semibold text-sm tracking-wider relative">
                                <div class="absolute inset-0 bg-gradient-to-r from-violet-500 to-purple-500 opacity-0 hover:opacity-20 transition-opacity duration-300"></div>
                                <span class="relative">Me ✨</span>
                            </th>
                        </tr>
                    </thead>
                    <tbody class="divide-y divide-slate-200">
                        <tr class="hover:bg-slate-100/50 transition-colors duration-200">
                            <td class="py-4 px-6 text-left font-semibold text-slate-700 bg-slate-50">Dedication</td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-red-100 flex items-center justify-center">
                                        <i class="fa-solid fa-xmark text-red-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-green-100 flex items-center justify-center">
                                        <i class="fa-solid fa-check text-green-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-red-100 flex items-center justify-center">
                                        <i class="fa-solid fa-xmark text-red-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6 bg-gradient-to-r from-violet-50 to-purple-50">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-gradient-to-r from-violet-500 to-purple-500 flex items-center justify-center shadow-lg">
                                        <i class="fa-solid fa-check text-white text-sm"></i>
                                    </div>
                                </div>
                            </td>
                        </tr>
                        <tr class="hover:bg-slate-100/50 transition-colors duration-200">
                            <td class="py-4 px-6 text-left font-semibold text-slate-700 bg-slate-50">Critical Thought</td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-red-100 flex items-center justify-center">
                                        <i class="fa-solid fa-xmark text-red-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-green-100 flex items-center justify-center">
                                        <i class="fa-solid fa-check text-green-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-green-100 flex items-center justify-center">
                                        <i class="fa-solid fa-check text-green-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6 bg-gradient-to-r from-violet-50 to-purple-50">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-gradient-to-r from-violet-500 to-purple-500 flex items-center justify-center shadow-lg">
                                        <i class="fa-solid fa-check text-white text-sm"></i>
                                    </div>
                                </div>
                            </td>
                        </tr>
                        <tr class="hover:bg-slate-100/50 transition-colors duration-200">
                            <td class="py-4 px-6 text-left font-semibold text-slate-700 bg-slate-50">Interpersonal Skills</td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-green-100 flex items-center justify-center">
                                        <i class="fa-solid fa-check text-green-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-green-100 flex items-center justify-center">
                                        <i class="fa-solid fa-check text-green-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-red-100 flex items-center justify-center">
                                        <i class="fa-solid fa-xmark text-red-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6 bg-gradient-to-r from-violet-50 to-purple-50">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-gradient-to-r from-violet-500 to-purple-500 flex items-center justify-center shadow-lg">
                                        <i class="fa-solid fa-check text-white text-sm"></i>
                                    </div>
                                </div>
                            </td>
                        </tr>
                        <tr class="hover:bg-slate-100/50 transition-colors duration-200">
                            <td class="py-4 px-6 text-left font-semibold text-slate-700 bg-slate-50">Logical Reasoning</td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-green-100 flex items-center justify-center">
                                        <i class="fa-solid fa-check text-green-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-red-100 flex items-center justify-center">
                                        <i class="fa-solid fa-xmark text-red-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-green-100 flex items-center justify-center">
                                        <i class="fa-solid fa-check text-green-500 text-sm"></i>
                                    </div>
                                </div>
                            </td>
                            <td class="py-4 px-6 bg-gradient-to-r from-violet-50 to-purple-50">
                                <div class="flex justify-center">
                                    <div class="w-8 h-8 rounded-full bg-gradient-to-r from-violet-500 to-purple-500 flex items-center justify-center shadow-lg">
                                        <i class="fa-solid fa-check text-white text-sm"></i>
                                    </div>
                                </div>
                            </td>
                        </tr>
                    </tbody>
                </table>
            </div>
        </div>
        <div class="mx-auto -mt-12 italic sm:hidden opacity-50">
            <p>Scroll to see more &rarr;</p>
        </div>
        <p class="mx-auto">So why not invest?</p>
    </section>
    <!-- Contador de visitas global -->
    <div class="w-full flex flex-col items-center justify-center py-12">
        <div class="relative bg-gradient-to-r from-violet-600 via-purple-600 to-indigo-600 p-6 rounded-2xl shadow-2xl transform hover:scale-105 transition-all duration-300">
            <!-- Efecto de brillo -->
            <div class="absolute inset-0 bg-gradient-to-r from-violet-400 to-purple-400 rounded-2xl blur-xl opacity-30 animate-pulse"></div>
            
            <!-- Contenido del contador -->
            <div class="relative z-10 text-center">
                <div class="flex items-center justify-center mb-2">
                    <i class="fas fa-eye text-white text-xl mr-2"></i>
                    <span class="text-white text-sm font-medium tracking-wider uppercase">Total Visits</span>
                </div>
                
                <div class="flex items-center justify-center">
                    <span class="text-4xl md:text-5xl font-bold text-white tracking-tight" id="visit-counter">
                        {#if isLoading}
                            <span class="inline-block animate-pulse">●</span>
                            <span class="inline-block animate-pulse animation-delay-200">●</span>
                            <span class="inline-block animate-pulse animation-delay-400">●</span>
                        {:else}
                            <span class="transition-all duration-300 ease-out">
                                {typeof visitCount === 'number' ? visitCount.toLocaleString() : visitCount}
                            </span>
                        {/if}
                    </span>
                </div>
                
                <!-- Línea decorativa -->
                <div class="w-16 h-0.5 bg-white/30 mx-auto mt-3 rounded-full"></div>
            </div>
            
            <!-- Decoración adicional -->
            <div class="absolute top-2 right-2 w-3 h-3 bg-white/20 rounded-full animate-ping"></div>
            <div class="absolute bottom-2 left-2 w-2 h-2 bg-white/15 rounded-full animate-bounce"></div>
        </div>
        
        <!-- Texto adicional -->
        <p class="text-slate-400 text-xs mt-4 opacity-75">Thanks for visiting my portfolio!</p>
    </div>
</main>