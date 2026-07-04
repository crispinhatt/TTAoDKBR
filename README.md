# Tradução PT-BR — Tiny Tina's Assault on Dragon Keep: A Wonderlands One-Shot Adventure

Tradução não-oficial para o Português do Brasil do jogo standalone **Tiny Tina's Assault on Dragon Keep: A Wonderlands One-Shot Adventure**.

> Baseada na tradução PT-BR completa do BL2 GOTY (CentralDeTraducoes.net.br) e na tradução da DLC original (Tribo Gamer), expandida e adaptada para o standalone com scripts Python.

---

## 📸 Screenshots

*(adicionar screenshots in-game aqui)*

---

## 📦 O que está traduzido

- **Menus principais** — WillowMenu, interface, HUD
- **Legendas e cinematics** — todas as cenas do jogo
- **Missões** — principais e secundárias (log, objetivos, descrições)
- **Skills** — árvores de habilidade de todos os 6 personagens (Gunzerker, Siren, Soldier, Assassin, Krieg, Mechromancer)
- **Armas e equipamentos** — cartões de stats, descrições, fabricantes
- **Desafios** — Badass Rank e desafios da DLC ("Esmagar Abóboras", etc.)
- **NPCs e inimigos** — nomes de todos os personagens, inimigos e chefes
- **Diálogos** — linhas de voz contextuais e sidequests
- **Customizações** — skins e cabeças de todos os personagens
- **Relíquias Serafim** — "Sombra dos Serafins", "Chance de Disparo Adicional"
- **Munições** — descrições de todos os pacotes de ammo
- **Dicas de loading** — 169 dicas da tela de carregamento
- **Launcher** — botões JOGA/AJUDA/DEFINIR/SALVAR/SAIR

## ❌ O que NÃO está traduzido (hardcoded no engine)

- Nomes de sub-áreas do mapa ("Streetwise Wharfs", "Unassuming Docks") — definidos no `.upk` do nível
- Botões de interação in-world ([E] TALK, [V] SMASH) — cookados no `.upk` do engine
- Flavor text de alguns itens especiais (shields Kite, relíquias com flavor text) — definidos no `.upk` de dados

---

## 📊 Cobertura

| Item | Status |
|---|---|
| Arquivos `.int` originais do standalone | 258/258 ✅ |
| Arquivos adicionais carregados pelo engine | +226 ✅ |
| **Total** | **484 arquivos** |
| Cobertura de strings visíveis | **~99,3%** |

---

## 🛠️ Como instalar

### Pré-requisitos
- Jogo instalado via Steam (App ID: 1816010)
- Caminho padrão: `I:\SteamLibrary\steamapps\common\Pawpaw\`

### Passo a passo

**1. Faça backup**

Copie a pasta de localização original antes de qualquer coisa:
```
I:\SteamLibrary\steamapps\common\Pawpaw\WillowGame\Localization\INT\
```
Guarde em local seguro.

**2. Baixe a tradução**

Baixe o arquivo ZIP da [última release](../../releases/latest).

**3. Extraia os arquivos**

Extraia o conteúdo do ZIP e copie **todos os arquivos** para:
```
I:\SteamLibrary\steamapps\common\Pawpaw\WillowGame\Localization\INT\
```
Confirme a substituição quando solicitado. A pasta ficará com **484 arquivos** (era 258).

**4. Jogue**

Abra o jogo normalmente pela Steam. Os textos aparecerão automaticamente em **Português do Brasil**.

> **Nota:** Não é necessário alterar nenhuma configuração de idioma no Steam ou no jogo. O engine lê automaticamente os arquivos da pasta `INT\`.

---

## 🔄 Como desinstalar

1. Feche o jogo
2. Restaure o backup da pasta `INT\` original (258 arquivos)
3. Ou use o Steam: `Biblioteca → Botão direito no jogo → Propriedades → Arquivos locais → Verificar integridade`

---

## ⚠️ Avisos importantes

- Esta é uma tradução **não-oficial** — sem relação com Gearbox Software ou 2K Games
- Testada na versão **1.0.4.0** do standalone (build Epic/Steam 2022)
- Se o jogo atualizar e alguma string quebrar, restaure o backup e verifique novas releases aqui
- **Não coloque arquivos extras** além dos incluídos no ZIP — arquivos fora da lista do `DefaultEngine.ini` causam "Initialization Error" na inicialização

---

## 🔧 Como funciona — Documentação Técnica

### Engine

O TTAoDK standalone usa:
- **Engine:** Unreal Engine 3 (UDK)
- **Localização:** sistema de arquivos `.int` (INI-style com encoding UTF-16LE + BOM)
- **Pasta:** `WillowGame\Localization\INT\`

### Estrutura dos arquivos `.int`

Três formatos coexistem nos arquivos:

```ini
; Formato 1 — subtitles/legendas
[Subtitles]
VO_Pawpaw_Previously_01=Então você quer ouvir uma história...

