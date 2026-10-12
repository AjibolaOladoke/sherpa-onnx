# sherpa-onnx

## What This Is

A practical reference entry for product and engineering: the sherpa-onnx notes, examples and fixes we reach for repeatedly. Kept current as part of the wider Swift Tech Co. engineering library.

## Images

[![sherpa-onnx](images/preview.png)](https://github.com/Swift-Tech-Co/sherpa-onnx)

## Introduction

This repository supports running the following functions **locally**

  - Speech-to-text (i.e., ASR); both streaming and non-streaming are supported
  - Text-to-speech (i.e., TTS)
  - Speaker diarization
  - Speaker identification
  - Speaker verification
  - Spoken language identification
  - Audio tagging
  - VAD (e.g., [silero-vad][silero-vad])
  - Speech enhancement (e.g., [gtcrn][gtcrn], DPDFNet)
  - Keyword spotting
  - Source separation (e.g., [spleeter][spleeter], [UVR][UVR])

on the following platforms and operating systems:

  - x86, ``x86_64``, 32-bit ARM, 64-bit ARM (arm64, aarch64), RISC-V (riscv64), **RK NPU**, **Ascend NPU**
  - Linux, macOS, Windows, openKylin
  - Android, WearOS
  - iOS
  - HarmonyOS
  - NodeJS
  - WebAssembly
  - [NVIDIA Jetson Orin NX][NVIDIA Jetson Orin NX] (Support running on both CPU and GPU)
  - [NVIDIA Jetson Nano B01][NVIDIA Jetson Nano B01] (Support running on both CPU and GPU)
  - [Raspberry Pi][Raspberry Pi]
  - [RV1126][RV1126]
  - [LicheePi4A][LicheePi4A]
  - [VisionFive 2][VisionFive 2]
  - [旭日X3派][旭日X3派]
  - [爱芯派][爱芯派]
  - [RK3588][RK3588]
  - [SpacemiT-K1][SpacemiT-K1]
  - [SpacemiT-K3][SpacemiT-K3]
  - etc

with the following APIs

  - C++, C, Python, Go, ``C#``
  - Java, Kotlin, JavaScript
  - Swift, Rust
  - Dart, Object Pascal

### Links for Huggingface Spaces

<details>
<summary>You can visit the following Huggingface spaces to try sherpa-onnx without
installing anything. All you need is a browser.</summary>

| Description                                           | URL                                     | 中国镜像                               |
|-------------------------------------------------------|-----------------------------------------|----------------------------------------|
| Speaker diarization                                   | [Click me][hf-space-speaker-diarization]| [镜像][hf-space-speaker-diarization-cn]|
| Speech recognition                                    | [Click me][hf-space-asr]                | [镜像][hf-space-asr-cn]                |
| Speech recognition with [Whisper][Whisper]            | [Click me][hf-space-asr-whisper]        | [镜像][hf-space-asr-whisper-cn]        |
| Speech synthesis                                      | [Click me][hf-space-tts]                | [镜像][hf-space-tts-cn]                |
| Generate subtitles                                    | [Click me][hf-space-subtitle]           | [镜像][hf-space-subtitle-cn]           |
| Audio tagging                                         | [Click me][hf-space-audio-tagging]      | [镜像][hf-space-audio-tagging-cn]      |
| Source separation                                     | [Click me][hf-space-source-separation]  | [镜像][hf-space-source-separation-cn]  |
| Spoken language identification with [Whisper][Whisper]| [Click me][hf-space-slid-whisper]       | [镜像][hf-space-slid-whisper-cn]       |

We also have spaces built using WebAssembly. They are listed below:

| Description                                                                              | Huggingface space| ModelScope space|
|------------------------------------------------------------------------------------------|------------------|-----------------|
|Voice activity detection with [silero-vad][silero-vad]                                    | [Click me][wasm-hf-vad]|[地址][wasm-ms-vad]|
|Real-time speech recognition (Chinese + English) with Zipformer                           | [Click me][wasm-hf-streaming-asr-zh-en-zipformer]|[地址][wasm-hf-streaming-asr-zh-en-zipformer]|
|Real-time speech recognition (Chinese + English) with Paraformer                          |[Click me][wasm-hf-streaming-asr-zh-en-paraformer]| [地址][wasm-ms-streaming-asr-zh-en-paraformer]|
|Real-time speech recognition (Chinese + English + Cantonese) with [Paraformer-large][Paraformer-large]|[Click me][wasm-hf-streaming-asr-zh-en-yue-paraformer]| [地址][wasm-ms-streaming-asr-zh-en-yue-paraformer]|
|Real-time speech recognition (English) |[Click me][wasm-hf-streaming-asr-en-zipformer]    |[地址][wasm-ms-streaming-asr-en-zipformer]|
|VAD + speech recognition (Chinese) with Zipformer CTC|[Click me][wasm-hf-vad-asr-zh-zipformer-ctc-07-03]| [地址][wasm-ms-vad-asr-zh-zipformer-ctc-07-03]|
|VAD + speech recognition (Chinese + English + Korean + Japanese + Cantonese) with [SenseVoice][SenseVoice]|[Click me][wasm-hf-vad-asr-zh-en-ko-ja-yue-sense-voice]| [地址][wasm-ms-vad-asr-zh-en-ko-ja-yue-sense-voice]|
|VAD + speech recognition (English) with [Whisper][Whisper] tiny.en|[Click me][wasm-hf-vad-asr-en-whisper-tiny-en]| [地址][wasm-ms-vad-asr-en-whisper-tiny-en]|
|VAD + speech recognition (English) with [Moonshine tiny][Moonshine tiny]|[Click me][wasm-hf-vad-asr-en-moonshine-tiny-en]| [地址][wasm-ms-vad-asr-en-moonshine-tiny-en]|
|VAD + speech recognition (English) with Zipformer trained with [GigaSpeech][GigaSpeech]    |[Click me][wasm-hf-vad-asr-en-zipformer-gigaspeech]| [地址][wasm-ms-vad-asr-en-zipformer-gigaspeech]|
|VAD + speech recognition (Chinese) with Zipformer trained with [WenetSpeech][WenetSpeech]  |[Click me][wasm-hf-vad-asr-zh-zipformer-wenetspeech]| [地址][wasm-ms-vad-asr-zh-zipformer-wenetspeech]|
|VAD + speech recognition (Japanese) with Zipformer trained with [ReazonSpeech][ReazonSpeech]|[Click me][wasm-hf-vad-asr-ja-zipformer-reazonspeech]| [地址][wasm-ms-vad-asr-ja-zipformer-reazonspeech]|
|VAD + speech recognition (Thai) with Zipformer trained with [GigaSpeech2][GigaSpeech2]      |[Click me][wasm-hf-vad-asr-th-zipformer-gigaspeech2]| [地址][wasm-ms-vad-asr-th-zipformer-gigaspeech2]|
|VAD + speech recognition (Chinese 多种方言) with a [TeleSpeech-ASR][TeleSpeech-ASR] CTC model|[Click me][wasm-hf-vad-asr-zh-telespeech]| [地址][wasm-ms-vad-asr-zh-telespeech]|
|VAD + speech recognition (English + Chinese, 及多种中文方言) with Paraformer-large          |[Click me][wasm-hf-vad-asr-zh-en-paraformer-large]| [地址][wasm-ms-vad-asr-zh-en-paraformer-large]|
|VAD + speech recognition (English + Chinese, 及多种中文方言) with Paraformer-small          |[Click me][wasm-hf-vad-asr-zh-en-paraformer-small]| [地址][wasm-ms-vad-asr-zh-en-paraformer-small]|
|VAD + speech recognition (多语种及多种中文方言) with [Dolphin][Dolphin]-base          |[Click me][wasm-hf-vad-asr-multi-lang-dolphin-base]| [地址][wasm-ms-vad-asr-multi-lang-dolphin-base]|
|Speech synthesis (Piper, English)                                                                  |[Click me][wasm-hf-tts-piper-en]| [地址][wasm-ms-tts-piper-en]|
|Speech synthesis (Piper, German)                                                                   |[Click me][wasm-hf-tts-piper-de]| [地址][wasm-ms-tts-piper-de]|
|Speech synthesis (Matcha, Chinese)                                                                  |[Click me][wasm-hf-tts-matcha-zh]| [地址][wasm-ms-tts-matcha-zh]|
|Speech synthesis (Matcha, English)                                                                  |[Click me][wasm-hf-tts-matcha-en]| [地址][wasm-ms-tts-matcha-en]|
|Speech synthesis (Matcha, Chinese+English)                                                          |[Click me][wasm-hf-tts-matcha-zh-en]| [地址][wasm-ms-tts-matcha-zh-en]|
|Speaker diarization                                                                         |[Click me][wasm-hf-speaker-diarization]|[地址][wasm-ms-speaker-diarization]|
|Voice cloning with ZipVoice (Chinese+English)                                               |[Click me][wasm-hf-voice-cloning-zipvoice]|[地址][wasm-ms-voice-cloning-zipvoice]|
|Voice cloning with Pocket TTS (English)                                               |[Click me][wasm-hf-voice-cloning-pocket]|[地址][wasm-ms-voice-cloning-pocket]|

</details>

### Links for pre-built Android APKs

<details>

<summary>You can find pre-built Android APKs for this repository in the following table</summary>

| Description                            | URL                                | 中国用户                          |
|----------------------------------------|------------------------------------|-----------------------------------|
| Speaker diarization                    | [Address][apk-speaker-diarization] | [点此][apk-speaker-diarization-cn]|
| Streaming speech recognition           | [Address][apk-streaming-asr]       | [点此][apk-streaming-asr-cn]      |
| Simulated-streaming speech recognition | [Address][apk-simula-streaming-asr]| [点此][apk-simula-streaming-asr-cn]|
| Text-to-speech                         | [Address][apk-tts]                 | [点此][apk-tts-cn]                |
| Voice activity detection (VAD)         | [Address][apk-vad]                 | [点此][apk-vad-cn]                |
| VAD + non-streaming speech recognition | [Address][apk-vad-asr]             | [点此][apk-vad-asr-cn]            |
| Two-pass speech recognition            | [Address][apk-2pass]               | [点此][apk-2pass-cn]              |
| Audio tagging                          | [Address][apk-at]                  | [点此][apk-at-cn]                 |
| Audio tagging (WearOS)                 | [Address][apk-at-wearos]           | [点此][apk-at-wearos-cn]          |
| Speaker identification                 | [Address][apk-sid]                 | [点此][apk-sid-cn]                |
| Spoken language identification         | [Address][apk-slid]                | [点此][apk-slid-cn]               |
| Keyword spotting                       | [Address][apk-kws]                 | [点此][apk-kws-cn]                |

</details>

### Links for pre-built Flutter APPs

<details>

#### Real-time speech recognition

| Description                    | URL                                 | 中国用户                            |
|--------------------------------|-------------------------------------|-------------------------------------|
| Streaming speech recognition   | [Address][apk-flutter-streaming-asr]| [点此][apk-flutter-streaming-asr-cn]|

#### Text-to-speech

| Description                              | URL                                | 中国用户                           |
|------------------------------------------|------------------------------------|------------------------------------|
| Android (arm64-v8a, armeabi-v7a, x86_64) | [Address][flutter-tts-android]     | [点此][flutter-tts-android-cn]     |
| Linux (x64)                              | [Address][flutter-tts-linux]       | [点此][flutter-tts-linux-cn]       |
| macOS (x64)                              | [Address][flutter-tts-macos-x64]   | [点此][flutter-tts-macos-x64-cn] |
| macOS (arm64)                            | [Address][flutter-tts-macos-arm64] | [点此][flutter-tts-macos-arm64-cn]   |
| Windows (x64)                            | [Address][flutter-tts-win-x64]     | [点此][flutter-tts-win-x64-cn]     |

> Note: You need to build from source for iOS.

</details>

### Links for pre-built Lazarus APPs

<details>

#### Generating subtitles

| Description                    | URL                        | 中国用户                   |
|--------------------------------|----------------------------|----------------------------|
| Generate subtitles (生成字幕)  | [Address][lazarus-subtitle]| [点此][lazarus-subtitle-cn]|

</details>

### Links for pre-trained models

<details>

| Description                                 | URL                                                                                   |
|---------------------------------------------|---------------------------------------------------------------------------------------|
| Speech recognition (speech to text, ASR)    | [Address][asr-models]                                                                 |
| Text-to-speech (TTS)                        | [Address][tts-models]                                                                 |
| VAD                                         | [Address][vad-models]                                                                 |
| Keyword spotting                            | [Address][kws-models]                                                                 |
| Audio tagging                               | [Address][at-models]                                                                  |
| Speaker identification (Speaker ID)         | [Address][sid-models]                                                                 |
| Spoken language identification (Language ID)| See multi-lingual [Whisper][Whisper] ASR models from  [Speech recognition][asr-models]|
| Punctuation                                 | [Address][punct-models]                                                               |
| Speaker segmentation                        | [Address][speaker-segmentation-models]                                                |
| Speech enhancement                          | [Address][speech-enhancement-models]                                                  |
| Source separation                           | [Address][source-separation-models]                                                  |

</details>

#### Some pre-trained ASR models (Streaming)

<details>

Please see

  - https://github.com/Swift-Tech-Co/sherpa-onnx
  - https://github.com/Swift-Tech-Co/sherpa-onnx
  - https://github.com/Swift-Tech-Co/sherpa-onnx

for more models. The following table lists only **SOME** of them.

|Name | Supported Languages| Description|
|-----|-----|----|
|[sherpa-onnx-streaming-zipformer-bilingual-zh-en-2023-02-20][sherpa-onnx-streaming-zipformer-bilingual-zh-en-2023-02-20]| Chinese, English| See also|
|[sherpa-onnx-streaming-zipformer-small-bilingual-zh-en-2023-02-16][sherpa-onnx-streaming-zipformer-small-bilingual-zh-en-2023-02-16]| Chinese, English| See also|
|[sherpa-onnx-streaming-zipformer-zh-14M-2023-02-23][sherpa-onnx-streaming-zipformer-zh-14M-2023-02-23]|Chinese| Suitable for Cortex A7 CPU. See also|
|[sherpa-onnx-streaming-zipformer-en-20M-2023-02-17][sherpa-onnx-streaming-zipformer-en-20M-2023-02-17]|English|Suitable for Cortex A7 CPU. See also|
|[sherpa-onnx-streaming-zipformer-korean-2024-06-16][sherpa-onnx-streaming-zipformer-korean-2024-06-16]|Korean| See also|
|[sherpa-onnx-streaming-zipformer-fr-2023-04-14][sherpa-onnx-streaming-zipformer-fr-2023-04-14]|French| See also|

</details>

#### Some pre-trained ASR models (Non-Streaming)

<details>

Please see

  - https://github.com/Swift-Tech-Co/sherpa-onnx
  - https://github.com/Swift-Tech-Co/sherpa-onnx
  - https://github.com/Swift-Tech-Co/sherpa-onnx
  - https://github.com/Swift-Tech-Co/sherpa-onnx
  - https://github.com/Swift-Tech-Co/sherpa-onnx

for more models. The following table lists only **SOME** of them.

|Name | Supported Languages| Description|
|-----|-----|----|
|sherpa-onnx-nemo-parakeet-tdt-0.6b-v2-int8| English | It is converted from https://github.com/Swift-Tech-Co/sherpa-onnx|
|Whisper tiny.en|English| See also|
|[Moonshine tiny][Moonshine tiny]|English|See also|
|sherpa-onnx-zipformer-ctc-zh-int8-2025-07-03|Chinese| A Zipformer CTC model|
|[sherpa-onnx-sense-voice-zh-en-ja-ko-yue-2024-07-17][sherpa-onnx-sense-voice-zh-en-ja-ko-yue-2024-07-17]|Chinese, Cantonese, English, Korean, Japanese| 支持多种中文方言. See also|
|[sherpa-onnx-paraformer-zh-2024-03-09][sherpa-onnx-paraformer-zh-2024-03-09]|Chinese, English| 也支持多种中文方言. See also|
|[sherpa-onnx-zipformer-ja-reazonspeech-2024-08-01][sherpa-onnx-zipformer-ja-reazonspeech-2024-08-01]|Japanese|See also|
|[sherpa-onnx-nemo-transducer-giga-am-russian-2024-10-24][sherpa-onnx-nemo-transducer-giga-am-russian-2024-10-24]|Russian|See also|
|[sherpa-onnx-nemo-ctc-giga-am-russian-2024-10-24][sherpa-onnx-nemo-ctc-giga-am-russian-2024-10-24]|Russian| See also|
|[sherpa-onnx-zipformer-ru-2024-09-18][sherpa-onnx-zipformer-ru-2024-09-18]|Russian|See also|
|[sherpa-onnx-zipformer-korean-2024-06-24][sherpa-onnx-zipformer-korean-2024-06-24]|Korean|See also|
|[sherpa-onnx-zipformer-thai-2024-06-20][sherpa-onnx-zipformer-thai-2024-06-20]|Thai| See also|
|[sherpa-onnx-telespeech-ctc-int8-zh-2024-06-04][sherpa-onnx-telespeech-ctc-int8-zh-2024-06-04]|Chinese| 支持多种方言. See also|

</details>

### Useful links

- Documentation: https://github.com/Swift-Tech-Co/sherpa-onnx
- Bilibili 演示视频: https://github.com/Swift-Tech-Co/sherpa-onnx

### How to reach us

Please see
https://github.com/Swift-Tech-Co/sherpa-onnx
for 新一代 Kaldi **微信交流群** and **QQ 交流群**.

## Projects using sherpa-onnx

> React Native wrapper and demo app for validating sherpa-onnx on iOS,
> Android, and Web, including ASR, TTS, VAD, KWS, speaker ID, diarization,
> language ID, punctuation, audio tagging, and speech enhancement.

- NPM package
- Live demo

### Speed of Sound

> A voice-typing application for the Linux desktop (GTK4/Adwaita).
> It captures microphone audio, transcribes it offline using Sherpa ONNX ASR models,
> optionally polishes the text with an LLM, and types the result into the active window
> via XDG Remote Desktop Portal keyboard simulation.

### VoxSherpa TTS

> VoxSherpa TTS is a 100% offline Android Text-to-Speech app powered by Sherpa-ONNX.
> It supports Kokoro-82M, Piper, and VITS engines with multilingual support including
> Hindi, English, British English, Japanese, Chinese and 50+ more languages.

- Download APK (All Versions)
- Android 11+ · 100% offline · No telemetry

<div align="center">

| Generate | Models | Library | Settings |
|:---:|:---:|:---:|:---:|
|  |  |  |  |

</div>

---
### BreezeApp from MediaTek Research

> BreezeAPP is a mobile AI application developed for both Android and iOS platforms.
> Users can download it directly from the App Store and enjoy a variety of features
> offline, including speech-to-text, text-to-speech, text-based chatbot interactions,
> and image question-answering

  - Download APK for BreezeAPP
  - APK 中国镜像

| 1 | 2 | 3 |
|---|---|---|
|[![](https://github.com/user-attachments/assets/1cdbc057-b893-4de6-9e9c-f1d7dfd1d992)](https://github.com/Swift-Tech-Co/sherpa-onnx)|[![](https://github.com/user-attachments/assets/d77cd98e-b057-442f-860d-d5befd5c769b)](https://github.com/Swift-Tech-Co/sherpa-onnx)|[![](https://github.com/user-attachments/assets/57e546bf-3d39-45b9-b392-b48ca4fb3c58)](https://github.com/Swift-Tech-Co/sherpa-onnx)|

### Open-LLM-VTuber

Talk to any LLM with hands-free voice interaction, voice interruption, and Live2D taking
face running locally across platforms

See also https://github.com/Swift-Tech-Co/sherpa-onnx

### voiceapi

<details>
  <summary>Streaming ASR and TTS based on FastAPI</summary>

It shows how to use the ASR and TTS Python APIs with FastAPI.
</details>

### 腾讯会议摸鱼工具 TMSpeech

Uses streaming ASR in C# with graphical user interface.

Video demo in Chinese: 【开源】Windows实时字幕软件（网课/开会必备）

### lol互动助手

It uses the JavaScript API of sherpa-onnx along with Electron

Video demo in Chinese: 爆了！炫神教你开打字挂！真正影响胜率的英雄联盟工具！英雄联盟的最后一块拼图！和游戏中的每个人无障碍沟通！

### Sherpa-ONNX 语音识别服务器

A server based on nodejs providing Restful API for speech recognition.

### QSmartAssistant

一个模块化，全过程可离线，低占用率的对话机器人/智能音箱

It uses QT. Both ASR
and TTS
are used.

### Flutter-EasySpeechRecognition

It extends [./flutter-examples/streaming_asr](./flutter-examples/streaming_asr) by
downloading models inside the app to reduce the size of the app.

Note: [[Team B] Sherpa AI backend](https://github.com/umgc/spring2025/pull/82) also uses
sherpa-onnx in a Flutter APP.

### sherpa-onnx-unity

sherpa-onnx in Unity. See also #1695,
#1892, and #1859

### xiaozhi-esp32-server

本项目为xiaozhi-esp32提供后端服务，帮助您快速搭建ESP32设备控制服务器
Backend service for xiaozhi-esp32, helps you quickly build an ESP32 device control server.

See also

  - ASR新增轻量级sherpa-onnx-asr
  - feat: ASR增加sherpa-onnx模型

### KaithemAutomation

Pure Python, GUI-focused home automation/consumer grade SCADA.

It uses TTS from sherpa-onnx. See also ✨ Speak command that uses the new globally configured TTS model.

### Open-XiaoAI KWS

Enable custom wake word for XiaoAi Speakers. 让小爱音箱支持自定义唤醒词。

Video demo in Chinese: 小爱同学启动～˶╹ꇴ╹˶！

### C++ WebSocket ASR Server

It provides a WebSocket server based on C++ for ASR using sherpa-onnx.

### Go WebSocket Server

It provides a WebSocket server based on the Go programming language for sherpa-onnx.

### Making robot Paimon, Ep10 "The AI Part 1"

It is a YouTube video,
showing how the author tried to use AI so he can have a conversation with Paimon.

It uses sherpa-onnx for speech-to-text and text-to-speech.
|1|
|---|
|[![](https://github.com/user-attachments/assets/f6eea2d5-1807-42cb-9160-be8da2971e1f)](https://github.com/Swift-Tech-Co/sherpa-onnx)|

### TtsReader - Desktop application

A desktop text-to-speech application built using Kotlin Multiplatform.

### MentraOS

> Smart glasses OS, with dozens of built-in apps. Users get AI assistant, notifications,
> translation, screen mirror, captions, and more. Devs get to write 1 app that runs on
> any pair of smart glasses.

It uses sherpa-onnx for real-time speech recognition on iOS and Android devices.
See also https://github.com/Swift-Tech-Co/sherpa-onnx

It uses Swift for iOS and Java for Android.

### flet_sherpa_onnx

Flet ASR/STT component based on sherpa-onnx.
Example a chat box agent

### achatbot-go

a multimodal chatbot based on go with sherpa-onnx's speech lib api.

### fcitx5-vinput

Local offline voice input plugin for Fcitx5 (Linux input method framework).
It uses C++ with offline ASR for speech recognition, supporting push-to-talk,
command mode, and optional LLM post-processing.

Video demo in Chinese: fcitx5-vinput

### Wake Word

A VS Code extension for hands-free voice-activated coding. It uses sherpa-onnx for real-time
keyword spotting (KWS) to detect custom wake phrases and trigger VS Code commands by voice.
Audio capture is handled by decibri, a
cross-platform Node.js microphone streaming library with prebuilt native binaries.

- VS Code Marketplace
- Open VSX
- decibri integration guides for sherpa-onnx

### SmartSub

> SmartSub is a local-first cross-platform desktop application for the complete subtitle production pipeline: audio/video transcription, subtitle translation, proofreading, and subtitle burning/muxing.
>
> It natively integrates sherpa-onnx to power three offline ASR engines  FunASR, Qwen3-ASR, and FireRedASR  delivering high-accuracy Chinese and multilingual speech recognition entirely on-device, with no file uploads required.

### Fono

> Talk to your computer. Fono is an open-source (GPL-3.0), complete voice-AI
> stack (speech-to-text, text-to-speech, a local LLM, wake word, speaker ID) in
> one small binary for the Linux, macOS, and Windows desktop. Press a key and
> speak: it types into any app, answers as a voice assistant, or drives a coding
> agent.

It uses sherpa-onnx's Supertonic TTS models for text-to-speech, with the
Supertonic text frontend ported to Rust. See also
#3750, which fixes dropped
diacritics in the Supertonic frontend for Romanian, Czech, Polish, Hungarian,
Turkish, Vietnamese, and other non-English Latin-script languages.

### Domia

> Domia is an open-source local AI companion you talk to, living entirely on
> hardware you own. Each Domia is its own character, with a distinct
> personality, voice, emotional state, and memory of you and its place  and it
> acts, not just talks: skills connect it to the real world over MCP, Home
> Assistant included. Domia nodes form a local peer-to-peer mesh that shares
> speech and reasoning compute, while room satellites bring each companion into
> the spaces where you live without giving up its identity. No cloud, no
> accounts, and no data leaving your network.

Domia runs sherpa-onnx in-process for keyword spotting, voice activity
detection, streaming and offline speech recognition, and text-to-speech.
Speech engines and models are selected through per-companion configuration,
making it easy to match supported sherpa-onnx models to different hardware.

### qwen-audio-agent

> A realtime full-duplex voice runtime for AI coding agents
> (Claude Code, Codex, OpenCode, and other ACP agents).
> It uses sherpa-onnx keyword spotting with the 3M-parameter
> zh-en transducer model to implement a local voice wake word:
> the app sleeps on idle but keeps the microphone open,
> and the wake phrase brings the session back with no cloud calls.

### Recly

> An open-source recorder for Galaxy Watch, Android, Apple Watch, iPhone, macOS,
> and Windows. Recordings go to the user's own Google Drive; there is no Recly
> server. The Android phone app (which also transcribes Galaxy Watch recordings)
> and the Windows app use sherpa-onnx for on-device transcription: Silero VAD
> splits each recording into speech segments, and sherpa-onnx's INT8 export of
> Qwen3-ASR 0.6B transcribes them. The ~1 GB model is downloaded on demand.

### China Unicom 中国联通安卓 App

> The Android App (version `>= 12.14.1 (2026.07.28)`) uses `sherpa-onnx` Kotlin API for keyword spotting.

### China Life 中国人寿 App

> The Android App (version `>= 3.5.46 (2026.03.23)`) uses `sherpa-onnx` Kotlin API for keyword spotting.

### deepseek-harness

> It uses
> the JavaScript npm package [sherpa-onnx-node][sherpa-onnx-node] with SenseVoice
for local speech recognition.

[sherpa-onnx-node]: https://github.com/Swift-Tech-Co/sherpa-onnx
[silero-vad]: https://github.com/Swift-Tech-Co/sherpa-onnx
[Raspberry Pi]: https://github.com/Swift-Tech-Co/sherpa-onnx
[RV1126]: https://github.com/Swift-Tech-Co/sherpa-onnx
[LicheePi4A]: https://github.com/Swift-Tech-Co/sherpa-onnx
[VisionFive 2]: https://github.com/Swift-Tech-Co/sherpa-onnx
[旭日X3派]: https://github.com/Swift-Tech-Co/sherpa-onnx
[爱芯派]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-speaker-diarization]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-speaker-diarization-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-asr]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-asr-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[Whisper]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-asr-whisper]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-asr-whisper-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-tts]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-tts-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-subtitle]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-subtitle-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-audio-tagging]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-audio-tagging-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-source-separation]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-source-separation-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-slid-whisper]: https://github.com/Swift-Tech-Co/sherpa-onnx
[hf-space-slid-whisper-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-streaming-asr-zh-en-zipformer]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-streaming-asr-zh-en-zipformer]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-streaming-asr-zh-en-paraformer]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-streaming-asr-zh-en-paraformer]: https://github.com/Swift-Tech-Co/sherpa-onnx
[Paraformer-large]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-streaming-asr-zh-en-yue-paraformer]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-streaming-asr-zh-en-yue-paraformer]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-streaming-asr-en-zipformer]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-streaming-asr-en-zipformer]: https://github.com/Swift-Tech-Co/sherpa-onnx
[SenseVoice]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-zh-zipformer-ctc-07-03]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-zh-zipformer-ctc-07-03]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-zh-en-ko-ja-yue-sense-voice]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-zh-en-ko-ja-yue-sense-voice]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-en-whisper-tiny-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-en-whisper-tiny-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-en-moonshine-tiny-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-en-moonshine-tiny-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-en-zipformer-gigaspeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-en-zipformer-gigaspeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-zh-zipformer-wenetspeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-zh-zipformer-wenetspeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[reazonspeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-ja-zipformer-reazonspeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-ja-zipformer-reazonspeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[gigaspeech2]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-th-zipformer-gigaspeech2]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-th-zipformer-gigaspeech2]: https://github.com/Swift-Tech-Co/sherpa-onnx
[telespeech-asr]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-zh-telespeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-zh-telespeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-zh-en-paraformer-large]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-zh-en-paraformer-large]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-zh-en-paraformer-small]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-zh-en-paraformer-small]: https://github.com/Swift-Tech-Co/sherpa-onnx
[dolphin]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-vad-asr-multi-lang-dolphin-base]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-vad-asr-multi-lang-dolphin-base]: https://github.com/Swift-Tech-Co/sherpa-onnx

