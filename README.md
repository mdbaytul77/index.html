<!DOCTYPE html>
<html lang="bn" class="dark">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>NovaSiri AI — Study & Voice Assistant (GitHub Pages Ready)</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Hind+Siliguri:wght@400;500;600;700&family=Inter:wght@400;500;600;700;800&display=swap" rel="stylesheet" />
  <script>
    tailwind.config = {
      darkMode: 'class',
      theme: {
        extend: {
          fontFamily: {
            sans: ['Inter', 'Hind Siliguri', 'system-ui', 'sans-serif'],
          },
          colors: {
            surface: '#0d1117',
            card: '#161b22',
            cardAlt: '#1f2630',
            line: '#30363d',
            brand: '#38bdf8',
            study: '#22c55e',
            accentPurple: '#a855f7',
            dangerRed: '#ef4444',
          },
        },
      },
    };
  </script>
  <style>
    * {
      -webkit-tap-highlight-color: transparent;
      box-sizing: border-box;
    }
    html, body {
      background-color: #0d1117;
      color: #f0f6fc;
      font-family: 'Inter', 'Hind Siliguri', sans-serif;
      overflow-x: hidden;
    }
    .no-scrollbar::-webkit-scrollbar {
      display: none;
    }
    .no-scrollbar {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }
    @keyframes pulseRing {
      0% { transform: scale(0.92); opacity: 0.7; }
      70% { transform: scale(1.28); opacity: 0; }
      100% { transform: scale(1.28); opacity: 0; }
    }
    .listening-ring {
      animation: pulseRing 1.5s cubic-bezier(0.24, 0, 0.38, 1) infinite;
    }
  </style>