; Formato 2 — KEY=VALUE simples (UI, menus, skills)
[HUD]
AmmoTitle=MUNIÇÃO
ToolTipsKB_Talk=[E] FALAR

; Formato 3 — structs aninhadas (NPCs, missões, pops)
[M_Aster_PlotMission01 MissionDefinition]
MissionName="Um Jogo de RPG"
MissionDescription="..."
PlayThroughs[0]=(DisplayName="Cidadão de Flamerock")
```

### Encoding

| Arquivo | Encoding |
|---|---|
| Standalone `.int` original | UTF-16LE com BOM (`FF FE`) |
| BL2 GOTY traduzido WillowMenu | cp1252 (sem BOM) |
| BL2 GOTY traduzido demais `.int` | UTF-16LE sem BOM |
| **Output final** | **UTF-16LE com BOM — sempre** |

### Fontes da tradução

| Fonte | Uso |
|---|---|
| CentralDeTraducoes — BL2 GOTY INT | Skills, missões BL2, UI, HUD |
| CentralDeTraducoes — DLC Aster INT | Missões, NPCs, itens da DLC |
| CentralDeTraducoes — DLC Lilac INT | Skills do Krieg/Psicopata |
| CentralDeTraducoes — DLC Tulip INT | Skills da Mechromancer |
| ESN (espanhol standalone) | Arquivos extras não cobertos pelo BL2 |
| Tradução manual/revisada | Desafios, Badass Tokens, nomes de inimigos |

### Scripts do projeto

Os scripts Python (`1`–`18`) ficam em `J:\Projetostraducao\BorderlandsTTADK\`.

| Script | Função |
|---|---|
| `1_extrair_strings.py` | Gera `strings_standalone.json` |
| `2_extrair_traduzidos.py` | Gera `strings_traduzidos.json` |
| `3_comparar.py` | Gera `mapa_traducao.json` |
| `4_gerar_arquivos.py` | Gera 257 arquivos em `output_int\` |
| `7_aplicar_restantes.py` | Aplica strings restantes |
| `10_mesclar_willowmenu.py` | Mescla WillowMenu (cp1252 + standalone) |
| `11_traduzir_willowmenu_restantes.py` | 40 strings novas do standalone |
| `12_corrigir_challenges.py` | Copia GD_Aster_Challenges.INT da DLC |
| `13_corrigir_subtitles_e_inimigos.py` | Subtitles + nomes de inimigos |
| `14_corrigir_subtitles_completo.py` | Corrige strings truncadas |
| `15_traduzir_nomes_inimigos.py` | 38 nomes de inimigos/NPCs |
| `18_copiar_traducoes_kv.py` | Copia tradução KEY=VALUE do BL2/DLCs |

### Regras críticas do engine

1. **Encoding obrigatório:** UTF-16LE com BOM (`\xFF\xFE`) — o engine ignora arquivos sem BOM
2. **Não adicionar arquivos arbitrários** — apenas arquivos listados no `DefaultEngine.ini` como `StartupPackages` ou que correspondam a `.upk` carregados são lidos
3. **WillowMenu.int deve ser MESCLADO** — nunca copiado direto do BL2 (faltam chaves do standalone)
4. **Subtitles.int:** formato KEY=VALUE sem aspas para VO_, com aspas para TIP_

---

## 📜 Histórico de versões

### v1.0.0 — Jul/2025
- Primeira versão pública
- 484 arquivos `.int` (258 originais + 226 extras)
- ~99,3% de cobertura de strings visíveis
- Tradução completa de skills, missões, UI, HUD, NPCs, inimigos, itens, customizações

---

## 🤝 Créditos

- **Tradução base BL2 GOTY:** [CentralDeTraducoes.net.br](https://centraldetraducoes.net.br)
- **Tradução base DLC (Tribo Gamer):** grupo Tribo Gamer
- **Adaptação e scripts standalone:** PINHATT
- **Assistência técnica:** Claude (Anthropic)

---

## 📄 Licença

Uso pessoal e não-comercial. Créditos às fontes originais obrigatórios em redistribuições.
