<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>Prompt Variation Web Tool</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <style>
    body {
      background: linear-gradient(to bottom, #e0ffe0, #f0fdf4);
      overflow: hidden;
    }
    .dollar {
      position: absolute;
      font-size: 24px;
      color: #4caf50;
      opacity: 0.6;
      animation: fall linear infinite;
      transition: transform 0.3s, opacity 0.3s;
    }
    .dollar:hover {
      transform: scale(1.4);
      opacity: 1;
      color: #2e7d32;
      text-shadow: 0 0 8px #4caf50;
    }
    @keyframes fall {
      0% { transform: translateY(-50px); }
      100% { transform: translateY(110vh); }
    }
  </style>
</head>
<body class="min-h-screen flex items-center justify-center p-6 relative">

  <!-- Falling Dollar Elements -->
  <script>
    const NUM_DOLLARS = 30;
    for (let i = 0; i < NUM_DOLLARS; i++) {
      const dollar = document.createElement('div');
      dollar.className = 'dollar';
      dollar.textContent = '$';
      dollar.style.left = Math.random() * 100 + 'vw';
      dollar.style.animationDuration = 5 + Math.random() * 10 + 's';
      dollar.style.fontSize = 16 + Math.random() * 24 + 'px';
      dollar.style.top = -Math.random() * 100 + 'px';
      document.body.appendChild(dollar);
    }
  </script>

  <div class="bg-white rounded-2xl shadow-2xl max-w-3xl w-full p-10 z-10 relative">
    <h2 class="text-3xl font-extrabold text-green-700 mb-4">🎨 Prompt Variation Assistant</h2>
    <p class="mb-4 text-gray-600 text-lg">Paste your image-to-prompt output below. Get creative, guided suggestions to make it unique for Adobe Stock!</p>
    <textarea id="promptInput" placeholder="Paste your image prompt here..." class="w-full h-36 p-4 border-2 border-green-300 rounded-xl text-gray-800 text-base focus:outline-none focus:ring-4 focus:ring-green-400"></textarea>
    <button onclick="showVariationGuide()" class="mt-5 bg-gradient-to-r from-green-500 to-green-600 text-white px-6 py-3 rounded-xl text-lg hover:scale-105 transition-transform duration-300">✨ Generate Variation Tips</button>

    <div id="output" class="hidden mt-10 p-6 bg-green-50 border-l-8 border-green-600 rounded-xl shadow-md">
      <h3 class="text-2xl font-bold text-green-700 mb-4">🔁 Prompt Variation Instructions</h3>
      <ul class="list-disc list-inside space-y-3 text-green-800 text-base">
        <li><strong>Stylistic twist:</strong> Add at least <em>two unique stylistic elements</em> (e.g., cinematic lighting, surreal color tones)</li>
        <li><strong>Emotional depth:</strong> Enrich the <em>subject’s emotion or pose</em> (e.g., joyful → introspective, active → dreamy)</li>
        <li><strong>Specific descriptors:</strong> Replace generic terms with <em>rich, vivid descriptions</em> (e.g., forest → pine sanctuary)</li>
        <li><strong>Camera variety:</strong> Use <em>diverse angles/lenses</em> (e.g., top-down drone shot, macro close-up)</li>
        <li><strong>Atmosphere:</strong> Inject <em>environmental mood</em> (e.g., misty twilight, golden hour rain)</li>
        <li><strong>Cultural flavor:</strong> Try <em>regional aesthetics</em> (e.g., Bengali monsoon, Nordic architecture)</li>
      </ul>
      <p class="mt-4 text-sm text-green-700 font-medium">📌 Final Tip: Don’t reuse phrasing. Rebuild the prompt with originality and tone!</p>
    </div>
  </div>

  <script>
    function showVariationGuide() {
      const input = document.getElementById("promptInput").value.trim();
      const outputBox = document.getElementById("output");
      if (input.length > 0) {
        outputBox.classList.remove("hidden");
        outputBox.scrollIntoView({ behavior: "smooth" });
      } else {
        alert("Please paste a prompt first.");
      }
    }
  </script>
</body>
</html>
