---
title: "About Me"
layout: posts
permalink: /about/
author_profile: true
classes: wide
---
I am a Ph.D. candidate in Statistical Science at Duke University. My research is at the intersection of reinforcement learning, large language models, and Bayesian inference. I aim to build learning systems that are statistically grounded, stable to optimize, and useful in real decision making settings.

Recently, I worked on reinforcement learning for frontier LLMs at Apple Foundation Models and safe LLM fine tuning at AWS GenAI. My academic work spans stable average reward reinforcement learning, robust policy optimization, personalized LLMs, efficient variational inference, and uncertainty aware scientific modeling.

Before Duke, I earned an M.A. in Statistics and Data Science and dual degrees in Industrial Engineering and Applied Statistics from Yonsei University, graduating first in my class. I enjoy working across theory, systems, and applications, including robotics, logistics, materials science, and environmental monitoring.

Please visit **Research & Presentation** and **Projects** to learn more. For my complete CV:

<div id="cv-document" class="cv-document" role="region" aria-label="Dongkyu Derek Cho CV" tabindex="0">
  <div class="cv-pages">
    <img src="/assets/pdf/cv-preview-1.png" alt="Dongkyu Derek Cho CV, page 1" />
    <img src="/assets/pdf/cv-preview-2.png" alt="Dongkyu Derek Cho CV, page 2" loading="lazy" />
  </div>
</div>
<script type="module">
  const viewer = document.querySelector('#cv-document .cv-pages');
  try {
    const pdfjs = await import('https://cdn.jsdelivr.net/npm/pdfjs-dist@6.5.438/build/pdf.min.mjs');
    pdfjs.GlobalWorkerOptions.workerSrc = 'https://cdn.jsdelivr.net/npm/pdfjs-dist@6.5.438/build/pdf.worker.min.mjs';
    const pdf = await pdfjs.getDocument({ url: '/assets/pdf/Derek_Cho_2026_RL_RESUME.pdf' }).promise;
    const pages = document.createDocumentFragment();
    for (let number = 1; number <= pdf.numPages; number++) {
      const page = await pdf.getPage(number);
      const viewport = page.getViewport({ scale: 2 });
      const canvas = document.createElement('canvas');
      canvas.width = viewport.width;
      canvas.height = viewport.height;
      canvas.setAttribute('role', 'img');
      canvas.setAttribute('aria-label', `Dongkyu Derek Cho CV, page ${number}`);
      await page.render({ canvasContext: canvas.getContext('2d'), viewport }).promise;
      pages.append(canvas);
    }
    viewer.replaceChildren(pages);
  } catch {
    // The supplied PDF's page previews stay visible if the renderer is unavailable.
  }
</script>
