<div align="center">

**[中文](./README.md) · English · [Français](./README.fr.md)**

# CrazyPearl · PRL Auto-Overclocking & Efficient Mining

### Find your GPU's efficient range. Get more hashrate from every watt.

Per-GPU core-offset and power testing, built to find lower-power, higher-efficiency mining settings.

![Windows x64](https://img.shields.io/badge/Windows-x64-0078D4?style=flat-square)
![Version](https://img.shields.io/badge/Version-v0.2.19_Beta-33BFA0?style=flat-square)
![PRL](https://img.shields.io/badge/PRL-PearlHash-7189FF?style=flat-square)

**[Download app](./疯狂的珍珠-0.2.19.exe?raw=true)** · **[Initial settings](./settings.json?raw=true)** · **[Share ledger](./fee-ledger.json?raw=true)**

[Measured results](#what-one-tuning-run-achieved) · [Quick start](#quick-start) · [Features](#features) · [Everyday settings](#everyday-settings) · [Files and upgrades](#files-and-upgrades)

</div>

---

**The same GPU can sometimes deliver similar or higher hashrate while drawing less power—with the right settings.** CrazyPearl automates the search: measure a baseline, test core overclock offsets and power limits, score measured hashrate against power, then validate and save a profile. Each NVIDIA GPU gets its own test, accounting for different models and individual silicon.

## What one tuning run achieved

A local PRL test with an RTX 5070 Ti:

| Metric | Before: baseline | Validated efficiency profile | Change |
| :--- | ---: | ---: | ---: |
| **Average GPU power** | 279.82 W | **249.98 W** | **10.7% lower** |
| **Average local hashrate** | 177.03 TH/s | **178.77 TH/s** | **1.0% higher** |
| **GPU hashrate per watt** | 0.633 TH/s/W | **0.715 TH/s/W** | **13.0% higher** |

**About 30W less GPU power, with a small hashrate gain in this test.** The profile used a +120 MHz core offset and a 250W power cap; the baseline cap was 280W. The baseline measurement lasted 180 seconds. The candidate completed a 600-second confirmation, with 16 shares accepted by the pool.

<details>
<summary>Test conditions and measurement basis</summary>

This example comes from the 0.2.18 auto-tuning test; the current 0.2.19 adds multi-GPU compatibility improvements. SRBMiner-MULTI 3.7.3, NVIDIA driver 617.42, memory target 7001 MHz and fans at 100% in both configurations. Hashrate comes from local engine reports; power comes from driver readings. Efficiency is calculated from integrated hashrate and energy over the measurement window. Percentages use unrounded values.

Results describe this card under these conditions. Test other GPUs, engines and environments independently. GPU power excludes the motherboard, CPU and PSU conversion losses; add those separately in the earnings calculator for whole-system estimates.

</details>

## Why CrazyPearl?

| Put hashrate per watt first | Tune each physical GPU | Keep the rig running |
| :--- | :--- | :--- |
| Choose best efficiency to compare power while retaining your minimum baseline hashrate, or choose highest hashrate when throughput is the priority. | Measure and save profiles per card instead of applying one GPU's settings across the entire rig. | Candidates get a 10-minute confirmation. Cancel with rollback, use thermal and recovery rules, and keep settings saved automatically. |

Core overclocking and power limits are tested together. The search never raises the starting power cap. If the driver lacks core-offset support, it tests power settings only.

## Features

| Feature | What it does |
| :--- | :--- |
| **Per-GPU auto-tuning** | Test measured hashrate and power for each NVIDIA GPU; keep separate best-hashrate and GPU-efficiency results, cancel with rollback, and save validated profiles. |
| **Three interface languages** | Choose 中文, English or Français at the top right. Changes apply immediately and save automatically, without changing your inputs or mining session. |
| **Multiple mining engines** | SRBMiner-MULTI, PeakMiner and BzMiner, with description cards, official download links and full-folder imports in one place. |
| **Multi-GPU monitoring** | Per-card hashrate, GPU core and memory temperatures, power, fan speed, clocks and shares. Long tables scroll independently; tuning targets follow device identity. |
| **Direct GPU tuning** | Adjust NVIDIA power, fans and clocks. Read supported driver clock bins with a dedicated button, then apply now or on mining start. |
| **Protection and recovery** | Configure low-hashrate, no-accepted-share and thermal rules, startup warm-up time and a restart budget. |
| **Local hashrate history** | Updates follow engine reports. Choose minutes, hours or days; gaps are marked in red and logged. |
| **Earnings and electricity estimates** | Choose an exchange and price basis. Combine hashrate, electricity price, power and daily runtime to estimate net earnings and energy costs, in CNY or USD. |
| **Pools and startup** | Enter your own wallet or pool account and worker name, configure backup pools and optionally start mining at Windows sign-in with saved settings. |
| **Logs and diagnostics** | Search live engine output, view app logs and export diagnostics. Logs stay together and follow a seven-day retention policy. |

Readings come from the engine or driver. Unavailable readings are marked in the interface. GPU compatibility depends on the selected engine; direct tuning is for NVIDIA GPUs.

## Quick start

### 1. Download three files into one folder

Use a **writable folder**. No archive extraction is needed. Install the GPU driver beforehand.

| File | Download | Purpose |
| :--- | :---: | :--- |
| **疯狂的珍珠-0.2.19.exe** | [Download app](./疯狂的珍珠-0.2.19.exe?raw=true) | Main application; the filename stays the same in all languages |
| **settings.json** | [Download settings](./settings.json?raw=true) | Blank initial configuration; valid edits save automatically |
| **fee-ledger.json** | [Download ledger](./fee-ledger.json?raw=true) | Initial share ledger ledger |

You can also open each repository file and select **Download raw file**. Save this README for offline reference if needed.

### 2. Choose an engine and enter your payout details

Open the EXE and select **English** at the top right. In **Mining engines**, download and select an engine, or import an existing engine's complete folder. Return to **Overview** and enter:

| Setting | What to enter |
| :--- | :--- |
| **Payout address / pool account** | Your own PRL address, or the account required by your pool. |
| **Worker name** | A recognizable name for this rig. Some pools use `account.worker`; edit the name after the dot in the payout/account field for those pools. |
| **Pool address** | The pool's `hostname:port`. Follow the chosen engine's instructions for backup connections and account rules. |

> **Enter your own payout details first. If you start with a blank payout address, the app uses the author's address and the affected earnings go to the author. A notice appears in Overview.**

### 3. Start mining and set your operating rules

Select **Start mining** and check hashrate, temperatures and accepted shares in Overview. Valid parameter changes save automatically.

- **For continuous operation:** fill in low-hashrate, share timeout, thermal and restart-limit rules in **Protection & recovery**.
- **For GPU tuning:** open **GPU tuning**, select **Read driver clock bins**, choose targets and select **Apply now**, or enable applying tuning when mining starts.
- **For automatic tuning:** start mining, select the online NVIDIA GPUs to test, choose **Best efficiency** or **Highest hashrate**, then select **Start auto-tuning**. Cards are tested one at a time: 60 seconds warm-up, 180 seconds measurement and a 10-minute confirmation for the candidate profile. Confirmed profiles save automatically. Power stays within the starting cap; **Cancel and restore** returns to the pre-test settings. open **Earnings**, choose an exchange and enter electricity price, exchange rate and other calculation inputs.

The public configuration has blank account, worker and device tuning fields, with a zeroed share ledger. Electricity price, hashrate and power estimate inputs start at zero; enter your own values.

## Everyday settings

<details>
<summary><strong>Automatic recovery: rules for low hashrate and missing shares</strong></summary>

Example: restart the engine if hashrate stays below **10%** of its baseline for **5 minutes**, allowing at most **3 restarts in 15 minutes**. These are example values; adjust them for your rig.

Share timeouts, warm-up and thermal rules are configurable separately. Use the local chart and app log to review when a fault occurred and what the app did.

</details>

<details>
<summary><strong>GPU tuning: read supported bins, then apply targets</strong></summary>

**Read driver clock bins** lists the driver's supported clock combinations. Editing saves targets; **Apply now** changes hardware. A core or memory clock value of **0** selects automatic mode.

Each GPU keeps its own targets, mapped by device identity.

</details>

<details>
<summary><strong>Backup pools and automatic startup</strong></summary>

Add backup connections in pool settings and check the selected engine's account, password and connection rules.

Before enabling automatic startup in **Protection & recovery**, check that your own payout details and pool have been saved. Mining starts with the saved configuration at the next Windows sign-in.

</details>

<details>
<summary><strong>Earnings: include electricity and operating conditions</strong></summary>

Choose an exchange and price basis, such as best bid or latest trade. Enter electricity price, USDT-to-CNY rate, other power consumption, daily runtime and the combined deduction percentage. View daily earnings and electricity estimates in CNY or USD.

Daily earnings are estimates derived from the selected market data and calculation inputs, rather than a record of pool payments. Keep the same calculation basis when comparing devices or settings.

</details>

## Files and upgrades

<details>
<summary><strong>Application, settings and logs stay in the application folder</strong></summary>

```text
CrazyPearl/
├─ 疯狂的珍珠-0.2.19.exe
├─ README.md / README.en.md / README.fr.md  Optional local guides
├─ settings.json       Auto-saved settings
├─ fee-ledger.json     Cumulative timing
├─ logs/               Runtime logs
├─ kernels/            Downloaded or imported engines
└─ downloads/          Download cache
```

The three folders are created automatically when needed. Logs are retained for today and the preceding six days. Files being written or in use are cleaned up later; settings and the timing ledger are retained.

**To upgrade:** stop mining and exit the app. Keep your existing `settings.json`, `fee-ledger.json` and `kernels/`, then replace the EXE with the new version. Do not overwrite your settings with the blank initial configuration.

</details>

<details>
<summary><strong>Per-GPU auto-tuning</strong></summary>

Start mining, select GPUs in GPU tuning, then scroll to the automatic test. Choose efficiency or hashrate, set the throughput floor and core-offset ceiling, and start. Use only one GPU tuning controller.

Defaults retain 90% of baseline hashrate with a +180 MHz offset ceiling. Each trial warms up for 60 seconds, measures for 180 seconds, then validates the candidate for 10 minutes. Cards are tested sequentially. Validated settings are saved and remain applied; the existing apply-on-mining-start option controls later starts.

The test never raises the starting power cap. It explores supported core offsets, power limits and nearby combinations; unsupported offsets use power-only tuning. Memory stays at baseline settings and voltage is unchanged. Cancellation, heat, GPU loss or faults trigger rollback; failed rollback stops this app's miner. Accepted-share validation uses process-wide counts and does not independently prove submission by every GPU.

Efficiency is measured GPU TH/s/W; motherboard consumption and PSU losses also affect whole-system cost. Results describe this device, engine and search range. Retest after engine or driver changes. Details are in `logs/date/auto-tune-*/report.json` under the seven-day log retention policy.

</details>

---

Software share fee: about 0.2%; engine fees are separate.

Fees are based on pool-accepted share counts: 998 accepted user shares trigger a batch targeting two accepted author shares. Share difficulty can vary, so this is not a fixed percentage of earnings.

This repository distributes a Windows x64 application. Source code, GPU drivers and third-party mining engines are not included. Engines are published by their respective authors; the app provides official download entry points. The app includes publisher integrity verification. Download the original files from this repository.

<details>
<summary>Developer PRL payout address</summary>

```text
prl1pqc3uxyeewp880raqumz5q6uuzaw9l3rpjxz2ur6agq5pzwmynpfqszj5nx
```

</details>

<div align="center">

[中文](./README.md) · **English** · [Français](./README.fr.md)

</div>