</head>
<body class="min-h-screen flex flex-col bg-surface text-slate-100">

  <!-- Top Header -->
  <header class="sticky top-0 z-30 bg-surface/95 backdrop-blur-md border-b border-line px-3 py-2.5">
    <div class="max-w-2xl mx-auto flex items-center justify-between gap-2">
      <div class="flex items-center gap-2 min-w-0">
        <button
          type="button"
          id="brandResetBtn"
          aria-label="Home and Reset View"
          class="w-9 h-9 rounded-xl bg-gradient-to-tr from-brand via-accentPurple to-pink-500 flex items-center justify-center shrink-0 shadow-md active:scale-95 transition"
        >
          <!-- Inline SVG Spark Logo -->
          <svg class="w-5 h-5 text-white" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
            <path d="M12 2l2.35 6.9L21.25 11l-6.9 2.35L12 20.25l-2.35-6.9L2.75 11l6.9-2.1L12 2z" />
          </svg>
        </button>
        <div class="truncate">
          <div class="flex items-center gap-1.5">
            <span class="font-bold text-sm sm:text-base tracking-tight text-white truncate">NovaSiri AI</span>
            <button
              type="button"
              id="githubBadgeBtn"
              class="text-[10px] font-semibold px-2 py-0.5 rounded-full bg-cardAlt text-brand border border-line hover:border-brand transition shrink-0"
            >
              GitHub Pages
            </button>
          </div>
          <p id="headerStatusSub" class="text-[11px] text-slate-400 truncate">Ready • Auto Language Match</p>
        </div>
      </div>

      <!-- Dedicated Top "পড়ালেখা" Button -->
      <div class="flex items-center gap-1.5 shrink-0">
        <button
          type="button"
          id="topStudyBtn"
          class="flex items-center gap-1.5 px-3 py-2 rounded-xl bg-study text-slate-950 font-bold text-xs sm:text-sm hover:brightness-110 active:scale-95 transition shadow"
        >
          <!-- Inline SVG Book Icon -->
          <svg class="w-4 h-4 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.3" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 6.253v13m0-13C10.832 5.477 9.246 5 7.5 5S4.168 5.477 3 6.253v13C4.168 18.477 5.754 18 7.5 18s3.332.477 4.5 1.253m0-13C13.168 5.477 14.754 5 16.5 5c1.747 0 3.332.477 4.5 1.253v13C19.832 18.477 18.247 18 16.5 18c-1.746 0-3.332.477-4.5 1.253" />
          </svg>
          <span>পড়ালেখা</span>
        </button>

        <button
          type="button"
          id="stopSpeechBtn"
          aria-label="Stop Voice Output"
          title="Stop Voice"
          class="p-2 rounded-xl bg-card border border-line text-slate-300 hover:text-white hover:bg-cardAlt active:scale-95 transition"
        >
          <!-- Inline SVG Volume Off / Stop Icon -->
          <svg class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" d="M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z" />
            <path stroke-linecap="round" stroke-linejoin="round" d="M17 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2" />
          </svg>
        </button>
      </div>
    </div>
  </header>

  <!-- Main Content -->
  <main class="flex-1 w-full max-w-2xl mx-auto px-3 pt-3 pb-44 space-y-3">

    <!-- Language Mode Selector Card -->
    <section class="bg-card border border-line rounded-2xl p-3 space-y-2.5">
      <div class="flex items-center justify-between gap-2 flex-wrap">
        <span class="text-xs font-bold text-slate-200 flex items-center gap-1.5">
          <!-- Inline SVG Globe / Translate Icon -->
          <svg class="w-4 h-4 text-brand" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" d="M3 5h12M9 3v2m1.048 9.5A18.022 18.022 0 016.412 9m6.088 9h7M11 21l5-10 5 10M12.751 5C11.783 10.77 8.07 15.61 3 18.129" />
          </svg>
          <span>ভাষা মোড (Language Mode)</span>
        </span>
        <span id="activeLangBadge" class="text-[11px] font-semibold px-2.5 py-0.5 rounded-full bg-brand/15 text-brand border border-brand/30">
          Auto Match (EN→EN / BN→BN)
        </span>
      </div>

      <div class="grid grid-cols-2 sm:grid-cols-4 gap-1.5">
        <button
          type="button"
          data-lang-mode="auto"
          class="lang-mode-btn px-2.5 py-2 rounded-xl text-xs font-semibold border border-brand bg-brand/20 text-white active:scale-95 transition text-center"
        >
          Auto Smart
        </button>
        <button
          type="button"
          data-lang-mode="bn-bn"
          class="lang-mode-btn px-2.5 py-2 rounded-xl text-xs font-semibold border border-line bg-cardAlt text-slate-300 hover:text-white active:scale-95 transition text-center"
        >
          বাংলা ↔ বাংলা
        </button>
        <button
          type="button"
          data-lang-mode="en-en"
          class="lang-mode-btn px-2.5 py-2 rounded-xl text-xs font-semibold border border-line bg-cardAlt text-slate-300 hover:text-white active:scale-95 transition text-center"
        >
          English ↔ English
        </button>
        <button
          type="button"
          data-lang-mode="en-bn"
          id="enToBnModeBtn"
          class="lang-mode-btn px-2.5 py-2 rounded-xl text-xs font-semibold border border-line bg-cardAlt text-slate-300 hover:text-white active:scale-95 transition text-center"
        >
          আমি EN → তুমি BN
        </button>
      </div>
      <p id="langModeHint" class="text-[11px] text-slate-400 leading-relaxed">
        ইংরেজি বললে/লিখলে ইংরেজিতে উত্তর পাবেন, বাংলায় বললে/লিখলে বাংলায় উত্তর পাবেন। অথবা বলুন: "আমি ইংরেজি বলবো তুমি বাংলা বলবে"।
      </p>
    </section>

    <!-- Voice Assistant Hub Card -->
    <section class="bg-card border border-line rounded-2xl p-3.5 shadow-lg">
      <div class="flex items-center gap-3.5">
        <div class="relative shrink-0">
          <div id="listenPulseRing" class="hidden absolute inset-0 rounded-full bg-brand/40 listening-ring pointer-events-none"></div>
          <button
            type="button"
            id="mainMicBtn"
            aria-label="Start or Stop Voice Input"
            class="relative w-16 h-16 rounded-full bg-gradient-to-tr from-brand via-accentPurple to-pink-500 flex items-center justify-center text-white shadow-lg active:scale-95 transition"
          >
            <!-- Inline SVG Microphone Icon -->
            <svg class="w-7 h-7" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true">
              <path stroke-linecap="round" stroke-linejoin="round" d="M12 18.75a6 6 0 006-6v-1.5m-6 7.5a6 6 0 01-6-6v-1.5m6 7.5v3.75m-3.75 0h7.5M12 15.75a3 3 0 01-3-3V4.5a3 3 0 116 0v8.25a3 3 0 01-3 3z" />
            </svg>
          </button>
        </div>

        <div class="flex-1 min-w-0">
          <div class="flex items-center gap-2">
            <span id="micStatePill" class="text-[11px] font-bold px-2 py-0.5 rounded-full bg-cardAlt text-slate-300 border border-line">
              Mic Idle
            </span>
            <span id="speechSupportNote" class="text-[10px] text-slate-400 truncate"></span>
          </div>
          <p id="liveSpeechPreview" class="text-sm font-medium text-white mt-1.5 break-words">
            মাইক্রোফোনে চাপ দিন অথবা নিচে লিখুন: "কল হামিদ", "ওপেন instagram", বা "পড়ালেখা"।
          </p>
        </div>
      </div>

      <!-- Quick Action Row: পড়ালেখা, কল হামিদ, ওপেন Instagram, নতুন ফ্যাক্ট -->
      <div class="grid grid-cols-2 sm:grid-cols-4 gap-2 mt-3.5">
        <button
          type="button"
          id="quickStudyBtn"
          class="flex items-center justify-center gap-1.5 py-2.5 px-2.5 rounded-xl bg-study/15 border border-study/40 text-study hover:bg-study/25 text-xs font-bold active:scale-95 transition"
        >
          <!-- Inline SVG Graduation / Book -->
          <svg class="w-4 h-4 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 14l9-5-9-5-9 5 9 5z" />
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 14l6.16-3.422a12.083 12.083 0 01.665 6.479A11.952 11.952 0 0012 20.055a11.952 11.952 0 00-6.824-2.998 12.078 12.078 0 01.665-6.479L12 14z" />
          </svg>
          <span>পড়ালেখা</span>
        </button>

        <button
          type="button"
          id="quickCallHamidBtn"
          class="flex items-center justify-center gap-1.5 py-2.5 px-2.5 rounded-xl bg-emerald-500/15 border border-emerald-500/40 text-emerald-300 hover:bg-emerald-500/25 text-xs font-bold active:scale-95 transition"
        >
          <!-- Inline SVG Phone Icon -->
          <svg class="w-4 h-4 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" d="M3 5a2 2 0 012-2h3.28a1 1 0 01.948.684l1.498 4.493a1 1 0 01-.502 1.21l-2.257 1.13a11.042 11.042 0 005.516 5.516l1.13-2.257a1 1 0 011.21-.502l4.493 1.498a1 1 0 01.684.949V19a2 2 0 01-2 2h-1C9.716 21 3 14.284 3 6V5z" />
          </svg>
          <span>কল হামিদ</span>
        </button>

        <button
          type="button"
          id="quickOpenInstaBtn"
          class="flex items-center justify-center gap-1.5 py-2.5 px-2.5 rounded-xl bg-pink-500/15 border border-pink-500/40 text-pink-300 hover:bg-pink-500/25 text-xs font-bold active:scale-95 transition"
        >
          <!-- Inline SVG Camera / Instagram Icon -->
          <svg class="w-4 h-4 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true">
            <rect x="2.5" y="2.5" width="19" height="19" rx="5" />
            <circle cx="12" cy="12" r="4" />
            <circle cx="17.5" cy="6.5" r="1" fill="currentColor" />
          </svg>
          <span>Instagram</span>
        </button>

        <button
          type="button"
          id="quickFactBtn"
          class="flex items-center justify-center gap-1.5 py-2.5 px-2.5 rounded-xl bg-amber-500/15 border border-amber-500/40 text-amber-300 hover:bg-amber-500/25 text-xs font-bold active:scale-95 transition"
        >
          <!-- Inline SVG Lightbulb Icon -->
          <svg class="w-4 h-4 shrink-0" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" d="M9.663 17h4.673M12 3v1m6.364 1.636l-.707.707M21 12h-1M4 12H3m3.343-5.657l-.707-.707m2.828 9.9a5 5 0 117.072 0l-.548.547A3.374 3.374 0 0014 18.469V19a2 2 0 11-4 0v-.531c0-.895-.356-1.754-.988-2.386l-.548-.547z" />
          </svg>
          <span>নতুন ফ্যাক্ট</span>
        </button>
      </div>
    </section>

    <!-- Dedicated পড়ালেখা (Study Mode) Panel -->
    <section id="studyPanel" class="bg-card border border-study/40 rounded-2xl p-3.5 space-y-3 shadow-lg">
      <div class="flex items-center justify-between gap-2">
        <div class="flex items-center gap-2">
          <span class="w-2.5 h-2.5 rounded-full bg-study"></span>
          <h2 class="text-sm font-bold text-white">পড়ালেখা (Study Companion)</h2>
        </div>
        <button
          type="button"
          id="toggleStudyCollapseBtn"
          class="text-xs font-semibold text-study hover:underline px-2 py-1"
        >
          Hide / Show
        </button>
      </div>

      <div id="studyPanelBody" class="space-y-2.5">
        <div class="grid grid-cols-2 sm:grid-cols-4 gap-2">
          <button
            type="button"
            data-study-prompt="গণিতের দ্বিঘাত সমীকরণ সমাধান করার সহজ নিয়ম ও একটি উদাহরণ দাও।"
            class="study-topic-btn p-2.5 rounded-xl bg-cardAlt hover:bg-slate-800 border border-line text-left active:scale-95 transition"
          >
            <span class="block text-xs font-bold text-study">📐 গণিত (Math)</span>
            <span class="block text-[11px] text-slate-400 mt-0.5">সহজ নিয়ম ও সমাধান</span>
          </button>

          <button
            type="button"
            data-study-prompt="বিজ্ঞান ও পদার্থবিজ্ঞানের নিউটনের ৩টি সূত্র সহজ উদাহরণসহ বুঝিয়ে দাও।"
            class="study-topic-btn p-2.5 rounded-xl bg-cardAlt hover:bg-slate-800 border border-line text-left active:scale-95 transition"
          >
            <span class="block text-xs font-bold text-brand">🔬 বিজ্ঞান (Science)</span>
            <span class="block text-[11px] text-slate-400 mt-0.5">সূত্র ও ব্যাখ্যা</span>
          </button>

          <button
            type="button"
            data-study-prompt="পড়ালেখায় মনোযোগ বাড়ানো ও পরীক্ষার সেরা প্রস্তুতির জন্য ৫টি কার্যকর সাজেশন দাও।"
            class="study-topic-btn p-2.5 rounded-xl bg-cardAlt hover:bg-slate-800 border border-line text-left active:scale-95 transition"
          >
            <span class="block text-xs font-bold text-amber-300">🎯 সাজেশন (Tips)</span>
            <span class="block text-[11px] text-slate-400 mt-0.5">পরীক্ষার প্রস্তুতি</span>
          </button>

          <button
            type="button"
            data-study-prompt="Explain how a basic DC motor or LED circuit works in simple steps."
            class="study-topic-btn p-2.5 rounded-xl bg-cardAlt hover:bg-slate-800 border border-line text-left active:scale-95 transition"
          >
            <span class="block text-xs font-bold text-purple-300">⚡ Circuits & Tech</span>
            <span class="block text-[11px] text-slate-400 mt-0.5">Step-by-step guide</span>
          </button>
        </div>

        <!-- Hamid Phone Number Config Strip for "কল হামিদ" -->
        <div class="flex flex-col sm:flex-row sm:items-center justify-between gap-2 pt-2 border-t border-line">
          <label for="hamidPhoneInput" class="text-xs text-slate-300 font-medium">
            হামিদ-এর ফোন নম্বর ("কল হামিদ" বললে কল হবে):
          </label>
          <div class="flex items-center gap-1.5">
            <input
              id="hamidPhoneInput"
              type="tel"
              value="+8801711000000"
              class="w-40 sm:w-44 bg-surface border border-line rounded-xl px-2.5 py-1.5 text-xs text-white font-mono focus:outline-none focus:border-study"
            />
            <button
              type="button"
              id="saveHamidPhoneBtn"
              class="px-3 py-1.5 rounded-xl bg-cardAlt hover:bg-slate-700 border border-line text-xs font-semibold text-white active:scale-95 transition"
            >
              Save
            </button>
          </div>
        </div>
      </div>
    </section>

    <!-- Action Cards Zone (Call Hamid / Open Instagram) -->
    <div id="actionCardsArea" class="space-y-2.5"></div>

    <!-- Conversation & Answers Feed -->
    <section id="chatFeed" class="space-y-3" aria-live="polite">
      <article class="bg-card border border-line rounded-2xl p-3.5 space-y-2">
        <div class="flex items-center justify-between">
          <span class="text-[11px] font-bold px-2 py-0.5 rounded-full bg-brand/15 text-brand">NovaSiri AI</span>
          <button
            type="button"
            data-speak-target="welcomeMsg"
            class="speak-msg-btn inline-flex items-center gap-1 text-xs font-semibold text-slate-300 hover:text-white bg-cardAlt px-2.5 py-1 rounded-lg border border-line active:scale-95 transition"
          >
            <!-- Inline SVG Speaker Icon -->
            <svg class="w-3.5 h-3.5 text-brand" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true">
              <path stroke-linecap="round" stroke-linejoin="round" d="M15.536 8.464a5 5 0 010 7.072m2.828-9.9a9 9 0 010 12.728M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 5v14c0 .891-1.077 1.337-1.707.707L5.586 15z" />
            </svg>
            <span>শুনুন</span>
          </button>
        </div>
        <div id="welcomeMsg" class="text-sm text-slate-200 leading-relaxed space-y-1.5">
          <p class="font-semibold text-white">স্বাগতম! আমি আপনার AI ভয়েস ও পড়ালেখা অ্যাসিস্ট্যান্ট।</p>
          <p class="text-xs text-slate-300">
            • <b>পড়ালেখা:</b> গণিত, বিজ্ঞান, সাজেশন ও যেকোনো শিক্ষামূলক প্রশ্নের উত্তর পাবেন।<br/>
            • <b>ভাষা:</b> ইংরেজি বললে ইংরেজি, বাংলা বললে বাংলা। অথবা বলুন <b>"আমি ইংরেজি বলবো তুমি বাংলা বলবে"</b>।<br/>
            • <b>ভয়েস কমান্ড:</b> বলুন <b>"কল হামিদ"</b> অথবা <b>"ওপেন instagram"</b>।<br/>
            • <b>নিরাপত্তা:</b> কোনো খারাপ কিছু চাইলে বলব: <b>"এটা আমার আইনের বাইরে"</b>।
          </p>
        </div>
      </article>
    </section>

  </main>

  <!-- Fixed Bottom Input + Navigation Bar -->
  <footer class="fixed bottom-0 inset-x-0 z-30 bg-surface/95 backdrop-blur-md border-t border-line">
    <div class="max-w-2xl mx-auto px-3 pt-2 pb-1.5">
      <form id="promptForm" class="flex items-center gap-2 bg-card border border-line rounded-2xl p-1.5 pl-3 focus-within:border-brand transition">
        <input
          id="promptInput"
          type="text"
          autocomplete="off"
          placeholder="প্রশ্ন লিখুন, 'কল হামিদ' বা 'ওপেন instagram' বলুন..."
          class="flex-1 bg-transparent text-sm text-white placeholder-slate-400 focus:outline-none min-w-0"
        />
        <button
          type="button"
          id="inlineMicBtn"
          aria-label="Voice Input"
          class="p-2.5 rounded-xl bg-cardAlt hover:bg-slate-700 text-brand active:scale-95 transition shrink-0"
        >
          <!-- Inline SVG Mic -->
          <svg class="w-4 h-4" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2.2" aria-hidden="true">
            <path stroke-linecap="round" stroke-linejoin="round" d="M12 18.75a6 6 0 006-6v-1.5m-6 7.5a6 6 0 01-6-6v-1.5m6 7.5v3.75m-3.75 0h7.5M12 15.75a3 3 0 01-3-3V4.5a3 3 0 116 0v8.25a3 3 0 01-3 3z" />
          </svg>
        </button>
        <button
          type="submit"
          id="sendPromptBtn"
          aria-label="Send Message"
          cl
