<div align="center">
  <img src="https://capsule-render.vercel.app/api?type=waving&color=0:8BE9FD,50:BD93F9,100:FF79C6&height=180&section=header&text=Kenneth&fontSize=60&fontColor=F8F8F2&animation=fadeIn&fontAlignY=35&desc=Software%20Engineer%20and%20Gameplay%20Systems%20Programmer&descAlignY=55&descSize=18" width="100%" alt="header" />
</div>

<div align="center">
  <a href="https://github.com/kads1024">
    <img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=600&size=22&duration=3200&pause=900&color=BD93F9&center=true&vCenter=true&width=680&lines=C%2B%2B+%2F+C%23+Software+Engineer;Gameplay%2C+Tools+%26+Engine+Programming;Unity+%E2%80%A2+Unreal+Engine+%E2%80%A2+Custom+C%2B%2B;Performance-minded%2C+systems-first+thinking" alt="Typing SVG" />
  </a>
</div>

<div align="center">
  <img src="https://komarev.com/ghpvc/?username=kads1024&label=Profile%20Views&color=BD93F9&style=flat-square" alt="profile views" />
  <img src="https://img.shields.io/badge/Based%20in-Philippines%20%F0%9F%87%B5%F0%9F%87%AD-6272A4?style=flat-square" alt="location" />
  <img src="https://img.shields.io/badge/Open%20to-Opportunities-50FA7B?style=flat-square" alt="open to work" />
</div>

---

## 👋 About Me

I'm a software engineer who builds **real-time, performance-sensitive systems**. Games are where I started to sharpened that skill set (tight frame budgets, cache-friendly data layouts, and manual memory management leave very little room to be sloppy), but the engineering underneath travels well beyond them.

I work primarily in **C++** and **C#**, across **Unity**, **Unreal Engine**, and hand-rolled codebases. I care about clean architecture, readable code that survives contact with a team, and profiling before optimizing.

```cpp
struct Engineer {
    std::string name     = "Kenneth";
    std::string role     = "Software Engineer";
    std::string location = "Philippines";

    std::vector<std::string> core      = { "C++", "C#", ".NET" };
    std::vector<std::string> engines   = { "Unity", "Unreal Engine" };
    std::vector<std::string> interests = { "Systems Design", "Graphics", "Tooling", "Optimization" };

    bool open_to_work() const noexcept { return true; }
};
```

### 🚀 Currently

- 🔭 Building &nbsp;→&nbsp; an unannounced title under NDA: real-time multiplayer systems work
- 🌱 Learning &nbsp;→&nbsp; graphics programming, multithreaded systems, engine internals, and advanced gameplay networking
- 🎯 Looking for &nbsp;→&nbsp; **gameplay, engine, tools, or software engineering roles** (remote-friendly)
- 💬 Ask me about &nbsp;→&nbsp; ECS, gameplay architecture, editor tooling, or shipping under a frame budget

---

## 🎮 Selected Work

<!-- =====================================================================
     TODO — THIS IS THE MOST IMPORTANT SECTION ON THE PAGE.
     A hiring manager decides here. Rules:
       1. Add a GIF for each. Motion beats text every single time.
       2. Lead with the ENGINEERING problem, not the genre or story.
       3. Quantify results wherever you honestly can (ms, MB, FPS, %, players).
       4. Three excellent entries beat six mediocre ones. Delete the rest.
     Put GIFs in assets/projects/ and keep each under ~5MB so they load fast.
     ===================================================================== -->

<table>
<tr>
<td width="50%" valign="top">

### 🔹 [Real-Time Raycaster (C++ / SDL3)](https://github.com/kads1024/mini-raycaster)

<img src="./assets/projects/raycaster.gif" width="100%" alt="Raycaster demo: a textured maze rendered in first person beside a top-down map, the camera turning a full circle while the ray fan sweeps across the map" />

**Problem**: Move from offline renders that take their time to something that has to hold a frame budget and answer to input.<br />
**Built**: ~550-line real-time raycaster in C++ on SDL3. Ray-marched textured walls, billboard sprites, and a per-pixel depth buffer, with the top-down map drawn beside the first-person view so the ray fan is visible as it sweeps.<br />
**Result**: Interactive movement through a textured maze at 1024×512, sprites correctly occluded by walls and by each other with no depth sorting anywhere in the pipeline.<br />
**Notable**: Sprites kept vanishing behind walls they were standing in front of. The depth buffer was a reused 32-bit colour buffer, so every distance silently truncated to whole grid cells (a wall at 3.97 units tested as 3). Storing depth as float fixed it, and the bug only ever surfaced when a sprite shared a cell with the wall behind it.

