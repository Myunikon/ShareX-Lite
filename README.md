<p align="center"><img src="https://getsharex.com/img/ShareX_Banner.png" alt="ShareX Banner"/></p>
<h1 align="center">ShareX-Lite</h1>
<h3 align="center">Lightweight, Offline-Focused Screen Capture & Productivity Tool</h3>
<br>
<p align="center">
  <a href="https://github.com/Myunikon/ShareX-Lite/actions/workflows/build.yml"><img src="https://img.shields.io/github/actions/workflow/status/Myunikon/ShareX-Lite/build.yml?branch=develop&label=Build&cacheSeconds=3600" alt="GitHub Workflow Status"/></a>
  <a href="./LICENSE.txt"><img src="https://img.shields.io/github/license/Myunikon/ShareX-Lite?label=License&color=brightgreen&cacheSeconds=3600" alt="License"/></a>
</p>
<br>

**ShareX-Lite** is a streamlined, lightweight fork of the open-source ShareX tool. It is optimized specifically for offline, local productivity. All uploading, online sharing, and external UI components have been removed to reduce bloat, protect privacy, and slash the final compiled folder footprint from **35MB+ down to ~5-7MB**.

---

## ⚡ What Makes it "Lite"?

*   **🔒 100% Offline (No Uploads)**: All file sharing, cloud uploading, URL shortening, and destination settings have been completely stripped from the UI and codebase. You can never accidentally upload a screenshot or file again.
*   **🚀 Snappy Editor (No Avalonia/SkiaSharp)**: Removed the heavy Modern Image Editor project along with its 30MB+ of dependencies (including SkiaSharp and Avalonia UI). It now defaults entirely to the snappy, instant-loading built-in legacy Windows Forms/GDI annotation editor.
*   **🌐 English-Only**: Removed over **1,740+** localized translation XML files (`*.*.resx`). This decreases source code size and prevents the compiler from generating dozens of culture-specific subfolders.
*   **🛠️ Release Optimizations**: Configured globally in `Directory.Build.props` with:
    *   `<PublishTrimmed>true</PublishTrimmed>`: Enabled partial IL trimming (tree-shaking) with root assembly preservation to safely trim unused base runtime code while keeping Windows Forms/WPF compatibility intact.
    *   `<InvariantGlobalization>true</InvariantGlobalization>`: Strips non-English runtime culture resources.
    *   `<DebugSymbols>false</DebugSymbols>`: Excludes debug symbol files (`.pdb`) from the build output.

---

## 🎨 Features Retained

Even with a massively reduced footprint, all core local capture and utility tools remain fully operational:

*   **Capture**: Region capture, screen capture, active window capture, scrolling screenshot.
*   **Record**: Screen recording (FFmpeg-based MP4 and GIF).
*   **Annotate**: Snappy, built-in drawing editor (shapes, arrows, text, step tool, blur, pixelate, crop, magnifier).
*   **OCR**: Snappy local text extraction (using Windows OCR API).
*   **Tools**: Color picker, screen color picker, screen ruler, pin-to-screen, QR code creator/reader.
*   **Automation**: Auto-save to local folder and copy to clipboard.

---

## 🛠️ How to Compile

You can compile **ShareX-Lite** using either **Visual Studio** or **GitHub Actions**:

### Build via GitHub Actions (Recommended)
1. Go to your fork on GitHub.
2. Go to the **Actions** tab and enable Actions for your repository.
3. Push any commit (or run the workflow manually if configured) to trigger the build.
4. Download the compiled portable `.zip` or setup installer from the finished run's **Artifacts** section.

### Build via Visual Studio
1. Open [ShareX.sln](file:///c:/Users/Nitro/Downloads/ShareX-Lite/ShareX.sln) in Visual Studio (2022 recommended).
2. Set the build configuration to **`Release`** and the platform to **`x64`** (or `ARM64`).
3. Build the solution (`Ctrl+Shift+B`).
4. Find your binaries in: `ShareX/bin/Release/net9.0-windows10.0.22621.0/ShareX.exe`.
