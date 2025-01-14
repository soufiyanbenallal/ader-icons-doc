<template>
  <div class="bg-white">
    <div class="w-full p-1">
      <div
        class="relative isolate overflow-hidden bg-gray-900 px-6 py-12 text-center shadow-2xl sm:rounded-3xl sm:px-16">
        <svg
          class="absolute inset-x-0 top-0 -z-10 size-full stroke-gray-800 [mask-image:radial-gradient(100%_100%_at_top_right,white,transparent)]"
          aria-hidden="true">
          <defs>
            <pattern id="0787a7c5-978c-4f66-83c7-11c213f99cb7" width="200" height="200" x="50%" y="-1"
              patternUnits="userSpaceOnUse">
              <path d="M.5 200V.5H200" fill="none" />
            </pattern>
          </defs>
          <rect width="100%" height="100%" stroke-width="0" fill="url(#0787a7c5-978c-4f66-83c7-11c213f99cb7)" />
        </svg>
        <svg viewBox="0 0 1024 1024"
          class="absolute left-1/2 -top-[11%] opacity-60 -z-10 size-[100vw] -translate-x-1/2 [mask-image:radial-gradient(closest-side,white,transparent)]"
          aria-hidden="true">
          <circle cx="512" cy="512" r="512" fill="url(#827591b1-ce8c-4110-b064-7cb85a0b1217)" fill-opacity="0.7" />
          <defs>
            <radialGradient id="827591b1-ce8c-4110-b064-7cb85a0b1217">
              <stop stop-color="#7775D6" />
              <stop offset="1" stop-color="#E935C1" />
            </radialGradient>
          </defs>
        </svg>
        <img src="/vite.svg" class="logo mx-auto" alt="Vite logo" />

        <h2 class="text-balance text-4xl font-semibold tracking-tight text-white sm:text-5xl">
          Beautiful hand-crafted SVG icons <br> by ader-solutions
        </h2>
        <p class="mx-auto mt-6 max-w-xl text-pretty text-lg/8 text-gray-400">
          A Curated Collection of Scalable Vector Icons for Digital Design
        </p>

        <div class="mt-10 gap-x-6">
          <slot />
        </div>
      </div>
    </div>
  </div>
</template>