`C++` &nbsp;`SDL3` &nbsp;`Real-Time Rendering`

<a href="https://github.com/kads1024/mini-raycaster">Code</a> · <a href="https://kads1024.github.io/devlog/raycasting-a-maze-in-real-time"><b>Devlog</b></a>

</td>
<td width="50%" valign="top">

### 🔹 [CHIP-8 Emulator (C++17 / SDL3)](https://github.com/kads1024/emulator-chip8)

<img src="./assets/projects/chip8.gif" width="100%" alt="CHIP-8 emulator demo: Tetris running at full speed on an emulated 64x32 monochrome display" />

**Problem**: Build something whose correctness I *cannot see*. A subtly wrong renderer looks wrong; a subtly wrong CPU still plays Tetris.<br />
**Built**: A CHIP-8 virtual machine in C++17 — 4 KB address space, 16 registers, 34 instructions dispatched through five function-pointer tables — plus an SDL3 layer that uploads the framebuffer as one streaming texture. The machine core has zero dependency on SDL, so every measurement below came from a 12-line headless harness.<br />
**Result**: Scores 18/18 on the standard opcode conformance ROM and runs commercial-era ROMs at full speed.<br />
**Notable**: Neither of those facts proves much. I instrumented *which handlers actually execute*: **6 of 34 never ran once** across the conformance ROM and 200,000 cycles of gameplay — and one of the six was flatly wrong, dereferencing its operand instead of using it. Four bytes of hand-written ROM turn it into a segfault by chaining two more latent bugs. Found by asking "what did it run", not "does it pass".

`C++` &nbsp;`SDL3` &nbsp;`Emulation` &nbsp;`Systems`

