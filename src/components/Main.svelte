<script>
    import Step from "./Step.svelte";

    let steps = [
        {
            name: "Conectando corazones",
            icon: "fa-solid fa-hands-helping",
            description:
                "Conectando corazones is a platform for connecting people in need with those who can help. It is a platform for connecting people in need with those who can help.",
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
            name: "a self taught developer",
            description:
                "I’m an advanced Information Systems Engineering student (expected graduation: Dec. 2025) with a strong interest in data analysis for decision-making. I’m currently improving my SQL skills and training in Power BI. I’m looking for my first professional experience in IT, where I can contribute with commitment, continuous learning, teamwork, and reliability.",
        },
        {
            name: "Passionate About Social Impact and Innovation",
            description:
                "Through academic and volunteer projects, I’ve applied my technical and strategic knowledge to real-world challenges. Projects like Conectando Corazones show my interest in using technology to solve social problems, while work in Smart Marketing and Strategic Analysis demonstrates my ability to apply data science and business tools effectively.",
        },
        {
            name: "Strong Communicator and Team Player",
            description:
                "I value effective communication, teamwork, and leadership, developed through my involvement in Rotaract and collaborative academic projects. I’m proactive, responsible, and organized—skills that I bring to any environment, especially when working on impactful solutions.",
        },
    ];
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
                My <span class="text-violet-400"> favorite tech</span> includes JavaScript
                (NEXT.JS or SvelteKit), TailwindCSS, Node.js + Express.js & PostgreSQL
                or Firebase/Firestore!
            </p>
            <button
                class="blueShadow mx-auto lg:mr-auto lg:ml-0 text-base sm:text-lg md:text-xl poppins relative overflow-hidden px-6 py-3 group rounded-full bg-white text-slate-950"
            >
                <div
                    class="absolute top-0 right-full w-full h-full bg-violet-400 opacity-20 group-hover:translate-x-full z-0 duration-200"
                ></div>
                <h4 class="relative z-9">Get in touch &rarr;</h4>
            </button>
        </div>
        <div class="relative shadow-2xl grid place-items-center ">
            <img
                src={"images/profile.png"}
                alt="Tomas Alvarez profile pic"
                class="object-cover z-[2] max-h-[70vh]"
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
    <section class=" py-20 lg:py-32 flex flex-col gap-24" id="projects">
        <div class="flex flex-col gap-2 text-center">
            <h6 class="text-large sm:text-xl md:text-2xl">
                A few of my creative endeavors.
            </h6>
            <h3 class="font-semibold text-3xl sm:text-4xl md:text-5xl">
                Curious to <span class="poppins text-violet-400">see</span> my work?
            </h3>
        </div>
        
        <div class="grid grid-cols-1 lg:grid-cols-3 gap-12 lg:gap-10">
            <a href="https://conectando-corazones.vercel.app/" target="_blank" rel="noopener noreferrer" aria-label="Visit Conectando corazones project">
            <Step step={steps[0]}>
                <p>
                    {steps[0].description} Using:<strong
                        class="text-violet-400"> Svelte, TailwindCSS, SvelteKit, PostgreSQL </strong
                    >   Final project of the career, in a group with 2 collaborators</p>
            </Step>
            </a>
            <Step step={steps[1]}>
                <p>
                    Data Mining with <strong
                        class="text-violet-400">Python</strong
                    >,
                    <strong class="text-violet-400">RapidMiner & SPSS Statistics</strong
                    >
                    Using a dataset of past customers, we applied various classification and prediction tools to implement smart marketing strategies. The goal was to offer different products tailored to the characteristics of potential clients.
                </p>
            </Step>
            <Step step={steps[2]}>
                <p>
                    Final Project for the Management Course. We conducted a comprehensive analysis of the company in its three main dimensions. We used tools such as <strong class="text-violet-400"
                       > PESTLE, Porter's Five Forces, and the Value Chain</strong
                    >
                    . The project included identifying a key problem and proposing a viable solution, including 
                    <strong class="text-violet-400">feasibility analysis, budgeting, and solution implementation</strong>.                    
                </p>
            </Step>
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
                    </div>
                </div>
            {/each}
        </div>
        <h5 class={" text-2xl sm:text-3xl font-semibold text-center poppins "}>
            The <span class="text-violet-400">Complete</span> Package
        </h5>
        <div
            class="flex flex-col overflow-x-scroll gap-10 max-w-[800px] mx-auto w-full"
        >
            <table class="bg-white text-slate-700 rounded text-center">
                <thead class={"border-b border-solid border-slate-200  "}>
                    <tr class="">
                        <th></th>
                        <th class="whitespace-nowrap p-2 px-4">Candidate #1</th>
                        <th class="whitespace-nowrap p-2 px-4">Candidate #2</th>
                        <th class="whitespace-nowrap p-2 px-4">Candidate #3</th>
                        <th
                            class="bg-violet-700 text-white whitespace-nowrap p-4 px-8"
                            >Me</th
                        >
                    </tr>
                </thead>
                <tbody>
                    <tr class="border-b border-solid border-slate-200">
                        <td
                            class="border-r border-solid border-white pl-4 pr-8 py-4 font-semibold text-sm"
                            >Dedication</td
                        >
                        <td><i class="fa-solid fa-xmark text-slate-500"></i></td>
                        <td><i class="fa-solid fa-check text-slate-500"></i></td>
                        <td><i class="fa-solid fa-xmark text-slate-500"></i></td>
                        <td><i class="fa-solid fa-check text-green-500"></i></td>
                    </tr>
                    <tr class="border-b border-solid border-slate-200">
                        <td
                            class="border-r border-solid border-white pl-4 pr-8 py-4 font-semibold text-sm"
                            >Critical Thought</td
                        >
                        <td><i class="fa-solid fa-xmark text-slate-500"></i></td>
                        <td><i class="fa-solid fa-check text-slate-500"></i></td>
                        <td><i class="fa-solid fa-check text-slate-500"></i></td>
                        <td><i class="fa-solid fa-check text-green-500"></i></td>
                    </tr>
                    <tr>
                        <td
                            class="border-r border-solid border-white pl-4 pr-8 py-4 font-semibold text-sm"
                            >Interpersonal Skills</td
                        >
                        <td><i class="fa-solid fa-check text-slate-500"></i></td>
                        <td><i class="fa-solid fa-check text-slate-500"></i></td>
                        <td><i class="fa-solid fa-xmark text-slate-500"></i></td>
                        <td><i class="fa-solid fa-check text-green-500"></i></td>
                    </tr>
                    <tr class="border-t border-solid border-slate-200">
                        <td
                            class="border-r border-solid border-white pl-4 pr-8 py-4 font-semibold text-sm"
                            >Logical Reasoning</td
                        >
                        <td><i class="fa-solid fa-check text-slate-500"></i></td>
                        <td><i class="fa-solid fa-xmark text-slate-500"></i></td>
                        <td><i class="fa-solid fa-check text-slate-500"></i></td>
                        <td><i class="fa-solid fa-check text-green-500"></i></td>
                    </tr>
                </tbody>
            </table>
        </div>
        <div class="mx-auto -mt-12 italic sm:hidden opacity-50">
            <p>Scroll to see more &rarr;</p>
        </div>
        <p class="mx-auto">So why not invest?</p>
    </section>
</main>