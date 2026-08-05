# Roulex
*Animated Physical Roulettes for Your Economy*

![](https://i.imgur.com/GSG8KA0.gif) ![](https://i.imgur.com/it8U69N.gif)
![](https://i.imgur.com/inZA3Nt.gif) ![](https://i.imgur.com/aLbzCh0.gif)

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/2ZqPRnNpx8U" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>


## This isn't a Donat Case at spawn. It's an economy item.

Every other roulette/crate plugin does the same thing: a crate sits at spawn, you buy a key, you click it, done. It's a vending machine.

**Roulex is different.** Roulettes are physical items that live in the player's inventory — not a block bolted to your spawn. That one change turns a gimmick feature into an actual economy system:

- Players can **trade** unopened roulettes with each other
- Players can **sell** them on your market/AH plugin like any other commodity
- Players can **lose them on death**, turning PvP and dungeons into real risk/reward
- Rare roulettes become **sought-after items** with their own market value — not a currency sink, but a currency

Set **droppable: false** on any roulette and it locks to that player instead — so you decide, per-roulette, whether it's a tradeable economy item or a personal reward. Nothing else on the market gives you that choice.

## System requirements:

- Java 17+
- Server version 1.19+
- Server software: Paper, Spigot

## Key Features:

- **Physical Economy Items** — Roulettes are real inventory items, not spawn-block gimmicks. Trade them, sell them, drop them on death — build an actual player-driven market around them instead of a one-and-done key system.
- **Unlimited Roulettes** — Create as many roulettes as you want via separate config files, each with its own ID, appearance, and rewards. Run a free starter roulette and a rare PvP-drop roulette side by side.
- **Fully Customizable GUI:**
  - Adjustable window size (27–54 slots).
  - Dedicated reel row where the seamless right-to-left spinning animation plays.
  - Custom informational elements (e.g., a "Possible Rewards" button) to guide and entice players.
- **Flexible Animations & Dynamic Sounds** — Control total spin duration, start/end spin speeds, and how smoothly the reel brakes to a stop. Assign different sound effects, volumes, and pitches to trigger at specific percentages of the spin animation — make a cheap roulette feel instant, and a rare one feel like an event.
- **Two Reward Types:**
  - Give an item directly.
  - Run a console command (grant ranks, currency, permissions).
  - Fully configure the drop chance (weight), display name, and lore for every single reward.
- **Vault Economy Integration** — Make roulettes free or paid, with fully configurable opening costs using your server's in-game currency. Feed straight back into your existing economy instead of running a separate crate-key currency.
- **Permission & Preview System:**
  - Restrict access to specific roulettes via permissions.
  - Preview mode for players without permission — the GUI opens and shows what they could win, but the start button is disabled to encourage rank upgrades.

## Why servers are switching to Roulex:

- A crate at spawn is a transaction. A roulette in someone's inventory is **an asset**.
- Rare roulettes appreciate in trade value organically — you don't have to manufacture scarcity, the item system does it for you.
- PvP servers get a genuine reason to hunt players carrying roulettes.
- Market/AH plugins instantly gain a new tradeable category with zero extra setup.

[![Discord](https://i.imgur.com/xq1G2P7.png)](https://discord.gg/ZMK3ndbJ7p) [![Wiki](https://i.imgur.com/mlkXxmn.png)](https://nelit.gitbook.io/roulex)

## Commands:

```
/roulex give <player> <roulette> [amount] - give a roulette item to a player
/roulex reload - reload configuration
/roulex info - plugin info
```

## Permissions:

```
roulex.reload - Allows reloading Roulex configuration files
roulex.give - Allows giving roulette items to players
roulex.admin - Grants access to all Roulex administrative commands
roulex.open.roulette.<roulette id> - Allows opening a specific roulette
```

## Configuration Files:

<details>
<summary>Plugin config (config.yml)</summary>

```yaml
format: LEGACY
enabled-roulettes:
  - example_roulette

messages:
  prefix: "&cRoulex &8>"

  general:
    no-permission: "&cYou do not have permission to use this command"
    no-permission-to-open: "&cThis roulette is exclusive to donators. Check out our store to unlock it!"
    unknown-command: "&7Unknown command"
    won: "&7You won: &6%reward%&7!"
    not-enough-money: "&cYou don't have enough money to open this roulette. Required: &f%cost%&c."
    economy-unavailable: "&cPaid roulettes are temporarily disabled. Please contact an administrator."
    money-withdrawn: "&7%amount% &7has been withdrawn from your balance to open this roulette."

  roulex:
    usage: "&7Usage: /roulex <give|reload>"

  reload:
    success: "&7Configuration reloaded &asuccessfully"

  give:
    usage: "&7Usage: /roulex give <player> <roulette> [amount]"
    invalid-amount: "&7Invalid amount: '%amount%'. Must be a number."
    amount-out-of-range: "&7Invalid amount: %amount%. Must be between 1 and 64."
    player-not-found: "&7Player not found or not online: %player%"
    roulette-not-found: "&7Roulette not found: %roulette%"
    sender-success: "&7You gave &f%amount%x &6%roulette% &7to &f%player%&7"
    receiver-success: "&7You received &f%amount%x &6%roulette%&7!"
```

</details>

<details>
<summary>Roulette config (example_full.yml)</summary>

```yaml
# Unique identifier of the roulette. Used in commands to reference this specific roulette.
# Must be unique across all roulette files.
# IMPORTANT: if players already have this roulette's item and the id is changed, that item
# will stop working (it's bound to the old id).
id: example_full

# Item the player holds to open the roulette
item:
  # Item material. For example DIAMOND, EMERALD, PLAYER_HEAD, etc.
  material: PLAYER_HEAD

  # Base64 head texture. Only works with material: PLAYER_HEAD
  texture: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNGVkNjc5OTE0OTc4OGI5ZTkwMTY4MTFkM2EzZDBlZDFmNTUyNTMwZDY3Zjk4Njk0NTAzMmQ2ZTQzOWZhODk5ZCJ9fX0="

  # Item name shown in the inventory
  display-name: "&9Example Roulette"

  # Item description (text below the name), line by line
  lore:
    - "&7Example roulette with every"
    - "&7reward type and option shown"
    - " "
    - "&aRight-click to open"

# Whether the player can drop/give away this roulette item.
# true - item can be dropped, false - item is locked to the player and can't be dropped
droppable: true

# Cost to open the roulette (in in-game currency). 0 - opening is free.
# Only works through Vault API - the server must have an economy plugin compatible with Vault
open-cost: 0

# Whether the player needs a special permission to open this roulette.
# true - can't open without the permission, false - available to everyone.
# Permission format: roulex.open.roulette.<roulette id> (e.g. roulex.open.roulette.example_full)
require-permission: false

# Whether a player without the permission above can still open the GUI just to look at it
# (start button will be visible but not clickable). Only matters if require-permission: true.
preview-without-permission: true

# GUI window settings
gui:
  # Total inventory GUI size, in slots. Must be a multiple of 9, minimum 18 (18, 27, 36, 45, 54).
  size: 36

  # GUI window title.
  title: "&dExample Roulette"

  # Row number (starting at 0) in the GUI where the spinning reel is displayed
  # (the row where reward items "spin"). Can't overlap with the start button or custom-elements.
  reel-row: 1

  # Decorative border/background settings for the GUI (filler items in empty slots).
  decoration:
    # Set of items that make up the background. Cycled through in list order.
    materials:
      - material: LIGHT_BLUE_STAINED_GLASS_PANE
        display-name: " " # item name (usually empty so no text is shown)
        lore: [] # item description (usually empty)
      - material: WHITE_STAINED_GLASS_PANE
        display-name: " "
        lore: []
      - material: PURPLE_STAINED_GLASS_PANE
        display-name: " "
        lore: []
    # How many consecutive slots get filled with one material before switching to the next
    # one in the list above.
    block-size: 2

  # Text pointers marking the slot where the spin result will land.
  pointer:
    label-above: "&e▼" # pointer text above the reel
    label-below: "&e▲" # pointer text below the reel

  # Button that starts the roulette spin.
  start-button:
    slot: 31 # slot number in the GUI where the button is placed (starting at 0)
    display-name: "&aStart" # button name
    lore:
      - "&7Spin the roulette!" # button description
    material: PLAYER_HEAD # button material. You can use a regular material instead of a head
    # button texture (only if material: PLAYER_HEAD)
    texture: "eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvZmE4ZjZiMTMxZWY4NDdkOTE2MGU1MTZhNmY0NGJmYTkzMjU1NGQ0MGMxOGE4MTc5NmQ3NjZhNTQ4N2I5ZjcxMCJ9fX0="

  # Additional decorative/informational items in the GUI (buttons with no spin function)
  # NOTE: these items have no click action - lore is shown on hover, like any item.
  custom-elements:
    - slot: 27
      material: BOOK
      display-name: "&ePossible Rewards"
      lore:
        - "&7Common: junk items"
        - "&7Rare: Diamond, Netherite"
        - "&7Special: coins and ranks"

# Spin animation settings
animation:
  # Total spin animation duration, in seconds.
  duration-seconds: 8

  # Delay between item changes in the reel at the START of the animation, in ticks.
  # LOWER value = FASTER reel spin at the start.
  start-speed-ticks: 1

  # Delay between item changes in the reel at the END of the animation (braking), in ticks.
  # HIGHER value = SLOWER reel spin before it stops.
  end-speed-ticks: 12

  # Fraction of the total animation duration (duration-seconds) spent braking.
  # For example, 0.25 means the last 25% of the animation time the reel smoothly slows down.
  brake-fraction: 0.25

# Sound effects for this roulette.
sounds:
  # Sound played when the player opens the roulette GUI.
  open:
    id: UI_BUTTON_CLICK
    volume: 1.0 # sound volume
    pitch: 1.0 # sound pitch, range 0.5-2.0

  # Sound played when the spin finishes and the reward is given.
  win:
    id: ENTITY_PLAYER_LEVELUP
    volume: 1.0
    pitch: 1.0

  # Sounds cycled through during the spin animation, in list order.
  # percent - relative share of the animation this sound covers (doesn't have to add up to 100).
  spin:
    - id: BLOCK_NOTE_BLOCK_BANJO
      volume: 0.6
      pitch: 1.0
      percent: 30 # 0% - 30% of the animation

    - id: BLOCK_NOTE_BLOCK_CHIME
      volume: 0.6
      pitch: 1.0
      percent: 40 # 30% - 70% of the animation

    - id: BLOCK_NOTE_BLOCK_DIDGERIDOO
      volume: 0.8
      pitch: 1.5
      percent: 30 # 70% - 100% of the animation, including the braking phase

# List of rewards. chance is the weight/chance in percent.
# display-name and lore are only required for type: COMMAND.
rewards:
  - material: ROTTEN_FLESH
    amount: 16
    chance: 25.0
    type: ITEM

  - material: COBBLESTONE
    amount: 32
    chance: 20.0
    type: ITEM

  - material: IRON_INGOT
    amount: 4
    chance: 15.0
    type: ITEM

  - material: DIAMOND
    amount: 1
    chance: 8.0
    type: ITEM

  - display-name: "&bRare Netherite"
    lore:
      - "&7A rare and valuable prize!"
    material: NETHERITE_INGOT
    amount: 1
    chance: 2.0
    type: ITEM

  # type: COMMAND runs a console command instead of giving an item.
  # %player% is replaced with the winner's name.
  - display-name: "&6500 Coins"
    material: GOLD_INGOT
    amount: 1
    chance: 20.0
    type: COMMAND
    command: "eco give %player% 500"

  - display-name: "&aVIP Rank (7 Days)"
    material: DIAMOND
    amount: 1
    chance: 8.0
    type: COMMAND
    command: "lp user %player% parent addtemp vip 7d"

  - display-name: "&d&lMVP Rank (Permanent)"
    material: DIAMOND_BLOCK
    amount: 1
    chance: 2.0
    type: COMMAND
    command: "lp user %player% parent add mvp"
```

</details>
