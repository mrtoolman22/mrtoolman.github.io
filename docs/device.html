<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>🕵️ Full Browser Fingerprint Test</title>
  <style>
    body { font-family: monospace; background: #111; color: #0f0; padding: 20px; }
    h1 { color: #0ff; }
    pre { white-space: pre-wrap; word-wrap: break-word; }
  </style>
</head>
<body>
  <h1>🕵️ Browser & Device Fingerprint</h1>
  <pre id="info">Collecting...</pre>

  <script>
    async function getFingerprint() {
      // WebGL Renderer
      const canvas = document.createElement("canvas");
      const gl = canvas.getContext("webgl") || canvas.getContext("experimental-webgl");
      let gpu = "Unavailable";
      if (gl) {
        const dbg = gl.getExtension("WEBGL_debug_renderer_info");
        gpu = dbg ? gl.getParameter(dbg.UNMASKED_RENDERER_WEBGL) : "Hidden";
      }

      // Canvas Fingerprint
      const ctx = canvas.getContext("2d");
      let canvasFp = "Unavailable";

      if (ctx) {
        ctx.textBaseline = "top";
        ctx.font = "16px Arial";
        ctx.fillStyle = "#f60";
        ctx.fillRect(0, 0, 100, 30);
        ctx.fillStyle = "#069";
        ctx.fillText("CANVAS-FP-TEST", 2, 2);
        canvasFp = canvas.toDataURL();
      }

      // Audio Fingerprint
      let audioFp = "Unavailable";
      try {
        const ctxAudio = new (window.OfflineAudioContext || window.webkitOfflineAudioContext)(1, 44100, 44100);
        const osc = ctxAudio.createOscillator();
        const comp = ctxAudio.createDynamicsCompressor();
        osc.type = "triangle";
        osc.frequency.setValueAtTime(10000, ctxAudio.currentTime);
        osc.connect(comp);
        comp.connect(ctxAudio.destination);
        osc.start(0);
        ctxAudio.startRendering();
        const rendered = await new Promise(res => {
          ctxAudio.oncomplete = (e) => res(e.renderedBuffer.getChannelData(0).slice(4500, 5000));
        });
        audioFp = rendered.reduce((acc, val) => acc + Math.abs(val), 0).toFixed(4);
      } catch (e) {}

      // Battery Info
      let batteryInfo = "Not supported";
      try {
        const battery = await navigator.getBattery();
        batteryInfo = {
          charging: battery.charging,
          level: battery.level,
          chargingTime: battery.chargingTime,
          dischargingTime: battery.dischargingTime,
        };
      } catch (e) {}

      const info = {
        // Device/Browser
        userAgent: navigator.userAgent,
        platform: navigator.platform,
        language: navigator.language,
        languages: navigator.languages,
        cookiesEnabled: navigator.cookieEnabled,
        online: navigator.onLine,
        maxTouchPoints: navigator.maxTouchPoints,
        hardwareConcurrency: navigator.hardwareConcurrency,
        deviceMemory: navigator.deviceMemory || "Unavailable",
        serviceWorker: "serviceWorker" in navigator,
        clipboard: "clipboard" in navigator,
        doNotTrack: navigator.doNotTrack,

        // Time
        timezone: Intl.DateTimeFormat().resolvedOptions().timeZone,
        timezoneOffset: new Date().getTimezoneOffset(),

        // Screen
        screenResolution: `${screen.width} x ${screen.height}`,
        colorDepth: screen.colorDepth,
        pixelRatio: window.devicePixelRatio,
        windowSize: `${window.innerWidth} x ${window.innerHeight}`,

        // GPU/WebGL
        webglRenderer: gpu,

        // Canvas Fingerprint
        canvasFingerprint: canvasFp,

        // Audio Fingerprint
        audioFingerprint: audioFp,

        // Battery
        battery: batteryInfo,

        // Network
        connection: navigator.connection ? {
          downlink: navigator.connection.downlink,
          effectiveType: navigator.connection.effectiveType,
          rtt: navigator.connection.rtt,
          saveData: navigator.connection.saveData
        } : "Not available",

        // Feature Detection
        features: {
          geolocation: "geolocation" in navigator,
          notification: "Notification" in window,
          localStorage: "localStorage" in window,
          sessionStorage: "sessionStorage" in window,
          indexedDB: "indexedDB" in window,
          webRTC: "RTCPeerConnection" in window
        }
      };

      document.getElementById("info").textContent = JSON.stringify(info, null, 2);
    }

    getFingerprint();
  </script>
</body>
</html>
