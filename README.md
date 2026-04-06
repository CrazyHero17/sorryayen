<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="A heartfelt apology page with thoughtful reflections.">
    <title>I hear you.</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #fefae0;
            color: #4b5563;
        }

        .fade-in {
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.8s ease-out, transform 0.8s ease-out;
        }

        .fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }

        .sunflower-shadow {
            box-shadow: 0 10px 30px -10px rgba(234, 179, 8, 0.2);
        }

        /* Reduced motion support for accessibility */
        @media (prefers-reduced-motion: reduce) {
            .fade-in,
            .fade-in.visible,
            button {
                transition: none;
            }
        }

        /* Better button focus states */
        button:focus-visible {
            outline: 2px solid #eab308;
            outline-offset: 2px;
        }
    </style>
</head>
<body class="antialiased min-h-screen flex flex-col items-center py-16 px-6 relative overflow-hidden bg-[#fefae0]">

    <!-- Decorative background elements with aria-hidden -->
    <div class="fixed top-10 left-10 text-5xl opacity-40 drop-shadow-sm cursor-default select-none pointer-events-none" aria-hidden="true">🌻</div>
    <div class="fixed bottom-20 right-10 text-5xl opacity-40 drop-shadow-sm cursor-default select-none pointer-events-none" aria-hidden="true">🌼</div>
    <div class="fixed top-1/4 right-16 text-4xl opacity-50 drop-shadow-sm transform rotate-12 cursor-default select-none pointer-events-none" aria-hidden="true">🌬️</div>
    <div class="fixed bottom-1/3 left-16 text-3xl opacity-50 drop-shadow-sm -rotate-12 cursor-default select-none pointer-events-none" aria-hidden="true">🌼</div>

    <div class="max-w-2xl w-full space-y-16 relative z-10">
        
        <!-- Header -->
        <div class="fade-in text-center space-y-4 pt-10">
            <h1 class="text-4xl md:text-5xl font-semibold text-gray-800 tracking-tight">You're right. 🌻</h1>
            <p class="text-lg text-amber-700">About everything.</p>
        </div>

        <!-- Sections Container -->
        <div class="space-y-8">
            <!-- Section 1: The Mistakes -->
            <section class="fade-in bg-white/80 backdrop-blur-sm p-8 rounded-2xl sunflower-shadow border border-yellow-200">
                <h2 class="text-xl font-semibold text-amber-600 mb-4">On repeating mistakes...</h2>
                <p class="text-gray-700 leading-relaxed">
                    Alam ko paulit-ulit na lang. I completely understand why you don't believe my words right now. I keep doing the exact same things you've told me hurt you, and I hate that I've made you feel this way. I promise to do better.
                </p>
            </section>

            <!-- Section 2: Communication -->
            <section class="fade-in bg-white/80 backdrop-blur-sm p-8 rounded-2xl sunflower-shadow border border-yellow-200">
                <h2 class="text-xl font-semibold text-yellow-600 mb-4">On how I listen...</h2>
                <blockquote class="border-l-4 border-yellow-400 pl-4 italic text-gray-600 mb-4 bg-yellow-50/50 py-3 rounded-r-lg">
                    "U listen to know, not to understand."
                </blockquote>
                <p class="text-gray-700 leading-relaxed">
                    This hit me really hard because it's true. I've been so focused on just giving a response or defending myself that I completely failed to actually connect with you and understand where you're coming from. I'm working on truly listening.
                </p>
            </section>

            <!-- Section 3: Taking Advantage -->
            <section class="fade-in bg-white/80 backdrop-blur-sm p-8 rounded-2xl sunflower-shadow border border-yellow-200">
                <h2 class="text-xl font-semibold text-orange-500 mb-4">On taking you for granted...</h2>
                <p class="text-gray-700 leading-relaxed">
                    I never want you to feel like I'm taking advantage of your feelings or the fact that you choose me. I've been complacent, and I've failed to handle you sa paraan na deserve mo. That's changing starting now.
                </p>
            </section>
        </div>

        <!-- Section 4: The Ending -->
        <div class="fade-in text-center pt-8 space-y-6">
            <p class="text-amber-800 text-lg font-medium">Take all the space you need. I'll be here, actually working on myself, for when (or if) you're ready. 🌼</p>
            
            <div class="mt-8">
                <button 
                    id="suntokBtn" 
                    class="bg-yellow-400 hover:bg-yellow-500 text-yellow-900 font-semibold py-3 px-8 rounded-full transition-all duration-300 transform hover:scale-105 shadow-md active:scale-95"
                    aria-expanded="false"
                    aria-controls="suntokResponse"
                >
                    About that suntukan...
                </button>
                <p 
                    id="suntokResponse" 
                    class="hidden mt-4 text-orange-600 font-medium animate-pulse"
                    role="status"
                    aria-live="polite"
                >
                    Game. You get a free hit. (I'd let you win anyway. I'm so sorry. 🥊)
                </p>
            </div>
        </div>

    </div>

    <script>
        // Scroll animation observer
        const observerOptions = { threshold: 0.1 };
        const observer = new IntersectionObserver((entries) => {
            entries.forEach(entry => {
                if (entry.isIntersecting) {
                    entry.target.classList.add('visible');
                }
            });
        }, observerOptions);

        document.querySelectorAll('.fade-in').forEach(el => observer.observe(el));

        // Button interaction with better state management
        const suntokBtn = document.getElementById('suntokBtn');
        const suntokResponse = document.getElementById('suntokResponse');

        suntokBtn.addEventListener('click', () => {
            const isExpanded = suntokBtn.getAttribute('aria-expanded') === 'true';
            suntokBtn.setAttribute('aria-expanded', !isExpanded);
            suntokBtn.classList.toggle('hidden');
            suntokResponse.classList.toggle('hidden');
        });

        // Prevent layout shift on button click
        suntokBtn.addEventListener('click', (e) => {
            e.preventDefault();
        });
    </script>
</body>
</html>

