# RMB/USD Exchange Rate Board

[简体中文](./README.md) | English

![RMB/USD rate board interface preview](artifacts/ui-audit/rmb-usd-rate-board.png)

A lightweight desktop widget for Windows 11. When you convert US-dollar cash remittances into RMB, it shows where today's USD/CNY rate sits within its own recent history, so you can see at a glance whether the current rate is high or low compared with the past 1 to 5 years.

## Data methodology

- Official central parity: from the public query page of the State Administration of Foreign Exchange (SAFE), with the data sourced by the China Foreign Exchange Trade System (CFETS). The central parity is the daily reference rate published for the RMB against major currencies.
- Bank reference price: the USD cash-buying rate of the Bank of China (the price at which the bank buys your US-dollar cash account balance).
- Historical position: the latest official central parity is compared with the daily central parities of all trading days over the last 1, 2, 3, and 5 years, using a mid-rank percentile.

Bank prices are for reference only; the actual transaction price is whatever your bank quotes when you do the business.

## Usage

The most convenient way is to double-click `启动汇率看板.cmd` in the repository root. The official release build lives at `release/win-x64/人民币美元汇率看板.exe`. Clicking the close button hides the window to the system tray; double-clicking the tray icon brings it back. Re-running the EXE also recalls an already-open board instead of creating a second instance. The pin button toggles always-on-top.

App data is stored in `%LOCALAPPDATA%\RmbUsdWidget`. By default the app does not start automatically with Windows.

## Development

```powershell
dotnet build RmbUsdWidget.sln
dotnet test RmbUsdWidget.sln
dotnet run --project .\src\RmbUsdWidget
dotnet run --project .\tests\RmbUsdWidget.Tests
```

## Release

```powershell
.\scripts\publish.ps1
```

Release output goes to `release/win-x64/`. Screenshots, the design review, and implementation comparison materials are under `artifacts/ui-audit/` and in `docs/qa/design-qa.md`.

## Project structure

```text
.
├─ src/RmbUsdWidget/       source code
├─ tests/RmbUsdWidget.Tests  automated tests
├─ docs/qa/               design-qa.md (design acceptance report)
├─ artifacts/ui-audit/     UI screenshots and comparison materials
├─ scripts/                release scripts
├─ release/                local release artifacts, not committed to Git
├─ RmbUsdWidget.sln
├─ README.md
└─ 启动汇率看板.cmd
```