[wasm-hf-tts-matcha-zh-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-tts-matcha-zh]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-tts-matcha-zh-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-tts-matcha-zh]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-tts-matcha-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-tts-matcha-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-tts-piper-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-tts-piper-en]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-tts-piper-de]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-tts-piper-de]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-speaker-diarization]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-speaker-diarization]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-voice-cloning-zipvoice]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-voice-cloning-zipvoice]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-hf-voice-cloning-pocket]: https://github.com/Swift-Tech-Co/sherpa-onnx
[wasm-ms-voice-cloning-pocket]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-speaker-diarization]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-speaker-diarization-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-streaming-asr]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-streaming-asr-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-simula-streaming-asr]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-simula-streaming-asr-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-tts]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-tts-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-vad]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-vad-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-vad-asr]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-vad-asr-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-2pass]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-2pass-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-at]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-at-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-at-wearos]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-at-wearos-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-sid]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-sid-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-slid]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-slid-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-kws]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-kws-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-flutter-streaming-asr]: https://github.com/Swift-Tech-Co/sherpa-onnx
[apk-flutter-streaming-asr-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-android]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-android-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-linux]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-linux-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-macos-x64]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-macos-arm64-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-macos-arm64]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-macos-x64-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-win-x64]: https://github.com/Swift-Tech-Co/sherpa-onnx
[flutter-tts-win-x64-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[lazarus-subtitle]: https://github.com/Swift-Tech-Co/sherpa-onnx
[lazarus-subtitle-cn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[asr-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[tts-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[vad-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[kws-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[at-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sid-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[slid-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[punct-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[speaker-segmentation-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[GigaSpeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[WenetSpeech]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-streaming-zipformer-bilingual-zh-en-2023-02-20]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-streaming-zipformer-small-bilingual-zh-en-2023-02-16]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-streaming-zipformer-korean-2024-06-16]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-streaming-zipformer-zh-14M-2023-02-23]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-streaming-zipformer-en-20M-2023-02-17]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-zipformer-ja-reazonspeech-2024-08-01]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-zipformer-ru-2024-09-18]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-zipformer-korean-2024-06-24]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-zipformer-thai-2024-06-20]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-nemo-transducer-giga-am-russian-2024-10-24]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-paraformer-zh-2024-03-09]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-nemo-ctc-giga-am-russian-2024-10-24]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-telespeech-ctc-int8-zh-2024-06-04]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-sense-voice-zh-en-ja-ko-yue-2024-07-17]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sherpa-onnx-streaming-zipformer-fr-2023-04-14]: https://github.com/Swift-Tech-Co/sherpa-onnx
[Moonshine tiny]: https://github.com/Swift-Tech-Co/sherpa-onnx
[NVIDIA Jetson Orin NX]: https://github.com/Swift-Tech-Co/sherpa-onnx
[NVIDIA Jetson Nano B01]: https://github.com/Swift-Tech-Co/sherpa-onnx
[speech-enhancement-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[source-separation-models]: https://github.com/Swift-Tech-Co/sherpa-onnx
[RK3588]: https://github.com/Swift-Tech-Co/sherpa-onnx
[spleeter]: https://github.com/Swift-Tech-Co/sherpa-onnx
[UVR]: https://github.com/Swift-Tech-Co/sherpa-onnx
[gtcrn]: https://github.com/Swift-Tech-Co/sherpa-onnx
[tts-url]: https://github.com/Swift-Tech-Co/sherpa-onnx
[ss-url]: https://github.com/Swift-Tech-Co/sherpa-onnx
[sd-url]: https://github.com/Swift-Tech-Co/sherpa-onnx
[slid-url]: https://github.com/Swift-Tech-Co/sherpa-onnx
[at-url]: https://github.com/Swift-Tech-Co/sherpa-onnx
[vad-url]: https://github.com/Swift-Tech-Co/sherpa-onnx
[kws-url]: https://github.com/Swift-Tech-Co/sherpa-onnx
[punct-url]: https://github.com/Swift-Tech-Co/sherpa-onnx
[se-url]: https://github.com/Swift-Tech-Co/sherpa-onnx
[rknpu-doc]: https://github.com/Swift-Tech-Co/sherpa-onnx
[qnn-doc]: https://github.com/Swift-Tech-Co/sherpa-onnx
[ascend-doc]: https://github.com/Swift-Tech-Co/sherpa-onnx
[axera-npu]: https://github.com/Swift-Tech-Co/sherpa-onnx
[SpacemiT-K1]: https://github.com/Swift-Tech-Co/sherpa-onnx
[SpacemiT-K3]: https://github.com/Swift-Tech-Co/sherpa-onnx

---

## Swift Tech Co.

Built and maintained by Swift Tech Co.

AI Automation | FinTech Platforms | Custom Software and Mobile Apps | SaaS Platforms | Cloud Infrastructure | Cybersecurity | SEO and Marketing | API Integration

**Join our community on Telegram:** [t.me/+Qt_eFvkb2rliMzNh](https://t.me/+Qt_eFvkb2rliMzNh)

Home | Services | Careers | Referral Program | Influencers | About | Contact

**Connect**

- Website: https://github.com/Swift-Tech-Co/sherpa-onnx
- LinkedIn: [linkedin.com/in/stephenoladoke](https://www.linkedin.com/in/stephenoladoke/)
- LinkedIn (Company): [linkedin.com/company/swift-tech-co](https://www.linkedin.com/company/swift-tech-co)
- X: [@MrOladoke](https://x.com/MrOladoke)
- Instagram: [@mr.oladoke](https://www.instagram.com/mr.oladoke/)
- Instagram (Company): [@swifttechco](https://www.instagram.com/swifttechco/)
- Organization: [github.com/Swift-Tech-Co](https://github.com/Swift-Tech-Co)

## Sources

Compiled and maintained from upstream [k2-fsa/sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) under permissive open-source license.

---

Maintained by [Swift Tech Co.](https://github.com/Swift-Tech-Co) - [Telegram](https://t.me/+Qt_eFvkb2rliMzNh)

## Sources

Compiled and maintained from upstream [k2-fsa/sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx) under permissive open-source license.

---

Maintained by [Swift Tech Co.](https://github.com/Swift-Tech-Co) - [Telegram](https://t.me/+Qt_eFvkb2rliMzNh)