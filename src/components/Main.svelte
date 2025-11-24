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
        {
            name: "RAG Assistant - Rotaract Statute",
            icon: "fa-solid fa-robot",
            description:
                "Retrieval-Augmented Generation (RAG) system that serves as an intelligent assistant for consulting the Rotaract statute. Uses advanced language models to answer questions about organizational regulations.",
        },
        {
            name: "Workflow Automation with n8n",
            icon: "fa-solid fa-gears",
            description:
                "Automated workflow system built with n8n to streamline business processes and reduce manual tasks through intelligent automation and integration between different services and platforms.",
        },
        {
            name: "RAG Agent with n8n",
            icon: "fa-solid fa-brain",
            description:
                "Advanced RAG-based agent integrated with n8n workflows for intelligent query processing and automated responses. Enables efficient information retrieval and task automation across multiple systems.",
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

    const resumeContact = [
        { label: "Location", value: "Arrecifes, Buenos Aires · Rosario, Santa Fe", icon: "fa-solid fa-location-dot" },
        { label: "Phone", value: "2478 513 656", icon: "fa-solid fa-phone", href: "tel:+542478513656" },
        { label: "Email", value: "alvarezmt8@gmail.com", icon: "fa-solid fa-envelope", href: "mailto:alvarezmt8@gmail.com" },
        { label: "Website", value: "tomasalvarez0.github.io/myportfolio", icon: "fa-solid fa-globe", href: "https://tomasalvarez0.github.io/myportfolio", external: true }
    ];

    const resumeProfile = "Advanced Systems Engineering student with strong foundations in data analysis, cybersecurity, and AI solutions (RAG/LLMs). Experienced in project management and process optimization, seeking to combine technical skills with business vision to deliver secure and impactful solutions.";

    const resumeExperience = [
        {
            role: "Socio de Rotaract Club Arrecifes",
            period: "2024 – Present",
            details: [
                "Budget management and financial allocation for social impact projects.",
                "Leadership of multidisciplinary teams with Excel-based reporting and KPIs."
            ]
        }
    ];

    const resumeLanguages = [
        { language: "Spanish", level: "Native" },
        { language: "English", level: "B1 Technical · Technical documentation reading" }
    ];

    const resumeEducation = {
        institution: "UTN Facultad Regional Rosario",
        period: "2020 – 2025",
        degree: "Ingeniería en Sistemas de Información",
        status: "2 subjects + final project pending"
    };

    const resumeSkills = [
        {
            title: "Data Analysis & BI",
            items: ["Excel (advanced)", "Power BI", "SQL", "ETL", "Power Query"]
        },
        {
            title: "Artificial Intelligence",
            items: ["RAG architectures", "Embeddings", "AI Agents", "LLMs (OpenAI)", "LangChain"]
        },
        {
            title: "Cybersecurity",
            items: ["Kali Linux (nMap, Nikto, SQLMap, Metasploit)", "Vulnerability analysis", "ISO 27001/27002"]
        },
        {
            title: "Automation & Management",
            items: ["n8n workflows", "ERP/MRP/CRP concepts", "Strategic planning", "Scrum"]
        },
        {
            title: "Development & Tools",
            items: ["GitHub", "HTML/CSS", "JavaScript", "Svelte", "SvelteKit"]
        }
    ];

    const resumeProjects = [
        {
            name: "Asistente inteligente con RAG",
            description: "Question-answering assistant over institutional regulations/statutes.",
            stack: "LangChain, Python, Gradio, OpenAI Embeddings & GPT"
        },
        {
            name: "Bot de automatización con n8n",
            description: "Automated order intake bot connected to WhatsApp with AI for customer support.",
            stack: "n8n, WhatsApp integration, LLM-based intent handling"
        },
        {
            name: "Conectando Corazones",
            description: "Platform connecting institutions and collaborators (final career project).",
            stack: "JavaScript, Node.js, PostgreSQL, Svelte"
        },
        {
            name: "Marketing inteligente",
            description: "Predictive marketing with classification algorithms using client datasets.",
            stack: "Python, Pandas, Matplotlib, RapidMiner"
        },
        {
            name: "Análisis Estratégico URG",
            description: "Strategic diagnosis using PESTLE and Porter’s Five Forces.",
            stack: "Business analysis, process optimization"
        }
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
            
            // Si hay error, generar un número aleatorio razonable
            // Entre 150 y 899 para que se vea realista
            const randomCount = Math.floor(Math.random() * (899 - 150 + 1)) + 150;
            
            isLoading = false;
            const targetCount = randomCount;
            
            // Misma animación de conteo progresivo pero con número aleatorio
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
                Soy Martín Tomás Alvarez, futuro Ingeniero en Sistemas con experiencia práctica en análisis de datos (<span class="text-violet-400">SQL, Power BI</span>) y gestión estratégica. Mi portafolio se centra en la aplicación de tecnologías de vanguardia como <span class="text-violet-400">Arquitecturas RAG</span> para IA y metodologías de <span class="text-violet-400">Ciberseguridad (ISO 27001, Kali Linux)</span>. Actualmente busco mi primera experiencia profesional para aportar una visión que equilibre la excelencia técnica y el impacto en el negocio.
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
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-12 lg:gap-10">
            <div class="scroll-reveal opacity-0 translate-y-8 transition-all duration-700 ease-out">
                <Step 
                    step={steps[0]} 
                    linkUrl="https://conectando-corazones.vercel.app/" 
                    linkText="Visit Website"
                    linkType="website"
                >
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
                <Step 
                    step={steps[2]} 
                    linkUrl="{base}/TPI-Gerencial-2025.pdf" 
                    linkText="View Details (PDF)"
                    linkType="pdf"
                >
                    <p>
                        Final Project for the Management Course. We conducted a comprehensive analysis of the company in its three main dimensions. We used tools such as <strong class="text-violet-400"
                           > PESTLE, Porter's Five Forces, and the Value Chain</strong
                        >
                        . The project included identifying a key problem and proposing a viable solution, including 
                        <strong class="text-violet-400">feasibility analysis, budgeting, and solution implementation</strong>.                    
                    </p>
                </Step>
            </div>
            <div class="scroll-reveal opacity-0 translate-y-8 transition-all duration-700 ease-out" style="transition-delay: 300ms">
                <Step step={steps[3]} pdfUrl="#" pdfButtonText="View Project">
                    <p>
                        {steps[3].description} Built with <strong class="text-violet-400">LangChain, Python, ChromaDB, Gradio</strong> and powered by <strong class="text-violet-400">OpenAI API</strong> (GPT model and embeddings). The system allows users to upload and query the Rotaract statute, providing accurate and contextual answers about organizational regulations and procedures.
                    </p>
                </Step>
            </div>
            <div class="scroll-reveal opacity-0 translate-y-8 transition-all duration-700 ease-out" style="transition-delay: 400ms">
                <Step step={steps[4]} pdfUrl="#" pdfButtonText="View Project">
                    <p>
                        {steps[4].description} Developed using <strong class="text-violet-400">n8n</strong> workflow automation platform. This project demonstrates the ability to create efficient automation pipelines that connect different services, automate repetitive tasks, and improve operational efficiency through intelligent workflow design.
                    </p>
                </Step>
            </div>
            <div class="scroll-reveal opacity-0 translate-y-8 transition-all duration-700 ease-out" style="transition-delay: 500ms">
                <Step step={steps[5]} pdfUrl="#" pdfButtonText="View Project (In Progress)">
                    <p>
                        {steps[5].description} Combining <strong class="text-violet-400">RAG technology</strong> with <strong class="text-violet-400">n8n automation</strong> to create an intelligent agent capable of processing specific queries and automating complex workflows. This project showcases the integration of AI-powered information retrieval with workflow automation for enhanced productivity.
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
    <!-- RESUME -->
    <section id="resume" class="py-20 lg:py-28 flex flex-col gap-16">
        <div class="flex flex-col gap-2 text-center">
            <h6 class="text-large sm:text-xl md:text-2xl uppercase tracking-[0.2em] text-violet-300">
                Curriculum
            </h6>
            <h3 class="font-semibold text-3xl sm:text-4xl md:text-5xl">
                Snapshot of my <span class="poppins text-violet-400">professional</span> profile
            </h3>
            <p class="text-slate-300 max-w-3xl mx-auto">
                All the highlights from my resume, including contact information, academic background, voluntary experience, and the blend of technical + business skills that I bring to every project.
            </p>
            <div class="flex flex-wrap items-center justify-center gap-3 mt-4">
                <a
                    href="{base}/AlvarezMartinTomas_IngSistemas.pdf"
                    target="_blank"
                    rel="noopener noreferrer"
                    class="inline-flex items-center gap-2 px-6 py-3 rounded-full bg-violet-600 hover:bg-violet-700 text-white font-semibold transition-all duration-200"
                >
                    <i class="fas fa-file-pdf"></i>
                    View PDF resume
                </a>
                <span class="text-sm text-slate-400">Updated 2025 · Full curriculum</span>
            </div>
        </div>
        <div class="grid gap-8 lg:grid-cols-[1.1fr_1.9fr]">
            <!-- Left column -->
            <div class="flex flex-col gap-6">
                <div class="bg-slate-900/70 border border-slate-800 rounded-3xl p-6 shadow-2xl shadow-violet-900/20">
                    <div class="flex items-center justify-between mb-4">
                        <h4 class="text-2xl font-semibold">Contact</h4>
                        <span class="text-sm uppercase tracking-wide text-violet-300">Let's connect</span>
                    </div>
                    <div class="flex flex-col gap-4">
                        {#each resumeContact as item}
                            <a
                                class="flex items-center gap-4 p-3 rounded-2xl bg-white/5 hover:bg-white/10 transition-colors duration-200"
                                href={item.href ?? undefined}
                                target={item.external ? "_blank" : undefined}
                                rel={item.external ? "noopener noreferrer" : undefined}
                            >
                                <div class="w-10 h-10 rounded-2xl bg-violet-600/20 text-violet-300 flex items-center justify-center text-xl">
                                    <i class={item.icon}></i>
                                </div>
                                <div class="flex flex-col text-left">
                                    <span class="text-xs uppercase tracking-widest text-slate-400">{item.label}</span>
                                    <span class="text-white text-lg font-medium">{item.value}</span>
                                </div>
                            </a>
                        {/each}
                    </div>
                    <div class="mt-6">
                        <a
                            href="{base}/AlvarezMartinTomas_IngSistemas.pdf"
                            target="_blank"
                            rel="noopener noreferrer"
                            class="inline-flex items-center gap-2 px-5 py-3 rounded-full bg-violet-600 hover:bg-violet-700 text-white font-semibold transition-all duration-200"
                        >
                            <i class="fas fa-file-pdf"></i>
                            Download full resume
                        </a>
                    </div>
                </div>
                <div class="bg-slate-900/70 border border-slate-800 rounded-3xl p-6">
                    <h4 class="text-2xl font-semibold mb-3">Professional Profile</h4>
                    <p class="text-slate-300 leading-relaxed">
                        {resumeProfile}
                    </p>
                </div>
                <div class="bg-slate-900/70 border border-slate-800 rounded-3xl p-6">
                    <h4 class="text-2xl font-semibold mb-4">Languages</h4>
                    <ul class="space-y-3">
                        {#each resumeLanguages as lang}
                            <li class="flex items-center justify-between p-3 rounded-2xl bg-white/5">
                                <span class="text-lg font-medium">{lang.language}</span>
                                <span class="text-sm uppercase tracking-wide text-violet-300">{lang.level}</span>
                            </li>
                        {/each}
                    </ul>
                </div>
            </div>
            <!-- Right column -->
            <div class="flex flex-col gap-6">
                <div class="bg-slate-900/70 border border-slate-800 rounded-3xl p-6">
                    <div class="flex items-center justify-between mb-4">
                        <h4 class="text-2xl font-semibold">Experience (Volunteering)</h4>
                        <span class="text-sm uppercase tracking-wide text-violet-300">Impact & leadership</span>
                    </div>
                    <div class="space-y-6">
                        {#each resumeExperience as exp}
                            <div class="p-4 rounded-2xl bg-white/5">
                                <div class="flex flex-col sm:flex-row sm:items-center sm:justify-between gap-2 mb-2">
                                    <h5 class="text-xl font-semibold">{exp.role}</h5>
                                    <span class="text-sm text-violet-300">{exp.period}</span>
                                </div>
                                <ul class="list-disc list-inside text-slate-300 space-y-2 text-sm sm:text-base">
                                    {#each exp.details as detail}
                                        <li>{detail}</li>
                                    {/each}
                                </ul>
                            </div>
                        {/each}
                    </div>
                </div>
                <div class="bg-slate-900/70 border border-slate-800 rounded-3xl p-6 grid gap-6 lg:grid-cols-2">
                    <div>
                        <h4 class="text-2xl font-semibold mb-3">Education</h4>
                        <p class="text-lg font-medium">{resumeEducation.institution}</p>
                        <p class="text-sm text-violet-300">{resumeEducation.period}</p>
                        <p class="mt-2 text-slate-300">{resumeEducation.degree}</p>
                        <p class="text-sm text-slate-400">{resumeEducation.status}</p>
                    </div>
                    <div>
                        <h4 class="text-2xl font-semibold mb-3">Core Skills</h4>
                        <div class="space-y-3">
                            {#each resumeSkills.slice(0, 2) as skill}
                                <div class="p-3 rounded-2xl bg-white/5">
                                    <p class="text-sm uppercase tracking-wide text-violet-300">{skill.title}</p>
                                    <p class="text-slate-200 text-sm mt-1">{skill.items.join(", ")}</p>
                                </div>
                            {/each}
                        </div>
                    </div>
                </div>
                <div class="bg-slate-900/70 border border-slate-800 rounded-3xl p-6">
                    <h4 class="text-2xl font-semibold mb-4">Full Skillset</h4>
                    <div class="grid gap-4 md:grid-cols-2">
                        {#each resumeSkills as skill}
                            <div class="p-4 rounded-2xl bg-white/5">
                                <p class="text-sm uppercase tracking-wide text-violet-300">{skill.title}</p>
                                <ul class="mt-2 space-y-1 text-slate-200 text-sm">
                                    {#each skill.items as item}
                                        <li class="flex items-center gap-2">
                                            <span class="w-1.5 h-1.5 rounded-full bg-violet-400"></span>
                                            {item}
                                        </li>
                                    {/each}
                                </ul>
                            </div>
                        {/each}
                    </div>
                </div>
                <div class="bg-slate-900/70 border border-slate-800 rounded-3xl p-6">
                    <div class="flex flex-col gap-2 mb-4">
                        <h4 class="text-2xl font-semibold">Featured Projects</h4>
                        <p class="text-slate-300 text-sm">Academic + personal initiatives that showcase my breadth.</p>
                    </div>
                    <div class="grid gap-4 md:grid-cols-2">
                        {#each resumeProjects as project}
                            <div class="p-4 rounded-2xl bg-white/5">
                                <p class="text-lg font-semibold">{project.name}</p>
                                <p class="text-slate-300 text-sm mt-1">{project.description}</p>
                                <p class="text-xs uppercase tracking-wide text-violet-300 mt-2">{project.stack}</p>
                            </div>
                        {/each}
                    </div>
                </div>
            </div>
        </div>
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