<a href="https://github.com/kads1024/emulator-chip8">Code</a> · <a href="https://kads1024.github.io/devlog/emulating-a-cpu-that-never-existed"><b>Devlog</b></a>

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🔹 [CPU Raytracer (C++20)](https://github.com/kads1024/mini-raytracer)

<img src="./assets/projects/raytracer.png" width="100%" alt="Raytracer render: four spheres with reflection and refraction over a checkerboard plane" />

**Problem**: Understand raytracing well enough to derive it, not just make it compile.<br />
**Built**: ~350-line CPU raytracer in C++20, no third-party libraries, on a templated N-dimensional vector library built with concepts.<br />
**Result**: Diffuse and specular shading, hard shadows, recursive reflection and refraction at 1024×768.<br />
**Notable**: Refraction derived from vector decomposition rather than copied, so total internal reflection emerges from the math instead of being special-cased.

`C++`

<a href="https://github.com/kads1024/mini-raytracer">Code</a> · <a href="https://kads1024.github.io/devlog/building-a-cpu-raytracer-from-scratch-in-c++20"><b>Devlog</b></a>

</td>
<td width="50%" valign="top">

### 🎨 More Work

A fourth deep dive — a **[procedural explosion raymarcher](https://github.com/kads1024/mini-raymarcher)** reconstructed line by line from ssloy's tinykaboom — is written up in full: <a href="https://kads1024.github.io/devlog/rendering-an-explosion-with-one-function">Rendering an Explosion with One Function</a>.

Playable builds, jam entries, and prototypes live on itch.io — several are downloadable and take under a minute to try.

<a href="https://kennysans37.itch.io">
  <img src="https://img.shields.io/badge/Browse%20playable%20builds-FA5C5C?style=for-the-badge&logo=itchdotio&logoColor=white" alt="itch.io" />
</a>

<br /><br />

Full case studies with breakdowns of the systems behind each project:

<a href="https://portfolio-wizard-theta.vercel.app/">
  <img src="https://img.shields.io/badge/Read%20the%20case%20studies-BD93F9?style=for-the-badge&logo=aboutdotme&logoColor=white" alt="Portfolio" />
</a>

</td>
</tr>
</table>

---

## 🛠️ Tech Stack

**Languages**

<p>
  <img src="https://img.shields.io/badge/C%2B%2B-00599C?style=for-the-badge&logo=cplusplus&logoColor=white" alt="C++" />
  <img src="https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=csharp&logoColor=white" alt="C#" />
  <img src="https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black" alt="C" />
  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python" />
  <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black" alt="JavaScript" />
  <img src="https://img.shields.io/badge/HLSL%20%2F%20GLSL-5586A4?style=for-the-badge&logo=opengl&logoColor=white" alt="Shaders" />
  <img src="https://img.shields.io/badge/SQL-4479A1?style=for-the-badge&logo=postgresql&logoColor=white" alt="SQL" />
</p>

**Engines & Frameworks**

<p>
  <img src="https://img.shields.io/badge/Unity-000000?style=for-the-badge&logo=unity&logoColor=white" alt="Unity" />
  <img src="https://img.shields.io/badge/Unreal%20Engine-0E1128?style=for-the-badge&logo=unrealengine&logoColor=white" alt="Unreal Engine" />
  <img src="https://img.shields.io/badge/.NET-512BD4?style=for-the-badge&logo=dotnet&logoColor=white" alt=".NET" />
  <img src="https://img.shields.io/badge/OpenGL-5586A4?style=for-the-badge&logo=opengl&logoColor=white" alt="OpenGL" />
  <img src="https://img.shields.io/badge/Vulkan-AE0F28?style=for-the-badge&logo=opengl&logoColor=white" alt="Vulkan" />
  <img src="https://img.shields.io/badge/SDL-1D1D1D?style=for-the-badge&logo=libsdl&logoColor=white" alt="SDL" />
</p>

**Tools & Workflow**

<p>
  <img src="https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git" />
  <img src="https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" alt="GitHub Actions" />
  <img src="https://img.shields.io/badge/Visual%20Studio-5C2D91?style=for-the-badge&logo=visualstudio&logoColor=white" alt="Visual Studio" />
  <img src="https://img.shields.io/badge/Rider-000000?style=for-the-badge&logo=rider&logoColor=white" alt="Rider" />
  <img src="https://img.shields.io/badge/CMake-064F8C?style=for-the-badge&logo=cmake&logoColor=white" alt="CMake" />
  <img src="https://img.shields.io/badge/Perforce-404040?style=for-the-badge&logo=perforce&logoColor=white" alt="Perforce" />
  <img src="https://img.shields.io/badge/Blender-E87D0D?style=for-the-badge&logo=blender&logoColor=white" alt="Blender" />
</p>

---

## 🧠 Engineering Focus

| Area | What that means in practice |
|:--|:--|
| **Systems Architecture** | Component/ECS design, decoupled subsystems, data-oriented layouts that scale past the prototype |
| **Performance** | Profile first, then fix: allocation churn, cache misses, draw calls, GC pressure |
| **Gameplay Networking** | Client prediction, server reconciliation, state replication, lag compensation |
| **Tooling** | Custom editors and inspectors, build automation, pipelines that save the team hours |
| **Low-Level C++** | RAII, move semantics, smart pointers, templates — and knowing when *not* to reach for them |
| **Cross-Discipline** | Turning design intent into maintainable systems, shipping alongside artists and designers |

---

## 📊 GitHub Activity

<div align="center">
  <img src="https://github-readme-stats-omega-jet-44.vercel.app/api?username=kads1024&show_icons=true&include_all_commits=true&count_private=true&hide_border=true&theme=dracula&bg_color=00000000&title_color=BD93F9&icon_color=FF79C6&text_color=F8F8F2&rank_icon=github" height="165" alt="GitHub stats" />
  <img src="https://github-readme-stats-omega-jet-44.vercel.app/api/top-langs?username=kads1024&layout=compact&langs_count=8&card_width=320&hide_border=true&theme=dracula&bg_color=00000000&title_color=BD93F9&text_color=F8F8F2" height="165" alt="Top languages" />
</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/kads1024/kads1024/output/snake.svg" alt="Snake animation eating my contributions" width="100%" />
</div>

---

## 🤝 Let's Connect

I'm open to conversations about gameplay, engine, tools, and backend roles — and I answer every message.

<div align="center">
  <a href="https://www.linkedin.com/in/ken-santos/">
    <img src="https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white" alt="LinkedIn" />
  </a>
  <a href="https://portfolio-wizard-theta.vercel.app/">
    <img src="https://img.shields.io/badge/Portfolio-BD93F9?style=for-the-badge&logo=aboutdotme&logoColor=white" alt="Portfolio" />
  </a>
  <a href="https://kennysans37.itch.io">
    <img src="https://img.shields.io/badge/itch.io-FA5C5C?style=for-the-badge&logo=itchdotio&logoColor=white" alt="itch.io" />
  </a>
  <a href="mailto:kennethamiel.santos@gmail.com">
    <img src="https://img.shields.io/badge/Email-EA4335?style=for-the-badge&logo=gmail&logoColor=white" alt="Email" />
  </a>
</div>

<br />

<div align="center">
  <i>Open to full-time, contract, and collaborative work — in games and well beyond them.</i>
</div>

<div align="center">
  <img src="./assets/footer.svg" width="100%" alt="" />
</div>