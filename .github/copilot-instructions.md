# Copilot Instructions — CK3 AGOT Bank Management Mod

## REGRA CRÍTICA: Permissões de Arquivo

**Copilot NÃO tem permissão para copiar, mover, sincronizar ou fazer robocopy de arquivos para a pasta instalada do mod.**

- Pasta instalada (SOMENTE O USUÁRIO PODE MODIFICAR):
  `C:\Users\Pedro\Documents\Paradox Interactive\Crusader Kings III\mod\AGOT - BANK MANAGEMENT\`

- Pasta de trabalho (workspace — Copilot pode editar aqui):
  `c:\Users\Pedro\Downloads\CK3---AGOT---BANK-MANAGEMENT-master\`

Após qualquer edição, **listar os arquivos alterados** para que o usuário os copie manualmente.

## Estrutura do Mod

- `common/decisions/` — decisões do banco
- `common/scripted_triggers/` — triggers de visibilidade
- `common/scripted_effects/` — efeitos de política
- `common/customizable_localization/` — loc customizada
- `events/` — eventos do dashboard
- `gui/event_window_widgets/` — widgets GUI
- `localization/english/` — arquivos YML (precisam de UTF-8 BOM)

## Regras Técnicas CK3

- YML de localização: **sempre UTF-8 com BOM** (bytes 239 187 191)
- Sem `fontsize_min` nos GUIs
- Background: `background = { color = { 0 0 0 0.4 } }` — não usar string
- Widgets passivos em eventos não disparam eventos (sem botões funcionais)
- Scope em localização: `GetPlayer.*` — não usar `ROOT.*`
