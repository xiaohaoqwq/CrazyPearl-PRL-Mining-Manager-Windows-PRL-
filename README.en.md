<div align="center">

**[中文](./README.md) · English · [Français](./README.fr.md)**

# CrazyPearl

### PRL mining on Windows, with less setup and less babysitting

Mining engines, pools, GPU controls and earnings estimates in one window.

![Windows x64](https://img.shields.io/badge/Windows-x64-0078D4?style=flat-square)
![Version](https://img.shields.io/badge/Version-v0.2.17_Beta-33BFA0?style=flat-square)
![PRL](https://img.shields.io/badge/PRL-PearlHash-7189FF?style=flat-square)

**[Download app](./疯狂的珍珠-0.2.17.exe?raw=true)** · **[Initial settings](./settings.json?raw=true)** · **[Timing ledger](./fee-ledger.json?raw=true)**

[Quick start](#quick-start) · [Features](#features) · [Everyday settings](#everyday-settings) · [Files and upgrades](#files-and-upgrades)

</div>

---

Getting a miner running is only the beginning. You still need to watch hashrate, track disconnections and check temperatures. **CrazyPearl brings those everyday tasks together.** Choose an engine, enter your payout details and pool, and manage your rig from one place. Valid settings save automatically for the next session.

## What's new in v0.2.17

- **Blank address stays blank.** The input and saved configuration remain empty. Mining uses the author's address with a persistent inline notice; no popup is shown. Per-pool payout overrides still take precedence.
- **Fees accrue from accepted shares.** At equal share difficulty, 998 accepted user shares earn a batch targeting two accepted author shares. The old 240-second minimum is removed. Rejected shares, overlapping protocol reports and warm-up time do not count. Any extra confirmations reported in a batch are credited against future fees.
- **Partial progress survives restarts.** If one author share is confirmed, only the remaining share is requested on retry. An attempt is limited to 600 seconds; an incomplete attempt resumes user mining and backs off for one hour.
- **User-only hashrate history.** Author sessions do not enter the chart or user statistics CSV and do not create network-failure markers. User samples resume at their real timestamps, without invented points or a line bridging the excluded interval.
- **Three languages remain available:** Chinese, English and French, with instant switching and automatic saving.

The fee ratio is based on accepted share counts. Share difficulty can vary between pools and over time, so this is not a fixed percentage of earnings. Scheduling records stay in the independent ledger and app event files; original engine output remains available for diagnostics.

Keep your existing settings, ledger, engines and logs when upgrading; replace only the EXE. Legacy time-based totals are retained as history. New billing starts from actual accepted shares and does not convert old seconds into shares.

## Why CrazyPearl?

| See every GPU | Recover from interruptions | Tune with driver data |
| :--- | :--- | :--- |
| View total hashrate alongside individual cards. Find the card losing speed or running hot. | Set rules for low hashrate, missing accepted shares and high temperatures, with a restart limit. | Read the driver's supported clock bins before choosing targets. Manage power, fans and clocks together. |

**Fewer windows and scripts to juggle. A clearer view of your rig.**

## Features

| Feature | What it does |
| :--- | :--- |
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
| **疯狂的珍珠-0.2.17.exe** | [Download app](./疯狂的珍珠-0.2.17.exe?raw=true) | Main application; the filename stays the same in all languages |
| **settings.json** | [Download settings](./settings.json?raw=true) | Blank initial configuration; valid edits save automatically |
| **fee-ledger.json** | [Download ledger](./fee-ledger.json?raw=true) | Initial cumulative timing ledger |

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
- **For earnings estimates:** open **Earnings**, choose an exchange and enter electricity price, exchange rate and other calculation inputs.

The public configuration has blank account, worker and device tuning fields, with a zeroed timing ledger. Electricity price, hashrate and power estimate inputs start at zero; enter your own values.

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
├─ 疯狂的珍珠-0.2.17.exe
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

---

Software share fee: about 0.2%; engine fees are separate.

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
