# AGOT Bank Mod Discoveries and Integration Notes

Date: 2026-03-21

## AGOT files copied for reference (inside workspace)
- AGOT_SOURCE_REFERENCE/common/decisions/agot_decisions/00_agot_banking_decisions.txt
- AGOT_SOURCE_REFERENCE/common/scripted_effects/00_agot_banking_effects.txt
- AGOT_SOURCE_REFERENCE/common/character_interactions/00_agot_banking_interactions.txt
- AGOT_SOURCE_REFERENCE/common/modifiers/00_agot_iron_bank_modifiers.txt
- AGOT_SOURCE_REFERENCE/common/customizable_localization/00_agot_banking_custom_loc.txt
- AGOT_SOURCE_REFERENCE/events/agot_events/agot_banking_events.txt
- AGOT_SOURCE_REFERENCE/gui/event_window_widgets/agot_enter_text_banking.gui
- AGOT_SOURCE_REFERENCE/gui/event_window_widgets/agot_character_list_banks.gui
- AGOT_SOURCE_REFERENCE/localization/english/agot/event_localization/agot_banking_l_english.yml

## Confirmed AGOT banking structure
- Namespace: `agot_banking`
- Core player decision flow starts at event `agot_banking.1001` (bank selection for loans).
- Existing AGOT management event: `agot_banking.0211`.
- Director-setting policy event: `agot_banking.0208` (interest level).

## Bank participation and role model in AGOT
- Director flags:
  - `IB_Director`
  - `bank1_Director`
  - `bank2_Director`
  - `bank3_Director`
- Shareholder variables (character scope):
  - `IB_Shares`
  - `bank1_Shares`
  - `bank2_Shares`
  - `bank3_Shares`

## Core bank globals in AGOT
- Liquidity/value:
  - `IB_FreeCapital`, `bank1_FreeCapital`, `bank2_FreeCapital`, `bank3_FreeCapital`
  - `*_LoanedCapital`, `*_BankValue`, `*_ValuePerShare`, `*_NofShares`
- Performance/risk:
  - `*_Earnings`, `*_Expenses`, `*_LostLoans`
  - `*_NofLoans`, `*_NofDefaults`
  - `*_RiskLevel`, `*_DividendLevel`, `*_InterestLevel`

## Gameplay model confirmed in AGOT scripts
- Interest level uses `-1 / 0 / 1` (low / medium / high).
- Lower interest tends to increase demand but reduce margin.
- Director stats (notably stewardship and diplomacy in several places) influence outcomes.
- War/economic context and RNG produce variable outcomes even with same policy.

## Engine and performance constraints (important)
- CK3 script execution is not designed for custom multicore scheduling from mods.
- CK3 mods cannot offload logic to GPU for gameplay scripts.
- Best performance strategy is reducing script frequency and scope.

## Stability strategy used in this submod
- Event-based dashboard (safe) instead of heavy always-on GUI loops.
- No aggressive global pulses for every character each day.
- Role-gated actions to reduce unnecessary script execution.
- Minimal hard overwrite approach to lower conflict risk.

## Mod load-order recommendation
- Keep this submod loaded after AGOT so its additions win when overlap exists.
- Prefer additive files and scripted hooks over replacing AGOT core files.

## Current submod integration state
1. Dashboard now reads real AGOT bank globals.
2. Investor access uses AGOT share variables.
3. Manager controls use AGOT director flags.
4. Policies write back into AGOT globals (risk/dividend/interest).
5. Dashboard includes a direct link into AGOT management event (`agot_banking.0211`).
6. Custom event widgets are now active:
   - dashboard layout (bank header, KPI cards, manager panel, debtor cards, incoming payments)
   - policy matrix layout (option/suboption impact table)
7. Monthly snapshot history is recorded on dashboard open (low overhead) and shown as 12-point trend values.

## Next upgrade targets
- Convert snapshot trend values into true visual bars/graph sprites.
- Pull additional debtor payment-history fields if AGOT exposes persistent paid-to-date values.
- Add optional direct action buttons on debtor cards (open character, remind, enforce route).
