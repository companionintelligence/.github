<div align="center">

# Companion Intelligence

**Open-source tools for private, local-first AI companions.**

[Website](https://ci.computer) · [Documentation](https://docs.ci.computer) · [Marketplace](https://hub.ci.computer/store) · [All public repositories](https://github.com/orgs/companionintelligence/repositories?type=public)

💫🔭💡📡✨🏠⚡🖥️🌟📥🤝📦🔓📖

</div>

Build and run apps and agents on hardware you own. Companion Memory provides a local personal data and memory layer; Companion Hub manages local apps and agents, with Companion OS as a Linux base. The projects below extend that system with capture, device integrations, spatial interfaces, and developer tools.

## How the public projects fit together

This map summarizes the connections described by the public projects: capture and devices can feed local memory; agents and spatial apps use or present local data; Hub runs local services and apps; supporting tools package, distribute, and build them. Standalone projects are included in their ecosystem group.

```mermaid
flowchart LR
    subgraph Base["Local platform"]
        OS["CI-OS"] --> HUB["Companion-Hub"]
        HUB <--> MEM["Companion-Memory"]
        STORE["Marketplace store"] -. "app catalog" .-> HUB
    end

    subgraph Capture["Capture and memory integrations"]
        BROWSER["CI-Browser-Extension"]
        DESKTOP["CI-Capture"]
        SYNC["CI-Agent-Sync"]
        HERMES["CI-Hermes"]
        OPENCLAW["CI-OpenClaw"]
        PLANNING["CI-Planning"]
        ATLAS["CI-Spatial-Atlas"]
    end
    BROWSER -->|"browser context"| MEM
    DESKTOP -->|"desktop activity"| MEM
    HERMES <-->|"API / MCP"| MEM
    OPENCLAW <-->|"MCP"| MEM
    PLANNING <-->|"MCP tools"| HERMES
    SYNC -. "agent configuration" .-> HERMES
    SYNC -.-> OPENCLAW
    MEM -->|"located memories"| ATLAS

    subgraph Devices["Devices and voice"]
        OMI["CI-OMI"]
        MENTRA["CI-Mentra"]
        EVEN["CI-Even-Realities"]
        PEBBLE["CI-Pebble"]
        VOICE["CI-Home-Assistant-Voice-PE"]
        MAIX["CI-MaixCAM"]
    end
    OMI -->|"wearable capture"| MEM
    MAIX -->|"edge vision capture"| MEM
    MEM -->|"alerts and triggers"| PEBBLE
    MENTRA -. "agent interface" .-> HERMES
    EVEN -. "agent interface" .-> OPENCLAW
    VOICE <-->|"local voice / assistant"| HUB

    subgraph Spatial["Spatial and XR"]
        SPATIAL["Companion Spatial"]
        SCAN["CI-Spatial-Unity"]
        META_SCAN["CI-Spatial-Web-Meta"]
        AGENT_U["CI-Spatial-Agent-Unity"]
        AGENT_WEB["CI-Spatial-Agent-Web"]
        PHOTO["CI-Spatial-Photo"]
        HOME["CI-Virtual-Home"]
        METAHUMAN["CI-MetaHuman"]
    end
    SCAN -->|"spatial export"| MEM
    META_SCAN -->|"scan assets"| AGENT_U
    SPATIAL -->|"room scan"| AGENT_WEB
    AGENT_U -. "spatial agent surface" .-> MEM
    AGENT_WEB -.-> MEM
    MEM -->|"3D memory views"| PHOTO
    MEM -->|"4D memory map"| ATLAS
    HUB -. "local app runtime" .-> HOME
    HUB -.-> METAHUMAN

    subgraph Community["Community projects and experiments"]
        SPELLBOOK["CI-Spellbook"]
        JIC["JustInCase"]
        BENCH["Local-Bench"]
        INFERENCE["CI-Active-Inference"]
        TOROLLO["Torollo"]
        SYSINFO["systeminformation fork"]
    end
    SPELLBOOK -. "discover projects" .-> HUB
    SYSINFO -. "system information" .-> HUB
    MODELS["Local models"] --> HUB
    BENCH -->|"benchmark"| MODELS
    JIC -. "offline guidance" .-> MODELS
    INFERENCE -. "agent experiment" .-> MEM

    subgraph Tooling["Build and distribution"]
        CICD["CI-Local-CICD"]
        BUILDER["CI-Static-Containter-Builder"]
        CACHE["CI-Tools-Cache-Mounts"]
        GONO["CI-GonoPBX"]
        BREW["homebrew-tap"]
        SCOOP["scoop-bucket"]
    end
    CICD -->|"local checks"| BUILDER
    CACHE -. "shared build caches" .-> CICD
    BUILDER -->|"container images"| STORE
    GONO -->|"published images"| STORE
    BREW -->|"desktop releases"| HUB
    SCOOP -->|"desktop releases"| HUB

    classDef core fill:#0f717a,stroke:#0b565c,color:#fff
    class OS,HUB,MEM,STORE core
```

## 🗯️ Platform

<table>
<thead>
<tr><th>Project</th><th>What it does</th></tr>
</thead>
<tbody>
<tr><td><a href="https://github.com/companionintelligence/CI-OS"><img src="https://raw.githubusercontent.com/companionintelligence/CI-OS/main/core/headless/payload/usr/share/icons/hicolor/scalable/apps/ci-os-logo.svg" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-OS"><strong>Companion OS</strong></a></td><td>Linux distribution for AI companions and development.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/Companion-Hub"><img src="https://raw.githubusercontent.com/companionintelligence/Companion-Hub/dev/packages/frontend/hub-brand/logos/app-icon.svg" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/Companion-Hub"><strong>Companion Hub</strong></a></td><td>Install and manage self-hosted apps, local models, and agents.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/Companion-Memory"><img src="https://raw.githubusercontent.com/companionintelligence/Companion-Memory/main/frontend/apps/desktop/src-tauri/icons/icon.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/Companion-Memory"><strong>Companion Memory</strong></a></td><td>Personal database and memory engine for Companion Intelligence.</td></tr>
</tbody>
</table>

## 🔌 Memory apps and integrations

<table>
<thead>
<tr><th>Project</th><th>What it does</th></tr>
</thead>
<tbody>
<tr><td>🤖 <a href="https://github.com/companionintelligence/CI-Agent-Sync"><strong>Agent Sync</strong></a></td><td>Versionable agent configuration templates and setup notes.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Capture"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Capture/main/assets/logo.svg" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Capture"><strong>Companion Capture</strong></a></td><td>Desktop capture for macOS, Windows, and Linux.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Browser-Extension"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Browser-Extension/master/store-assets/safari/app-icon-1024.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Browser-Extension"><strong>Browser Extension</strong></a></td><td>Capture browsing context from supported browsers.</td></tr>
<tr><td>🔭 <a href="https://github.com/companionintelligence/CI-Spatial-Atlas"><strong>Companion Atlas</strong></a></td><td>Turn images and video into a time-aware 3D scrapbook map.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Planning"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Planning/main/client/public/icon-512.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Planning"><strong>Companion Planning</strong></a></td><td>Local-first, MCP-native personal planning app.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-OpenClaw"><img src="https://raw.githubusercontent.com/companionintelligence/CI-OpenClaw/master/logo.webp" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-OpenClaw"><strong>Companion OpenClaw</strong></a></td><td>OpenClaw Docker image for Companion Hub.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Hermes"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Hermes/master/logo.webp" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Hermes"><strong>Companion Hermes</strong></a></td><td>Hermes agent with Companion Memory integration.</td></tr>
</tbody>
</table>

## 📱 Devices, voice, and wearables

<table>
<thead>
<tr><th>Project</th><th>What it does</th></tr>
</thead>
<tbody>
<tr><td><a href="https://github.com/companionintelligence/CI-Home-Assistant-Voice-PE"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Home-Assistant-Voice-PE/main/web/public/icon.svg" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Home-Assistant-Voice-PE"><strong>Home Assistant</strong></a></td><td>Voice integration for Home Assistant with Memory and Hub.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Even-Realities"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Even-Realities/main/ci-glasses-app/public/icon.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Even-Realities"><strong>Even Realities</strong></a></td><td>Companion integration for Even Realities G2 glasses.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Mentra"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Mentra/main/site/public/icon.svg" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Mentra"><strong>Mentra</strong></a></td><td>Live app for Mentra smart glasses.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Pebble"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Pebble/main/assets/appstore/icon/icon-512.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Pebble"><strong>Pebble</strong></a></td><td>Pebble watch interface for memory and local models.</td></tr>
<tr><td>📷 <a href="https://github.com/companionintelligence/CI-MaixCAM"><strong>MaixCAM</strong></a></td><td>Companion projects for Sipeed MaixCAM devices.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-OMI"><img src="https://raw.githubusercontent.com/companionintelligence/CI-OMI/main/sdks/react-native/example/assets/icon.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-OMI"><strong>OMI</strong></a></td><td>Omi wearable integration experiments.</td></tr>
</tbody>
</table>

## 🌐 Spatial, XR, and virtual worlds

<table>
<thead>
<tr><th>Project</th><th>What it does</th></tr>
</thead>
<tbody>
<tr><td><a href="https://github.com/companionintelligence/CI-Spatial"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Spatial/main/public/icon-512.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Spatial"><strong>Companion Spatial</strong></a></td><td>Web-based room scanning.</td></tr>
<tr><td>🥽 <a href="https://github.com/companionintelligence/CI-Spatial-Unity"><strong>Companion Scan</strong></a></td><td>Quest and WebXR room scanning with local computer vision.</td></tr>
<tr><td>🧭 <a href="https://github.com/companionintelligence/CI-Spatial-Web-Meta"><strong>Spatial Web Meta</strong></a></td><td>Quest 3 room mapping with a local vision server.</td></tr>
<tr><td>🤖 <a href="https://github.com/companionintelligence/CI-Spatial-Agent-Unity"><strong>Spatial Agent for Unity</strong></a></td><td>Mixed-reality companion for Quest and Pico.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Spatial-Agent-Web"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Spatial-Agent-Web/main/marketplace/ci-spatial-companion-webxr/metadata/logo.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Spatial-Agent-Web"><strong>Spatial Agent for Web</strong></a></td><td>Embodied agent framework for WebXR and WebSpatial.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Spatial-Photo"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Spatial-Photo/main/assets/icon.svg" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Spatial-Photo"><strong>Photo Time Machine</strong></a></td><td>Explore photos and video as 3D memories.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-Virtual-Home"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Virtual-Home/main/portal/icons/icon-512.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Virtual-Home"><strong>Virtual Home</strong></a></td><td>Turn house specifications into explorable 3D worlds.</td></tr>
<tr><td>🤖 <a href="https://github.com/companionintelligence/CI-MetaHuman"><strong>Companion MetaHuman</strong></a></td><td>Locally hosted, embodied companion built with Unreal Engine.</td></tr>
</tbody>
</table>

## 🧪 Community projects and experiments

<table>
<thead>
<tr><th>Project</th><th>What it does</th></tr>
</thead>
<tbody>
<tr><td><a href="https://github.com/companionintelligence/CI-Spellbook"><img src="https://raw.githubusercontent.com/companionintelligence/CI-Spellbook/main/public/logo/icon-512.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-Spellbook"><strong>Spellbook</strong></a></td><td>Curated directory of agents, apps, and tools.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/JustInCase"><img src="https://raw.githubusercontent.com/companionintelligence/JustInCase/main/public/assets/logo.svg" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/JustInCase"><strong>Just In Case</strong></a></td><td>Offline emergency knowledge search.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/Local-Bench"><img src="https://raw.githubusercontent.com/companionintelligence/Local-Bench/main/video/assets/app-icon.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/Local-Bench"><strong>Local Bench</strong></a></td><td>Benchmark local LLM token-generation speed.</td></tr>
<tr><td>🤖 <a href="https://github.com/companionintelligence/CI-Active-Inference"><strong>Active Inference</strong></a></td><td>Experimental active-inference agent.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/Torollo"><img src="https://raw.githubusercontent.com/companionintelligence/Torollo/main/frontend/src/assets/logo.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/Torollo"><strong>Torollo</strong></a></td><td>Local visual playground for system design and networking.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/systeminformation"><img src="https://raw.githubusercontent.com/companionintelligence/systeminformation/master/docs/assets/logo.png" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/systeminformation"><strong>systeminformation fork</strong></a></td><td>Companion Intelligence fork of the Node.js system information library.</td></tr>
</tbody>
</table>

## 🛠️ Developer tools and distribution

<table>
<thead>
<tr><th>Project</th><th>What it does</th></tr>
</thead>
<tbody>
<tr><td>🔁 <a href="https://github.com/companionintelligence/CI-Local-CICD"><strong>Local CI/CD</strong></a></td><td>Audit and run repository checks on local hardware.</td></tr>
<tr><td>🧱 <a href="https://github.com/companionintelligence/CI-Static-Containter-Builder"><strong>Static Container Builder</strong></a></td><td>Package static web apps as self-contained Docker images.</td></tr>
<tr><td>💾 <a href="https://github.com/companionintelligence/CI-Tools-Cache-Mounts"><strong>Cache Mounts</strong></a></td><td>Mount shared NFS caches on macOS and Linux.</td></tr>
<tr><td><a href="https://github.com/companionintelligence/CI-GonoPBX"><img src="https://raw.githubusercontent.com/companionintelligence/CI-GonoPBX/main/docs/assets/icon.svg" alt="" width="24" height="24" /></a> <a href="https://github.com/companionintelligence/CI-GonoPBX"><strong>GonoPBX images</strong></a></td><td>Build and publish GonoPBX images for the marketplace.</td></tr>
<tr><td>🍺 <a href="https://github.com/companionintelligence/homebrew-tap"><strong>Homebrew tap</strong></a></td><td>Desktop app distribution.</td></tr>
<tr><td>🪣 <a href="https://github.com/companionintelligence/scoop-bucket"><strong>Scoop bucket</strong></a></td><td>Desktop app distribution.</td></tr>
</tbody>
</table>
