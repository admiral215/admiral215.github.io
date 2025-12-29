<script>
    import { theme } from '$lib/stores/theme';
    import { fade, fly } from 'svelte/transition';
    import { onMount } from 'svelte';

    const texts = [
        'Building with purpose',
        'Solving meaningful problems',
        'Learning every day'
    ];

    let displayText = '';
    let index = 0;
    let charIndex = 0;
    let isDeleting = false;
    let typingSpeed = 100;

    onMount(() => {
        const type = () => {
            const currentText = texts[index];

            if (!isDeleting && charIndex < currentText.length) {
                displayText += currentText[charIndex];
                charIndex++;
                typingSpeed = 100;
            } else if (isDeleting && charIndex > 0) {
                displayText = currentText.substring(0, charIndex - 1);
                charIndex--;
                typingSpeed = 50;
            } else if (!isDeleting && charIndex === currentText.length) {
                isDeleting = true;
                typingSpeed = 2000;
            } else if (isDeleting && charIndex === 0) {
                isDeleting = false;
                index = (index + 1) % texts.length;
                typingSpeed = 500;
            }

            setTimeout(type, typingSpeed);
        };

        type();
    });
</script>

<div class="min-h-screen flex items-center justify-center">

    <button
            class="absolute top-8 right-8 px-4 py-2 text-xs uppercase tracking-wider
               "
            on:click={() => theme.update(t => t === 'light' ? 'dark' : 'light')}
    >
        {#if $theme === 'light'}
            <svg xmlns="http://www.w3.org/2000/svg"
                 viewBox="0 0 24 24"
                 fill="none"
                 stroke="currentColor"
                 stroke-width="1.5"
                 class="w-6 h-6">
                <path d="M21 12.8A9 9 0 1 1 11.2 3
           a7 7 0 0 0 9.8 9.8z"/>
            </svg>
        {:else}
            <svg xmlns="http://www.w3.org/2000/svg"
                 viewBox="0 0 24 24"
                 fill="none"
                 stroke="currentColor"
                 stroke-width="1.5"
                 class="w-6 h-6">
                <path d="M12 3a6 6 0 0 1 3 11.25V17a1 1 0 0 1-1 1h-4a1 1 0 0 1-1-1v-2.75A6 6 0 0 1 12 3z"/>
                <path d="M9 21h6"/>
            </svg>
        {/if}
    </button>

    <section class="text-center px-6 max-w-3xl">

        <div class="inline-block mb-8" in:fade={{ duration: 600 }}>
            <img
                    src="/portfolio/photo.webp"
                    alt="Rully Admiral"
                    class="w-40 h-40 object-cover
                       border-4 border-neutral-800 dark:border-neutral-200"
            />
        </div>

        <h1 class="text-5xl md:text-6xl font-bold uppercase tracking-tight mb-3"
            in:fly={{ y: 20, delay: 200 }}>
            Rully Admiral
        </h1>

        <div class="w-20 h-px bg-neutral-800 dark:bg-neutral-100 mx-auto mb-6"
             in:fade={{ delay: 300 }}></div>

        <p class="text-sm uppercase tracking-widest font-medium mb-8"
           in:fade={{ delay: 400 }}>
            Software Engineer
        </p>

        <div class="h-6 mb-12"
             in:fade={{ delay: 500 }}>
            <p class="font-mono text-sm">
                {displayText}<span class="inline-block w-2 h-4 bg-neutral-900 dark:bg-neutral-100 ml-1 animate-blink"></span>
            </p>
        </div>

        <div class="flex gap-4 justify-center flex-wrap mb-12"
             in:fly={{ y: 20, delay: 600 }}>
            <a
                    href="/portfolio/CV_RullyAdmiral.pdf"
                    target="_blank"
                    class="px-10 py-3 text-sm uppercase tracking-wider font-semibold
                    border border-neutral-300 hover:border-neutral-800 dark:border-neutral-700 dark:hover:bg-neutral-300"
            >
                Resume
            </a>
        </div>

        <div class="flex justify-center gap-6"
             in:fade={{ delay: 700 }}>
            <a
                    href="https://linkedin.com/in/rully-admiral-1aa315287"
                    target="_blank"
                    class="p-3 border border-neutral-300 dark:border-neutral-700
                       hover:border-neutral-800 dark:hover:border-neutral-200
                       "
                    aria-label="LinkedIn"
            >
                <svg class="w-5 h-5"
                     xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M19 0h-14c-2.761 0-5 2.239-5 5v14c0 2.761 2.239 5 5 5h14c2.762 0 5-2.239 5-5v-14c0-2.761-2.238-5-5-5zm-11 19h-3v-11h3v11zm-1.5-12.268c-.966 0-1.75-.79-1.75-1.764s.784-1.764 1.75-1.764 1.75.79 1.75 1.764-.783 1.764-1.75 1.764zm13.5 12.268h-3v-5.604c0-3.368-4-3.113-4 0v5.604h-3v-11h3v1.765c1.396-2.586 7-2.777 7 2.476v6.759z"/>
                </svg>
            </a>

            <a
                    href="https://github.com/admiral215"
                    target="_blank"
                    class="p-3 border border-neutral-300 dark:border-neutral-700
                       hover:border-neutral-800 dark:hover:border-neutral-200
                       "
                    aria-label="GitHub"
            >
                <svg class="w-5 h-5"
                     fill="currentColor" viewBox="0 0 24 24">
                    <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z"/>
                </svg>
            </a>

            <a
                    href="mailto:rullyadmiral@gmail.com"
                    class="p-3 border border-neutral-300 dark:border-neutral-700
                       hover:border-neutral-800 dark:hover:border-neutral-200
                       "
                    aria-label="Email"
            >
                <svg class="w-5 h-5"
                     fill="none" stroke="currentColor" viewBox="0 0 24 24" stroke-width="2">
                    <path stroke-linecap="round" stroke-linejoin="round"
                          d="M3 8l7.89 5.26a2 2 0 002.22 0L21 8M5 19h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v10a2 2 0 002 2z"/>
                </svg>
            </a>
        </div>
    </section>
</div>