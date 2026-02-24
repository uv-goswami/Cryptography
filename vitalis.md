# 🏆 VITALIS: THE MASTER HACKATHON GUIDE

## PART 1: What You Actually Built (Explain it to yourselves first)

You need to realize that you didn't just build a "website." You built a **Local Edge-Computing AI Application**. This is cutting-edge engineering. Here is exactly what your code does in plain English:

1. **The Brain (RunAnywhere SDK & WebAssembly):**
* *Normally:* Apps send text to a cloud server (like ChatGPT), wait, and get text back.
* *What you did:* You used **WebAssembly (WASM)**. WASM takes heavy, complex C++ AI code and allows it to run directly inside Google Chrome or Safari. Your app literally turns the user's phone or laptop into a mini AI server. It uses the device's own graphics card (**WebGPU**) or processor (**CPU**) to generate answers.


2. **The Vault (OPFS & LocalStorage):**
* *Normally:* AI models are massive (gigabytes). Downloading them every time would crash the app.
* *What you did:* You utilized the **Origin Private File System (OPFS)**. This is a hidden, highly secure, high-speed "hard drive" inside the browser. When the user clicks "Download AI", the model saves there *permanently*. You also used standard `LocalStorage` for their health profile. **Zero data goes to the internet.**


3. **The Shell (Progressive Web App - PWA):**
* *Normally:* You have to go to the App Store or Play Store to download an app.
* *What you did:* You built a PWA with a **Service Worker**. A Service Worker is a script that runs in the background and intercepts network requests. It caches all your React UI files. When the user opens the app, it loads instantly from the cache, making it work seamlessly in **Airplane Mode**.



---

## PART 2: The Perfect Demo Script (5 Minutes)

Do not wing this. Have one person talk, and one person share their screen to drive the app. **CRITICAL: Download all AI models onto the demo computer *before* the call begins so you don't waste time on a loading bar.**

**Step 1: The Hook (1 minute)**

* **Speaker:** "Hi judges. Current health AI apps have a fatal flaw: to get personalized coaching, you have to surrender your most intimate medical and biological data to cloud servers. Furthermore, they require constant internet, shutting down when you're hiking, flying, or in a gym basement. We built **Vitalis** to fix this. Vitalis is a 100% offline, private-by-design Sovereign AI Health Coach."

**Step 2: The UI & Profile (1 minute)**

* **Driver:** *Shows the Profile Tab.*
* **Speaker:** "Everything you see here—name, weight, goals—is aggressively sandboxed using local storage. There is no backend database. We also built a 'Model Manager' allowing users to scale the AI to their device. We are using the Liquid Foundation Model for standard devices, and a lightning-fast SmolLM2 model for older phones."

**Step 3: The Killer Demo (2 minutes) 🔥**

* **Driver:** *Turns off the computer's Wi-Fi (or turns on Airplane mode on screen).*
* **Speaker:** "To prove our data never leaves the device, we are now entirely offline. Let's ask Vitalis a question."
* **Driver:** *Types: "I have lower back pain, what should I do?" and hits send. The AI streams the text.*
* **Speaker:** "Notice the zero latency. This isn't an API call. This is an LLM running entirely in the browser using WebAssembly and WebGPU."

**Step 4: The 'One More Thing' (1 minute)**

* **Speaker:** "But health isn't just text. Because we process data locally, we integrated Multimodal capabilities without compromising privacy."
* **Driver:** *Clicks the Camera icon (Vision) or Voice icon.*
* **Speaker:** "We can run Vision models locally to estimate meal nutrition, and Voice models for hands-free workout coaching. Vitalis isn't just an app; it's a private health ecosystem."

---

## PART 3: The "Grill Session" (Anticipated Q&A)

Judges will test your technical depth. Memorize these answers.

**1. "Why didn't you just use an API like OpenAI or Claude? It's much easier."**

* **Your Answer:** "Privacy and latency. Health data is highly regulated and deeply personal. Routing it through a third-party API exposes users to data harvesting and leaks. By running inference locally via WebAssembly, we guarantee absolute zero-knowledge privacy. Plus, eliminating network round-trips gives us zero-latency responses and offline capabilities."

**2. "Won't downloading these AI models destroy the user's phone storage and battery?"**

* **Your Answer:** "It's a valid concern, which is why we engineered a hardware-adaptive approach. First, we use quantized (compressed) models like the Liquid 350M and SmolLM2 135M, which are incredibly lightweight. Second, they only download once into the browser's OPFS (Origin Private File System). Finally, our engine defaults to WebGPU to efficiently offload processing to the graphics chip, saving battery, but gracefully falls back to CPU on older devices."

**3. "If everything is offline, how do you update the app or the AI?"**

* **Your Answer:** "The UI and app logic update automatically through our Service Worker whenever the user reconnects to the internet. For the AI models, if we release a smarter version, the Model Manager will notify the user to initiate a new OPFS background download when they are on Wi-Fi."

**4. "What happens if the user clears their browser cache? Do they lose everything?"**

* **Your Answer:** "Currently, yes. Because we strictly enforce local data ownership, clearing device storage deletes the data. However, we proactively built a 'Data Export' feature so users can download their JSON history. In our future scope, we plan to implement peer-to-peer syncing or encrypted local file backups."

---

## PART 4: Navigating the "Mentorship" Phase

The second half of the call is the judges giving you feedback. **How you handle this determines if you move to the finals.**

* **Rule 1: NEVER ARGUE.** If a judge says, "I think your UI is confusing," do not defend it. Say: *"That is a fantastic point. We debated that internally, and getting your perspective validates that we need to streamline it. We will implement that for the final round."*
* **Rule 2: BE COACHABLE.** Judges advance teams who listen. They want to see that if they give you advice today, you will actually build it by tomorrow.
* **Rule 3: PIVOT TO FUTURE SCOPE.** If they point out a missing feature (e.g., "Why doesn't it connect to an Apple Watch?"), say: *"Exactly! That is Phase 2 of our architecture. We are currently exploring the Web Bluetooth API to pull live heart rate data locally without a cloud server."*

---

## PART 5: Your 24-Hour Action Plan (Divide & Conquer)

Stop coding new features immediately. A working app with 3 features scores 100x higher than a broken app with 10 features.

**Assign these roles right now:**

1. **The Driver (1 person):** Your job is the demo. Make sure the app is running flawlessly on your machine at `localhost:5173`. Make sure the LLM, Vision, and Voice models are fully downloaded in your browser. Practice turning off your Wi-Fi and running the app.
2. **The Architect (1 person):** Your job is the Q&A. Read Part 1 and Part 3 of this guide five times. You are the defender of the code. If they ask about WASM, WebGPU, or OPFS, you take the mic.
3. **The Visionary (1 person):** Your job is the opening and closing pitch. Practice delivering the 1-minute Hook. You need to sound passionate about data privacy and the future of edge computing.

You guys have built an incredibly complex, highly relevant piece of technology. Trust the architecture, stick to the script, and emphasize the privacy/offline superpowers. You are going to crush this evaluation!r
