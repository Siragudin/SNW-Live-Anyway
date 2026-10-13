# SNW: Live Anyway — Concept Document

Oct 12, 2026 · @Siragudin

SNW: Live Anyway is a persistent post-apocalyptic survival sandbox with no scripted story: you start as a stranger with a backpack, and the world you leave behind is the one you built.

© 2026 Siragudin Guseynov. All rights reserved. Licensed under Creative Commons BY-NC-ND 4.0.

## High Concept

**The pitch.** SNW: Live Anyway is a persistent, online, post-apocalyptic survival sandbox built on one promise: real freedom. Not "freedom within the rails the developer allows." There is no script to follow and no chosen one to play. There is a living world, and you get to live in it.

The world doesn't bend around you. You enter as one survivor among many, and what the world becomes depends on what you physically do in it.

**The vertical arc.** Survival is where you start, not where you finish. The real goal is to grow and make the world around you better:

1. **Solo survival.** Scrounging sticks with a backpack and a pistol.
2. **Cooperation.** A trusted group, then a Community.
3. **Settlement.** A fortified base in the Wilds.
4. **District governance.** You own a sovereign server-state and write its laws.

Founding a District is not the end of the game. It is the moment the simulation shifts to the macro layer, and the game becomes geopolitics.

**Core fantasy.** *"I'm the one who builds the new world."* You start alone, with nothing but a backpack. You find people you trust. Together you build a safe Settlement. The Settlement grows into a Society, the Society builds a Civilization, and one day the stranger with the backpack runs an entire District. A month later you walk back to a place you once left, and you don't recognize it. You did that.

**Design pillars.**

| Pillar | What it means |
| --- | --- |
| Cooperation over toxic competition | The architecture removes the incentive to kill for loot: a dead player's body cannot be looted. Surviving together is simply the better deal. |
| Player-written rules | Districts are not city-builder skins. Players set the laws, the economy and the access rules on their own server. |
| A world that lives without you | The simulation never pauses. NPCs act, markets move, weather transforms materials, and consequences accumulate while you are offline. |
| GameAI, not scripts | The AI Mayor and the world's creatures are driven by a managed AI layer that recomposes behavior continuously. Players can't memorize patterns. |

**What makes it different.**

- **No loot-the-corpse economy.** Most survival games reduce to killing newcomers for gear. Here that motivation is designed out, not banned. PvP still exists, but for human reasons: ideology, territory, clan politics, revenge.
- **A District is not a "settlement."** In a typical game, the city is a decorated menu and the mayor role is a UI. In Live Anyway the District owner actually controls a physical territory, an economy and access rights on a real server.
- **No pause button.** When you leave, the world keeps computing. You come back to an honest, logical result of what happened without you.
- **A living AI Mayor.** Not a quest-giver waiting for you to walk up, but a dynamic governor modeled on a fair, objective and very strict human ruler.

## Design Philosophy: Simulation-Native Worlds

Live Anyway is built on Simulation-Native Worlds (SNW), the idea that a digital world should be a continuous living system, not a stage set. Four principles carry that idea.

**1. The world is a system, not a script.** There are no authored events or story triggers. There are base conditions and rules, and events emerge from cause and effect. A blockaded trade route, an economic crisis, a clan split, the capture of a powered-down District: none of it was written by a designer. It is the product of player actions and GameAI decisions.

**2. GameAI is part of the simulation.** NPCs are not mannequins on animation loops. They live in the environment, hold local memory, have personalities and relationships, weigh risk, and make their own decisions. The AI Mayor governs District Zero. Mutants patrol territories, migrate when a range is depleted and defend their dens. Traders change tone based on your reputation. Players can't learn the patterns, because the patterns are rebuilt over and over.

**3. The player is part of the world.** You are not the center of the universe. You are an important, active participant who can drive huge change, but you are far from the only one. The world neither adapts to you nor waits for you.

**4. Life without an observer.** The world doesn't pause when you log off. This is a social property of an online world, not just a server requirement: while one person is offline, everyone else keeps living. Prices move with extraction and demand. Clans form alliances and fall apart. Districts grow or decay. You return to a changed world, not a save file.

**The consequence.** The world is not personalized to any individual player. There is no "wait for me," and no scene that freezes until the actor arrives. Live Anyway is an online game where nobody waits for you, and that is exactly why the world feels alive.

## Setting and World

**The post-apocalypse.** The world was born on the ruins of civilization after a global epidemic war. The plagues didn't just wipe out most of humanity. They remade the biosphere. Old infrastructure is gone, nature has taken everything back, and the bioweapons never went away: they mutated, adapted, and became a permanent part of the ecosystem. What's left of humanity lives in scattered, isolated enclaves, and between those islands of order lies the Wilds.

**The Wilds.** The Wilds are the uncontrolled, autonomous, lethal part of every District, and they cover **80 to 90 percent** of its area. They are not an empty wasteland. They are a living, hostile system packed with mutant dens and wandering zombies.

They are also the economic engine of the game. Unexplored space means untouched loot: abandoned megacities, mothballed military bases, secret labs. The Wilds tempt with wealth and kill for the smallest mistake.

**Four classes of threat.** Each kills by its own rules, and players have to learn all four.

| Threat | How it works |
| --- | --- |
| Weather and environment | Acid rain and toxic storms eat armor and gear. Anomalous hurricanes knock you down. Solar radiation scorches open ground. Nature acts on its own schedule. |
| Mutants, zombies and wildlife | Run by GameAI. They patrol, migrate, defend dens, and react instantly to heat or noise from humans. |
| Contamination | Invisible. Residual radiation zones and bioweapon sites can't be seen. You go by dosimeter clicks or the first symptoms of choking and sickness. |
| Other players | The least predictable threat. Corpses can't be looted, so there is no profit in murder, but people will still fight over ideology, influence, clan politics, revenge or a strategic chokepoint. You can't make a deal with a human once and for all. |

**Atmosphere.** The mood is dynamic and changes with where your character stands.

- **The Citadel (Ring 1).** Light, easy, safe. It's an island of calm in an ocean of chaos. You can exhale, trade, craft and talk with friends at the bar.
- **The Wilds (Ring 4).** Permanent, oppressive, primal dread. The sky can turn from clear to acid storm in a moment. Play becomes tactical movement from cover to cover with constant checks on radar and PDA. You can't just take a walk out here. Surviving the Wilds isn't luck. It's focus and readiness for the worst.

## GameAI Architecture

In Live Anyway, "GameAI" does not mean AI in the academic sense. We are not trying to build a mind or a model of human thought. GameAI is the **control layer of the simulation**: it takes server statistics and uses them to assemble, on the fly, the behavior of every managed entity in the world. That includes the AI Mayor, NPCs, mutants, zombies and wildlife.

It works in four layers. Each layer has its own owner, its own source of change, and its own limits.

**Layer 1: Invariant Core.** A fixed set of physical and logical laws set by the developers. It cannot be changed under any circumstances, because breaking it would break the simulation itself. Examples:

- An NPC trader cannot kill a player in the Citadel.
- The AI Mayor cannot repeal a law it issued without a reason recorded in the statistics.
- A mutant cannot leave its range against the logic of the ecosystem.
- A defense turret cannot fire at someone who broke no law.
- A zombie cannot become a player's ally or access social mechanics.

GameAI has no access to this layer. It runs on top of it and can never violate it. That answers the "what if the AI goes rogue?" question: the invariants sit outside its reach.

**Layer 2: Behavior Library.** A large, ever-growing set of scripts, reactions, patterns, lines, tones, priorities and logic fragments, written and expanded by the developers across the life of the project. Every element is simple, predictable and unremarkable alone: a trader's reaction to high reputation, a mutant patrol pattern, a Mayor's line when a charter rule is broken, a herd's migration algorithm. These are building blocks.

**Layer 3: Dynamic Composition.** This is where GameAI actually works. It receives a continuous stream of server data: who is online, where they are, what they're doing, what resources they hold, what jobs they've done, their reputation, their history with NPCs and the District, and what's happening in the world right now.

From that data, GameAI does not pick one script from the library. It **assembles behavior on the fly from many layers at once**. The same trader in the Citadel will talk differently to a player who has run Mayor contracts for years than to someone walking through the door for the first time. We didn't write a script for each of them. GameAI built two different compositions out of the same base elements.

This is the key difference from classic systems. In most games, players learn how an NPC works, find the patterns, write guides and optimize against frozen behavior. Here that path is closed. A guide recorded yesterday goes stale not because we shipped a patch, but because GameAI stopped using the combination of scripts the guide was built on.

**Layer 4: Bounded Modification.** The highest level of GameAI autonomy. Within limits the developers set, GameAI can modify Layer 2 elements as well as compose them: parameters, tone, reaction speed, priorities, fragment combinations. It cannot write a new script from scratch or leave its allowed corridor, but inside the corridor it moves freely.

- If the stats show players have stopped fearing acid rain, GameAI can raise its frequency.
- If traders have become predictable, it can shift tone and priority parameters.
- If mutants patrol too predictably, it can change the pattern mix.

**The developers set the corridor and GameAI moves inside it.** The corridor is what keeps the world playable and fair instead of arbitrary.

**What this buys us.** The central problem of any long-lived online world is predictability. The longer a game runs, the better players understand it, and the less surprise remains. Guides, wikis, videos and calculators gradually turn a living world into a solved problem. Live Anyway is built so that can't fully happen. While the developers keep expanding the library and GameAI keeps recomposing and tuning it, players never hit bottom. The world stays alive not because it is complex, but because it is constantly rebuilding itself.

## World Structure: The Hex Map

**An infinite honeycomb.** The map expands fractally and has no hard outer edge. All inhabited land is divided into regular hexagons, and each hex is a sovereign administrative unit called a **District**.

At global launch, only a few isolated **District Zeros** (starter incubators) are generated. They are not connected to each other, so you cannot travel from one Zero to another. **Your choice of starting District Zero at character creation is final.** As Communities claim new territory, empty hexes fill in and the world grows outward in every direction.

**What a District is.** Not a patch of land or a leveling zone, but a digital micro-state with its own laws, economy and social scene. Every District has four mandatory properties:

- **Hard physical borders.** The fixed geometry of one hex.
- **Political sovereignty.** There is always a legitimate owner: the AI Mayor in a District Zero, or a Community Head in a Private District. The owner sets internal rules and access rules for the safety Rings.
- **Economic autonomy.** Its own markets, warehouses, workshops, supply and demand, and logistics chains.
- **A social ecosystem.** Its own residents, guests, clan culture and history.

There are two types: **Zero Districts** (starter zones run by GameAI) and **Private Districts** (independent states created and run by players).

**One District, one server.** This is the project's main technical trade-off for scaling an online sandbox. We don't simulate billions of polygons on one mega-server, which would end in network collapse. Each District is an independent compute environment that loads only when a player crosses its border. This puts a natural cap on population:

- When a server hits its critical limit, outsiders (guests) can't enter and join a virtual queue, getting in only as slots free up.
- The limit does **not** apply to residents. A permanent **20 percent** of server capacity is reserved for registered citizens, guaranteeing instant access to their own home at any time.

The cap protects Districts from server crowding. It is also a strong incentive for clans to spread out and found new hex-states instead of piling into one place.

**Borders and transitions.** You move between servers by strict geographic rules, and only through **Transition Points** on the hexagon's edges. Each of the six sides connects directly to a specific neighbor. Walk to the edge you want and you arrive on that server.

If a District sits on the frontier and the hex beyond it hasn't been generated yet, the Transition Point stays inactive. The way is physically closed.

Technically, a transition means disconnecting from one server and loading another. The player sees a seamless travel cutscene (a road, a canyon, a pass) and then materializes at the edge of the new District, on the side they came from. **You never spawn in the center or in the Citadel.** You spawn in the Wilds on the periphery and have to fight your way across hostile land to reach the safe core.

Load flow: current District (Server A) -> cross Transition Point at the hex edge -> loading cutscene -> materialize at the edge of the neighboring District (Server B).

**Distance as a balancing force.** Distance is not an abstract number on a screen. It is the main physical and economic balancer of the universe.

*Movement.* Space has honest weight. To get from District 1 to District 3, you physically cross all of District 2, border to border, on foot or by vehicle. That takes serious time, preparation, fuel and provisions, and carries constant risk of permanent death in the Wilds. A target ten hexes away is a full, deadly expedition through a chain of different states with different laws.

*Regional economy.* Distance sets price, which produces natural geopolitics:

- The farther a District is from the raw-material producer, the longer and riskier the transport.
- The higher the risk and delivery time, the higher the markup on imports in the local market.
- Sky-high long-range import prices make local production the smart play in every District.

Neighboring Districts naturally form dense, mutually beneficial trade blocs and alliances. Distant territories either stay isolated and become fully self-sufficient, or specialize in rare endgame resources (uranium, for example) whose scarcity justifies any logistics cost.

## District Zero: The Starter Zone

**Role.** District Zero is the foundational starting point, the cradle and incubator for every new player. It is much larger than a standard Private District. Its job is onboarding: newcomers learn the basic laws of survival, make their first scouting runs, and meet the baseline threats.

To avoid killing an unprepared player in their first hour, the Wilds in a Zero are deliberately a little softer than on the outer frontier. It's an incubator, not a greenhouse. Danger is real but tuned to what starting gear can handle.

**The AI Mayor.** Everything in District Zero runs under a specialized macro-model of GameAI: the AI Mayor. The Mayor is an objective, cold, mathematically exact administrator. Its logic rests on absolute fairness and equality: no premium accounts, no pay-to-win boosts, no system favorites. But within that fairness, the Mayor is **very strict**. Everyone must follow the charter and the District's rules, and the smallest violation is punished with immediate exile or physical elimination.

*Production compromise.* All heavy industry in a Zero (plants, factories) belongs to the Mayor. To avoid server load from simulating every machine, these factories are **interactive set pieces**. The system calculates when finished goods and resources appear in District warehouses, imitating a full industrial cycle.

The Mayor's direct control and defense dome cover **Rings 1 and 2 only** (the city and the industrial outskirts). The rest of the hex isn't under its authority.

**The four safety Rings.** A Zero is divided radially into four zones with different safety metrics and rules of behavior.

| Ring | Name | Protection and rules |
| --- | --- | --- |
| 1 | **Citadel (City)** | Absolute safety. Crime is physically impossible. The interface blocks weapons at the code level. Total AI Mayor control. |
| 2 | **Outskirts / Industrial Zone** | Supervised, mostly safe. Weapons are allowed and you can shoot mutants. Killing players is forbidden: offenders are instantly eliminated by heavy stationary turrets. Lone zombies occasionally break through, keeping the tension real. |
| 3 | **Gray Zone** | Partial protection. The Mayor doesn't physically control this land but records crimes. A violator gets **Persona Non Grata** status: a permanent ban from Rings 1 and 2, enforced by turrets. Help from Communities is possible but not guaranteed. |
| 4 | **The Wilds** | Absolute chaos. No law, no system protection, no rules. Only might, firepower and personal luck. |

*Ring 1: Citadel.* A huge fortified megacity at the heart of the District: large residential blocks for newcomers, some factories, markets of every kind, and key NPCs who coordinate expeditions and hand out starter jobs. You physically cannot draw a weapon here.

*Ring 2: Outskirts.* The industrial belt, holding all of the Mayor's plants and raw-material bases. You can draw and fire (into the air or at mutants), because zombie groups and lone predators sometimes push through from the Wilds. The Mayor's turrets cover it densely but don't guarantee 100 percent safety. Killing or deliberately wounding another player here counts as treason.

*Ring 3: Gray Zone.* A buffer, not covered by the Mayor's defenses. The chaos of the Wilds starts here, but the Mayor keeps scanning by satellite and PDA. Any recorded attack on a human permanently brands the aggressor. They can never approach the Outskirts or Citadel gates without being shot by heavy guns.

*Ring 4: The Wilds.* The largest, most uncontrolled sector of the District. No codes, no Mayor rules, no morality.

**The market.** The Citadel runs a branching network of specialized markets: weapons and ammo, armor and clothing, provisions, medicine, and raw materials and components. Trade runs through **physical NPC vendors at counters**, not terminals, for immersion.

The core law of trade is fully dynamic prices and stock, driven by what the player society does:

- If players haul a given resource out of the Wilds and sell it, the market processes it, and the finished goods show up more often and at a discount.
- Hot items that sell out fast spike in price.
- Dead stock that sits for years drifts down to its price floor.

Private District markets work differently. There is no AI balancing of supply and demand there: owners set prices, taxes and stock by hand, based on their own interests and economy.

**Specialized Zeros.** At character creation, the player picks the **Specialization** of the District Zero they spawn in. It is final, and it defines the starting economic experience and early-game direction.

| Specialization | What you get |
| --- | --- |
| Metallurgy | Deep mines for ore. Metals and alloys are always in surplus and extremely cheap. Ideal for future gunsmiths and blacksmiths. |
| Agrarian | Huge abandoned greenhouse complexes and hydroponic farms that players can restart together. Cheap food, spirits and organic raw materials. |
| Energy | Built around surviving power plants. The cheapest electricity in the Citadel and Outskirts, speeding up energy-dependent processes and crafting. |
| Tech | Packed with workshops and labs. Steady access to cheap electronics, chips and advanced tools. |

**Leaving the nest.** District Zero is the parent's house, and you have to leave home to grow up. The ceiling inside the incubator is an experienced player with good loot. The Mayor's GameAI deliberately won't let players grow without limit in its jurisdiction, enforced by hard system constraints:

- Players are physically forbidden from building their own industrial plants in a Zero.
- Uranium and other top-tier endgame resources can't be mined there.
- You can't start generating a personal District or get full freedom inside the starter hex.

Life itself pushes strong players out, not by force but by the impossibility of developing further. They leave on their own, and three paths open up:

1. Move to an existing Private District and live and work for another clan.
2. Join a young Community and build a first Settlement on the edge of the Zero.
3. Push your own clan to the limit and trigger generation of a sovereign District of your own on the infinite map.

## Private Districts

**What it is.** A Private District is a sovereign hex map created by a Community (clan) once it reaches a certain level of technological and social capital. Unlike a Zero, it has no AI Mayor and no outside oversight. It's a blank slate of digital matter that belongs to real people. The Community can run heavy endgame industry, mine strategic resources, build large-scale infrastructure, and dictate the rules of physical and social presence by itself.

Flow: Settlement on the edge of a hex -> Head initiates -> Private District generates (hidden mode) -> Relay is built -> Sovereign, open state.

**How a new District is born.**

*1. Initiation and geographic anchoring.* Only the **Community Head** can trigger generation. The new hex spawns in the nearest free cell, on the side of the map where the Community's old Settlement stood. If the clan held a base on the eastern border of a Zero or adjacent Private District, their new sovereign District generates on the hex to the east.

*2. Procedural generation and transfer.* Once triggered, a procedural algorithm runs:

- Every Private District is the same hexagonal shape, with a **Citadel** automatically built at its geometric center.
- Terrain, mineral deposits, river beds and abandoned structures are generated randomly. No two Private Districts are alike.
- At creation, a total evacuation occurs: the Head and all members are teleported into the new Citadel. Members who were offline materialize inside it on their next login.
- **Capital transfer.** All workshops, warehouses, resources and buildings move seamlessly into the new Citadel's perimeter, keeping their tech levels.

*3. The old Settlement.* Right after the phase transition, the old base is marked as an **abandoned settlement** on the map. Buildings and walls stay in place as ownerless set pieces, open to looting or to be taken over by other Solos.

**Ownership and succession.** The Community Head is recognized by the system as the sole, absolute **Owner** of the District. That power can't be challenged by internal players or overridden by developer tooling. The Owner may appoint officers and deputies to manage resources when they're away, but no member can remove the Head through the interface. Transfer of power is protected by strict protocols:

- **Voluntary transfer.** The Head may hand the Community and the District to any clanmate at will.
- **Forced transfer (inheritance).** Happens only on the Head's permanent death. Leadership passes automatically to the heir the Head was **required to name in advance** in the PDA.

**Citadel and Outskirts: sovereign control.** The new Citadel is built in the same infrastructure state as the old Settlement at the moment of transition. Development continues from that point, with one big difference: the Community can now build full industrial facilities.

- **Inside the Citadel:** the City Hall (admin hub), markets, clan housing, and open building plots.
- **Industrial contour:** all heavy industry sits outside the city walls, in the Outskirts and across the rest of the District.
- **Access:** the Owner fully controls who may enter the server, sets any authorization rules, taxes and bans in the PDA. Who they want in comes in; who they don't, doesn't.
- **Defense:** Rings 1 and 2 start under strong automatic protection. The rest of the District (Gray Zone and Wilds) starts exposed, and can be gradually secured with a turret network if the Community can afford the compute and supply.

**Closed and open Districts: the Relay.** A Private District is born in **Closed mode**:

- The Community is locked inside the hex and can't leave.
- No outside player can physically enter the server.
- The District shows on the global map, but its interior, terrain and resources are hidden by fog of war.

This is a deliberate compromise that gives the Community time to prepare, fortify and install defenses. The Owner can stay closed as long as they like, within a developer-set maximum. If the Community neglects development and doesn't open the borders in time, the District is declared **failed (abandoned)**, wiped from memory, and the hex is released to another Community.

To open the District for trade and expansion, the Community must build a monumental structure in the Citadel: the **Relay**. It can be built on day one, but rushing is risky. A weak District without enough firepower will be captured and enslaved by stronger outside clans.

Once the Relay activates:

- The detailed topographic map opens to the whole world.
- All Transition Points on the hex borders become active.
- Outside players, traders and expeditions may enter the server.
- The Community can leave through Transition Points into neighboring hexes.

**This is irreversible.** The District is open forever. It cannot go back to Closed mode.

**Specialization.** The Head picks the District's Specialization at initiation, and it can never be changed. It leaves a permanent mark on the look of the world (more themed structures spawn) and grants the Community one fundamental bonus:

- **Resource specialization.** Example: *Metallurgy* generates a huge, unique uranium-rich mine required for endgame crafting.
- **Industrial specialization.** Example: *Energy* hands the Community a ready-to-run power plant or small nuclear plant of a scale players couldn't craft on their own at that stage.

**Abandonment and capture.** A Private District is an energy-hungry, demanding organism. It can't exist without constant human upkeep.

*Signs of decline.* If the Community stops logging in, the District dies fast. Industry and markets need a constant supply of raw materials and huge amounts of electricity. Fuel in a small nuclear plant is finite: players must mine or buy rare nuclear batteries and swap them into the reactor on time. Once upkeep stops, power fails, markets close, factories go quiet, and the Citadel's defense turrets lose power. Every passing trader and scout can see the decay at once.

*Capture mechanics.*

- **Capturing an abandoned District.** If a District is fully unpowered and its Community is deemed inactive, any outside Community may enter the Citadel, hack the City Hall, and claim the District with all its infrastructure.
- **Assaulting an active District.** You can try to take a living District, but with a Head and even a minimal garrison it is practically impossible. The Citadel's base defense is monumental, and developed industry lets the Owner blanket the land with turrets. Defenders only have to keep the reactor running and swap batteries.
- **Solo-abuse protection (technical limit).** Even if one brilliant solo player wipes out an entire clan and destroys every Citadel turret, they can't take the District. The capture function in City Hall is tied to social status: Solos simply have no capture option in their PDA. Only the legitimate Head of another Community can start a flag change.

## The Player

Flow: arrive as a stranger with no armor -> craft with your own personal skill -> buy Med Cards in the PDA for protection -> evacuate, or die permanently.

**Starting out.** The game has no "chosen one" with innate advantages. After character creation, you materialize in the Citadel of your chosen District Zero as an **absolute outsider**. Your starting kit is cut to the bone: one basic weapon, no armor, a critical shortage of food and basic meds. The fiction is that you were brought to the Citadel under escort from the far Wilds and left to figure out a harsh reality from a blank slate.

There is **no tutorial**. Our philosophy: if a world needs training wheels, it was badly designed. Environment, interfaces and material logic should be readable from the first seconds. Inside the Citadel you're protected, but knowing the Wilds begin just beyond the gates puts heavy psychological pressure on you from minute one.

**Exploration.** Your first steps happen in the safety of Ring 1 and the semi-protected Ring 2, where you take your first run. To build starter capital, the Citadel offers simple local quests from ordinary NPCs, built on courier logistics: carry a package or components to the Outskirts and back. These contracts earn your first currency for ammo, decent food and medicine.

Tools for exploring:

- **Global PDA.** Every agent has a pocket computer that shows, in real time, the topography of the current District and the entire open hex map.
- **Social exchange.** Newcomers can team up in person with veterans in Citadel bars, trading info and planning routes.
- **AI Mayor expeditions.** The Mayor regularly organizes large state expeditions deep into the Wilds. Newbies and veterans can team up under its banner for high-paying raid tasks. The fuel at this stage is pure curiosity and the pressure not to fall behind rival clans.

**Survival.** Survival rests on continuously meeting basic human needs: food, water and real sleep. Sleep and hydration are physical factors of the simulation, just like outside threats.

The Wilds' threats are ranked by how destructive they are:

1. **Weather and environment (highest threat).** Acid rain, hurricanes and solar radiation kill fastest and most surely. No amount of shooting skill saves you, only physical shelter.
2. **Mutants and zombies (medium).** GameAI predators following biological instinct. Deadly, but their logic can be read and avoided.
3. **Contamination (hidden).** Residual radiation, mutated plagues and poisoned water. They demand constant attention to your gauges and supplies.
4. **Other players (dynamic).** Since looting corpses is impossible, people stop being a threat by default. Whether other survivors become mortal danger or loyal allies is up to the players, through diplomacy, personal morals and clan politics.

**Progression: the player levels up, not the character.** Our central design rule: in this game, the person on the other side of the monitor is what you level.

The character has no artificial levels, no stat points, no passive skill trees. There is only a public **Action Record**: mutants killed, runs completed, depth reached across Districts. Other players can read it to judge how reliable you are.

There are no classes. What changes over time is not numbers on a sheet but the skill of the human controlling the character.

- **Crafting is a real skill.** To build an advanced device or weapon, you must actually know how to do it. Crafting is not pressing "Make" in a menu. It takes focus, attention and real dexterity from the person at the screen.
- **Failure is possible.** If you're careless or your hands slip, materials and time are lost for good and you get a defective result. The better you've truly learned the assembly process, the higher your personal chance of success.
- **Guides are player-made.** All guides and instructions are written and recorded by players from hands-on experience, not by the developers.

**Death and evacuation.** The cost of a mistake is maximal: **death is permanent**. A dead agent can't come back. You start over with a new character. But since there's no artificial leveling, an experienced player who loses a character returns as a master, minus the loot and gear.

The only barrier between a character and deletion is a timely call for medical help: **Med Evacuation**.

- **In a District Zero**, Med Evacuation is a mandatory core service of District infrastructure.
- **In a Private District**, it is the property of the owning Community. Whether other players can use it is up to the District's Head and rules.
- It is always a **paid** service. Price and currency can vary by District, terms and owner rules.

*How you pay.*

| Situation | Payment |
| --- | --- |
| District Zero | Buy a standard Med Card in the Citadel with ordinary in-game currency. |
| Private District (owning Community) | Paid in physical terms. The Med Center's evacuation drone needs special single-use **med-nuclear batteries** supplied by the clan. No batteries in the Med Center's reactor, no drones in the air. |
| Private District (outside guests) | Buy that District's Med Cards for in-game currency, before or after crossing, through the PDA. Each clan can set any price per evacuation on its territory, even an astronomical one. A Zero's Med Card cannot be used in a Private District. |

*How the insurance works.* If you hold an active, paid Med Card for the current District, permanent death is turned off. On taking lethal damage, your character just loses consciousness. A cutscene plays as a drone arrives, and your agent materializes on a bed in the Med Center of the current District's Citadel. **Nothing is lost on Med Evacuation**: all raid loot and your backpack are fully preserved.

You can buy any number of evacuations through the PDA, but the server's total is hard-capped by the number of nuclear batteries currently in the District's Med Center. If a clan stops supplying its hospital, Med Card sales and evacuation are physically blocked for everyone on the server.

**Permanent death.** Permanent death triggers automatically and instantly in one case only: when you lose consciousness and have no evacuations purchased for that District in your PDA.

You can call the drone manually through the PDA at any moment, even at full health (to escape being surrounded, for example). If your character collapses from wounds or toxins, the call is made automatically.

Without insurance, your character dies for good. Body, clothing, backpack and gathered loot are completely and irreversibly wiped from server memory. Only the character's unique nickname and lifetime achievements are permanently recorded in the game's global history and stat tables. No reset, no restore. You start over.

**Valhalla: the Pantheon of departed legends.**

*Status and rules.* Valhalla is a sacred, isolated museum map for the memory of the game's legends, where the ghosts of fallen legendary players stand. Only movement and exploration are allowed. Shooting, damage, crafting, building, inventory and trading are all disabled. Its single purpose is contemplating the history of the world and preserving players' legacies.

*Who becomes a ghost.* Only legendary players in the **global top 10** by statistics.

- **Trigger:** the final permanent death of a legend in the Wilds, or a deliberate, confirmed exit from the game through the deletion menu.
- The ghost keeps an exact copy of the player's best gear at the height of their glory.

*The Legend's Confession.* When a legend leaves (or after permanent death), moderators send them a form for recording voice lines. On top of standard triggers, the key element is the **Personal Story**.

| Audio pack slot | Description |
| --- | --- |
| Ambient | Quiet, looping muttering as the ghost wanders Valhalla. |
| Greeting | A short phrase when a living player walks up to the ghost. |
| Personal Story (the headline feature) | A voice recording of 1 to 5 minutes. The player tells their real story: a success, the memory of a major economic crisis, a betrayal by a friend, or the founding of their District. |

When a visitor approaches a ghost and presses "Listen to the story," the location's ambient fades and the legend's monologue plays with an "afterlife echo" filter.

*Manual moderation.* Because the Personal Story is a long recording of a real person's voice, it goes through mandatory manual moderation. Moderators check for gross violations, advertising and toxicity. Once approved, the story is stitched into the ghost permanently, and a unique visual cataclysm fires on the server to mark the new Legend entering Valhalla.

**Player specialization.** The game has no system-level character specializations. The human at the monitor has them. Whatever your hands learned through real play is what you're recognized for. With enough persistence, attention and focus, one person can learn every process in the universe, from delicate electronics repair to piloting heavy machinery. You fully define your character's look, face, clothing and build, creating a unique visual marker for yourself in the social space of the hex map.

## Societies and Civilization

In traditional virtual worlds, social structures are a UI layer: friend lists, clan chat and alliance tables sit on top of the map and never touch the physical world. In SNW, human society is a **symmetrical extension of the material world**. Social institutions form, scale, split and migrate under the same cause-and-effect laws that move water or spread fire.

**The scaling ladder.** Humanity in the simulation follows one evolutionary vector, from the entropy of individual survival to the order of a global civilization.

*1. Solo (starting entropy).* Every newcomer materializes in the Citadel as a Solo. Life is limited to basic needs and a minimal starting kit. The game doesn't force collectivization: you're free to stay a Solo forever, living in the Gray and Wild zones on personal skill, stealth and contract work for Mayor expeditions. But your influence on matter stays local. A Solo can reshape a tree or dig a trench, but can't build an industrial contour or redraw the map.

*2. Group (circle of trust).* The natural answer to the Wilds is the Group: an informal circle that crystallizes around shared runs, mutual cover and information swaps. A Group has **no legal weight** in the simulation, no shared property, no common power interface. It is purely a psychological phenomenon of trust between Solos, and a critical transitional stage where characters are tested, social roles get assigned, and the core of a future community forms.

*3. Settlement and Society (Community crystallization).* The move from nomadic survival to settled building is a qualitative leap: forming a **Society (Clan)**. Technically and logically it is inseparable from claiming a physical point on the map and founding a Settlement.

On the edges of Zero and Private Districts sit empty, abandoned infrastructure nodes. To claim one and turn it into a sovereign Community base, a player starts construction of a key system object: the **Frequency Antenna**.

Flow: Solo / Group -> find an empty node -> build a Frequency Antenna -> Society (Clan) crystallizes.

Once the Antenna activates, the system registers the Settlement as legitimate Community territory, and its founder automatically becomes **Head**. Inviting friends into the Settlement's perimeter is technically an initiation: joining the Society.

**Environmental safety.** An active Frequency Antenna fundamentally changes how you deal with the Wilds, splitting threats by how they perceive it:

- **Biological threats (mutants and animals).** The Antenna emits a directional high-frequency pulse that works like a powerful stun device. It physically suppresses the nervous system of Wilds fauna, triggering irresistible instinctive fear. The area around the Settlement is cleared of dens and patrols.
- **Anthropomorphic threats (zombies).** Zombies fill a specific small niche in the ecosystem. Their biology is human, so their central nervous system is immune to the Antenna's emissions. Zombies are deaf to wave-induced fear.

So the Antenna provides an energy dome but not an absolute solution. To defend a Settlement from zombie breakthroughs and raiders, the Community must build a material defensive contour: physical walls, covered fields of fire, and automatic turrets.

**The local accumulation strategy.** The classic mistake of young Communities is launching expansion too early. The architecture lets a Head trigger generation of a Private District almost immediately after the Antenna and minimal workshops. But a hard rule applies: **only the infrastructure physically built in the starting Settlement transfers to the new District.**

A Community that heads into deep hex-space with an undeveloped tier-1 industry will generate a Private District that is empty and weak. Isolated, with no outside support, it is headed for a severe crisis.

The evolutionarily correct strategy:

1. Settle in a Settlement inside District Zero.
2. Use abundant resources, the stable AI market of the Citadel and the safety of the incubator for deep development.
3. Build efficient workshops and bank technological capital and surplus currency.
4. Only at peak local development, make the transition and deploy the Private District in its best starting state.

**Splits and migration.** Society in SNW is fluid, unstable matter. Large Communities inevitably develop ideological, economic or leadership rifts. The system doesn't suppress this artificially, and offers a tool: **Splitting**.

If part of a Society disagrees with the Head's policy, they can run a split. The Head and loyal members stay in place and keep control of the current District, the Citadel and its balance. The leavers can either scatter as Solos or migrate collectively.

How a material split works:

- Community law lets members move freely across the map and build Frequency Antennas on any free node, inside their own District or on outside territory.
- By itself, a clan member building an Antenna does **not** create an autonomous Society (unlike a Solo doing the same).
- But when a split has matured inside the Community, the leaving faction's leader builds an Antenna at the map edge and sends out a call to unite through the interface.
- The breakaway players confirm the move into the new local perimeter. The system records the birth of a new Community with its elected internal Head.

Splits and migration need no permission from administrators or developers. They are a natural expression of social dynamics, reshaping the map of human presence.

**Civilization: cultural expansion.** The peak of SNW's vertical gameplay is moving from running an isolated Private District to building a **Civilization**. When a Community has fully developed its District, pushed industry to its peak and filled the Citadel with endgame resources, its geopolitical role changes. The clan stops being "survivors" and becomes **Architects of a New World**.

Then the fractal-similarity mechanic starts:

Flow: successful open District -> influx of newcomers -> new Communities form inside it -> help with expansion -> a network of friendly sister-Districts.

- District owners create attractive, fair laws and set an affordable price for Med Evacuation, turning their territory into a thriving hub for newcomers.
- Incoming players and young Groups see the model working and found their starter Settlements inside the District.
- When those young Communities are ready to create their own Private Districts, the established patron clan gives material and logistical help to expand into neighboring empty hexes.
- Young Communities raised inside this ecosystem will, with roughly 99 percent likelihood, absorb the starter District's laws, culture and norms.

Through patronage, strong clans build belts of neighborly, mentally and economically similar Districts. This is how a macro-civilization is born in SNW: a single ideological and economic network of servers, shaped not by the game's creators but by the will, culture and intelligence of the players.

**Population structure.** Flow: total server capacity -> 20% resident quota (queue-free entry) + 80% visitor slots (queue-based entry).

Every District server splits its population into two categories with very different legal and technical status.

- **Residents.** The owning Community (the main clan of the Citadel), plus every outside Community that has managed to anchor on the periphery of the hex and found local Settlements with Frequency Antennas. Anyone with registered property and an active base inside the hex is officially a Resident.
- **Visitors (guests).** Everyone else: Solos, transit trade caravans, mercenaries, spies, explorers and tourists. They have no permanent base on this server and are only there temporarily.

Server capacity is split **20 percent for Residents and 80 percent for Visitors** (final ratio adjustable by developers during optimization).

- **Resident reserve.** The server code reserves these seats, guaranteeing Residents permanent, unobstructed, instant entry to their District at any time of day or night.
- **Visitor queue.** Guest slots are strictly limited. If a District is popular and the Visitor cap is full, new arrivals at the Transition Points go into a virtual **Queue**. They load in as other outside players leave through the opposite Transition Points or log off.

**Society limits and sovereign enforcement.** As established, the District Owner has absolute authority within their territory, including the right to ban any new Settlements and any other Communities in their hex. Following the realism principle, this ban is **not** enforced by switching off interface buttons. There's no system message saying "You are not allowed to build here."

- Even under the strictest ban, any outside player or Group can physically walk to the edge of the map and, against the law, build a Frequency Antenna and found an illegal Settlement.
- At that moment, game mechanics step aside for pure human politics and emergent consequences.
- The Owner's response isn't coded. It is unique to the situation. They can ignore a guerrilla base that pays an unofficial tax, negotiate and legalize it, or, if the clan is hostile, respond with force: refuse to sell the District's Med Cards (turning any knockout into permanent death) and send a punitive expedition from the Citadel to blow up the illegal Antenna and level the Settlement.

**Why limits drive expansion.** Hard caps on server population and political pressure from strong District owners are the key evolutionary lever pushing the SNW world to grow without end. In classic MMOs, players clump onto one server and turn it into an overcrowded digital camp, which kills the economy and the hardware. Live Anyway solves this with systemic motivation:

- Young Communities feel cramped in someone else's District because of queues for their guests and limited quotas.
- Building on the outskirts of developed hexes carries a huge risk of destruction by the District's owners.
- The scarcity of free slots and the laws of strong clans push players out to the frontier instead of crowding one map.

To get guaranteed queue-free access, a personal Citadel and the right to write their own laws, Communities take the resources they built up in District Zero and head to the edge of the inhabited world, triggering generation of new Private Districts. The limits don't punish players. They are the strongest incentive to expand, getting human civilization to fill the infinite map one step at a time.

## Economy and Crafting

Flow: resource extraction (time + effort) -> District Warehouse -> production (bench to factory) -> market (AI-driven pricing, or the Owner's will).

**Resources and extraction.** The raw-material model is built on a simple twist: resources are **unlimited in quantity but strictly limited in availability.** Raw materials are mineral ores (iron, copper, sulfur, endgame uranium), water and timber. We don't do the unrealistic "clear-cut the forest" or "drain the mine in a day" loop. Mines and sawmills hold an inexhaustible supply that could feed a civilization for decades, but extracting it takes huge amounts of time, tactical planning and real physical effort.

Extraction is tied to the physicality of the world:

- Mining iron ore means physically standing in a deep mine, digging out layers by hand, and then hauling the heavy raw ore to a foundry by hand.
- Every resource has its own labor-intensive extraction cycle, which prevents raw-material oversupply on the market and protects the economy from inflation.
- **Specialization factor.** Specialized Zero or Private Districts (say, a Metallurgy one) get one concrete bonus: that profile resource is much easier and faster to extract there. All other resources follow the standard, very hard protocol.

**Production.** The production cycle is linear and logical, staged from rough primary processing to final assembly of high-tech goods. Example chain:

1. **Primary stage.** Iron ore hauled in from the mine goes to a foundry, where heat processes smelt it into ingots and blanks.
2. **Intermediate stage.** The refined iron goes to a gun shop, where a barrel is turned.
3. **Final stage.** In assembly workshops, the barrel, a wooden stock and metal mechanisms combine into a finished rifle.

**Four crafting tiers.** Depth and automation of crafting are tied directly to the tech level of the Community's infrastructure.

| Tier | What it does |
| --- | --- |
| 1. Hand crafting | Available anywhere from the PDA interface. Simple, light items: torches, crude bandages, stakes. No stationary equipment, but limited to basic primitives. |
| 2. Workbench | The first stationary step. Complex, multi-part items and starter-tier weapons. Extremely labor-intensive: it demands maximum concentration, time and dexterity from the person at the screen. |
| 3. Workshop | A professional infrastructure node that automates complex items. Builds high-tech items many times faster than a bench and sharply cuts the manual labor required. |
| 4. Factory | The industrial endgame, available only inside Private Districts (Zero factories are Mayor set pieces). Runs conveyor-style batch production and saves the Community huge amounts of time and effort. With a steady raw-material supply in the warehouse, a factory runs fully autonomously, stamping out batch after batch until the stock runs out or the warehouse fills. |

**Storage.** Every hex District has a monumental logistics node: the **Citadel Warehouse**, with strict separation of access rights.

- **Owner Community warehouse.** The single digital and physical base of the clan holding the District. Everything mined, bought or produced by the Community flows here. The main convenience: the Head and officers never carry resources crate to crate. Raw materials and finished goods are delivered automatically and instantly from the Warehouse to factory lines or to the shelves of clan-run markets.
- **Visitor warehouse (lockers).** An isolated sector for outside players and Solos. Any traveler can rent a personal locker. It's an absolutely safe area, protected by AI code or the Community's guns. Nobody, including the District Owner, can remove or even see an outsider's goods. The locker's contents are physically generated and displayed only to its owner.

**Markets: supply, demand and dynamic prices.** Trade happens inside Citadels and larger Settlements. The market economy runs in two completely different modes, depending on the District's status.

*District Zero economy (run by the Mayor's GameAI).* Markets in the starter hex are fully controlled by AI algorithms. They're split by strict category (weapons and ammo, clothing and armor, food and medicine), and trade runs only through physical NPC vendors at counters.

- **Supply and demand.** Prices are strictly dynamic. In a hard shortage (players buying up all the ammo), the price of the scarce item spikes. If an item doesn't sell and sits in a vendor's stock for months, the AI steadily marks it down to a floor.
- **Dynamic assortment.** Mayor shops never carry a stable, complete catalog of weapons or armor. The range is shaped directly by player actions. The more of a given resource (say copper and sulfur) players mine in the Wilds and sell to NPC vendors, the more often finished goods built from it (such as quality ammo) appear on shelves at a discount.

*Private District economy (pure player capitalism).* Inside a Community's sovereign hex, the AI Mayor's authority ends. In the Citadels and Settlements of private servers, the players who own the world run all markets by hand.

- Trade, barter and distribution follow whatever rules the Community Head sets.
- The clan shapes the assortment from what its factories can produce.
- Owners manually set any prices on weapons, food and Med Evacuation cards, with full control of the financial flows on their territory. Nobody can contest their economic will. A District can be a free trade republic with minimal prices or a hard, closed dictatorship.

## Trade and Logistics

Trade runs on three levels: free barter between players, the Head's will inside Communities, and a contract exchange between Districts. Delivery follows the shortest path, unless a blockade forces a detour.

**Player to player (micro level).** Solos get full commercial freedom. At this level, trade is a relationship between free people with no system or clan obligations.

- Players may buy, sell or swap any material goods, components and loot at their own discretion.
- Free barter (item for item) and trade for in-game currency are both allowed.
- The game has **no built-in real-money trading** and doesn't make it part of gameplay. Any outside deals between players sit outside the in-game economy and are governed by platform rules and applicable law.

**Community to Community (meso level).** Commercial relations between Communities follow a corporate hierarchy. Unlike free Solos, rank-and-file members are tightly subordinate to the chain of command.

- All external clan trade is controlled personally by the Community Head.
- Rank-and-file members may buy or sell raw materials and finished goods only in the volumes, directions and currency the Head has approved in the PDA.
- The Community acts on the market as a single economic agent, pooling resources in the shared Settlement Warehouse.

**District to District (macro level) and Contracts.** The top tier of the simulation turns Live Anyway into a large-scale geopolitical exchange. Trade between sovereign hex-servers is direct interstate relations between District Owners.

The PDA gives every District Head a specialized **Exchange Terminal**. The Owner sees, in real time, trade offers (supply and demand for raw materials and goods) from every other open District on the infinite hex map. Trade runs on in-game currency or barter, through direct diplomatic negotiation between District leaders.

*The macro-logistics trade-off.* District Heads and their Communities never have to move millions of tons of contract-bought raw materials by hand across hex borders. Once two Owners agree and sign a digital **Supply Contract** in the PDA, the system takes over logistics. Purchased goods are automatically shipped from the seller District's Warehouse and flow in a steady, continuous stream straight into the buyer District's Warehouse.

**Delivery, distance and transit time.** Automatic macro-delivery between District warehouses obeys hard physical and geographic laws, driven by **Distance**. Transit time comes from a strict system formula:

- **Base metric (X):** the fixed time (in hours or minutes) to automatically deliver a batch between two directly adjacent Districts (sharing a physical border).
- **Long-range formula:** if the seller District is further away, delivery time grows in proportion to distance.

```latex
T = X \cdot N
```

where N is the exact number of hex Districts the cargo has to physically cross on its way to the destination.

**Regional economy and trade networks (geopolitics).** Because delivery time and reliability depend on geography, Districts inevitably form trade networks and regional economies.

- **Neighbor automation.** Owners of bordering Districts can fully automate buy-sell cycles for raw materials. This creates sturdy, stable regional markets with near-instant delivery, turning a cluster of hexes into one thriving economic bloc.
- **Shortest-path law.** For long-range shipments, the system automatically routes cargo along the shortest geographic vector through the chain of intermediate hexes.
- **Economic blockade as a weapon.** If a District on the shortest path has officially banned transit or trade with the destination District, the routing algorithm hits a barrier and has to recalculate, sending cargo the long way around through neutral hexes. A detour raises the number of Districts crossed (N), which by the formula sharply stretches delivery time and drives up the final price of goods. One aggressive clan can strangle a neighbor's economy just by closing its borders to transit caravans, which opens up endless room for real geopolitics, intrigue and economic warfare.

## Politics, Diplomacy and Conflict

Flow: law issued in the PDA -> no system-level bans -> physical enforcement by the Community -> emergent politics.

**Laws and District rules.** The political structure of SNW rests on absolute legislative sovereignty. Laws on each hex are set by its Owner.

- **In a District Zero:** the base legal code and safety charter are hard-coded by the developers (an absolute weapons block in the Citadel, turret elimination for murder in the Outskirts).
- **In a Private District:** the Head of the founding Community has absolute right to set any rules and codes. In the PDA, an Owner can issue decrees such as:
  - A total ban on other Communities and illegal Settlements.
  - A ban on carrying or using certain weapon types.
  - Economic embargoes and bans on specific categories of goods.
  - Restricted outsider access to technological infrastructure, workbenches and warehouses.
  - Emergency Med Evacuation for Community members only.

**Enforcement: force, not magic.** This is the central design compromise and a triumph of emergence in SNW: **the system never turns the Head's laws into magic physical prohibitions.**

If an Owner bans outside bases, the violator never sees a "Building prohibited by the system" popup. The code doesn't block the crafting mechanic. Any illegal migrant or hostile group can walk deep into the Wilds of someone else's District and try to set up a hidden Settlement against the ruler's will.

That's where real politics begins: the law exists on paper (in the PDA), and enforcing it becomes the Community's own job. A Head's absolute legislative power does not equal automatic control of physical space.

- If the Community is strong, with many patrols, vehicles and a dense network of Frequency Antennas and turrets, it will physically find and destroy violators.
- If the Community is weak and can't control 90 percent of its giant hex, the ban is worthless. Illegal bases, guerrilla camps and Solo black markets will bloom on the District's edges. A PDA ban does not equal physical impossibility.

**Diplomacy and alliances.** Communication channels are split strictly along the social hierarchy.

- **Macro-diplomacy (interstate level).** The PDA includes a closed, isolated diplomatic chat. Only legitimate District Heads have access. Hidden from rank-and-file players, this is where global negotiations happen, supply contracts are signed, action against common threats is coordinated, and Official Alliances between Districts are formed.
- **Micro-diplomacy (social level).** Alliances and pacts between ordinary Solos or Groups have no digital representation in the PDA. They are pure verbal trust agreements between real people. A person's word weighs more than a line of code. You can keep it for years, or break it with a knife in the back on the next run.

**Conflicts.** The conflict spectrum in SNW scales from local scuffles to full wars of annihilation.

- **Player vs. player.** Everyday clashes between Solos in the Gray and Wild zones. They can flare up spontaneously, with a clear cause (splitting rare loot at an abandoned bunker) or no cause at all, as a product of human nature, fear or personal dislike.
- **District vs. District.** Large-scale geopolitical standoffs between Communities, run through economic and military tools: hard trade embargoes, blocking transit routes for a neighbor's logistics network, a full ban on entry for a hostile clan's members, and covert sabotage runs to cut power at enemy nuclear reactors and blow up Frequency Antennas.

**Reputation and Persona Non Grata.** Feedback and social control form an open reputation map of the world.

*District Reputation.* Every player who visits a hex can leave a detailed review of the District through their PDA, rating safety, how reasonable the Owner's laws are, market prices and Med Card costs. A public **District Reputation** is built transparently from these ratings. Districts with strong reputations attract traders and newcomers and speed up their clan's economic growth. Districts known as "chaos zones" or "pirate coves" quickly lose traffic and decline.

*Persona Non Grata.* A District-owning Community can officially declare a specific player, or a whole hostile Society, Persona Non Grata and ban their legal entry. In keeping with SNW's material principle, this status does **not** mechanically lock the Transition Point. An exiled player can still cross the hex border and load the server. But the PDA instantly alerts the Owners that the offender has crossed the perimeter, and the status automatically switches all Outskirts and Citadel defense turrets to lethal fire. The exile becomes a living target, and staying in the District becomes an extreme survival test.

## Communication and the PDA

Flow: local contact with live auto-translation -> global PDA as an indestructible hub -> District-to-District macro interface.

**In-game chat and player communication.** Communication in Live Anyway is tied to physical distance between characters and to social circles.

- **Proximity (near circle).** When two agents get close in a hex, the system opens direct local chat. Being in line of sight is enough to start talking. It simulates natural face-to-face conversation with no remote devices.
- **Remote (social groups).** Through the PDA, players get classic text channels and internal forums, structured by access level: a global chat for the current location, a private Community channel, and a private chat with an approved friends list.

**Communication between Districts.** Macro-communication between sovereign hexes sits outside ordinary game chat. District Owners coordinate through a dedicated **District Control Panel** in the PDA. It connects server leaders directly, so they can resolve transit questions, declare embargoes and agree macro-contracts on the exchange without wading through general chat noise.

**Automatic translation and language support.** Live Anyway is one global ecosystem that erases the borders between real countries. To make multinational play seamless, the game integrates instant end-to-end auto-translation.

- Every text message in private, local, clan and cross-server chats is automatically translated into the language each player has selected in their client settings.
- *Example:* a Russian-speaking player types "Привет" in local chat, and a gamer from India standing nearby instantly sees it in Hindi on their screen. When the Indian player replies in Hindi, the system turns it into Russian text.
- It happens invisibly, at the speed of in-game ping. Players may not even realize their conversation partner is writing in another language.
- The simulation core is built with native support for most of the world's major languages, turning the hex map into a global social experiment without language barriers.

**The PDA and information system.** The Personal Digital Assistant (PDA) is the main, fundamental tool a human uses to interact with the living digital reality.

Given the hardcore nature of the game (where permanent death wipes all gear and your backpack), the PDA has a special technical status: **it can't be lost, broken, smashed or stolen.** It is an inalienable, virtually stitched part of the agent's interface. It stays with you anywhere in the infinite world, in any circumstances and across rebirths.

Its structure includes:

| Module | Function |
| --- | --- |
| Interactive map | Shows the topography of the current District and the whole global hex grid. Interactive: you can see every law, rule, tax and marker that District Owners have officially set for their territories. |
| Remote communication hub | Secure channels for coordinating Communities and talking to friends over very long distances. |
| Personal stats archive | A full log of your lifetime achievements (threats destroyed, depth of runs, successful crafts), available to show other players. |
| Med Evacuation interface | Lets you instantly buy insurance Med Cards for any open Private District before you cross its physical borders. |

## Survival and Cooperation

Flow: solo survival (maximum hardcore) -> chance meeting (coordination) -> a tight Group (a real shot at success) -> titanic effort (cleansing a District).

**Environmental danger and the plasticity of chaos.** On the surface, the threat list looks standard for a hardcore survival sim. SNW adds one key refinement: **environmental danger is not a frozen constant. The world is plastic and can be put in order.**

At the start, the Wilds (Ring 4) teem with mutant hordes and zombie swarms, and the sky constantly threatens toxic precipitation. But the District-owning Community can do titanic work. Through huge time investment and coordinated effort, players can:

- Clear mutant nests step by step.
- Build a network of Frequency Antennas and defense turrets.
- Build sealed shelters from acid rain and solar radiation across the whole hex.

Technically, this means a Community can push the border of Ring 2 (Outskirts) out to the physical edge of the hex. A Wild land can become a fully safe, civilized space where walking from one edge of the hex to the other is totally comfortable. But behind every meter of that safety stands a real story of struggle, kilowatts of power and the sweat of hundreds of living people.

**Expeditions.** Raids into unexplored land are the main engine of technological development. Expeditions form inside a Community to resupply warehouses centrally, and also organically between complete strangers.

The main goal of any expedition is finding and extracting scarce endgame raw materials. The physics of the Wilds are built so that crossing them alone, hauling a heavy load of ore, is practically impossible.

So SNW's social engineering breaks the toxic survival-game mold: a chance meeting of two Solos in the Wilds will, with **95 percent probability**, lead to instant coordination and mutual help instead of hostility. Fear of a merciless environment outweighs aggression. People instantly understand that standing back to back and covering each other is the only way to get the haul back to the Citadel alive.

**Solo survival (the ultimate extreme).** Live Anyway has **no difficulty sliders or settings** in the menu. The world is equally harsh to everyone. Instead of artificial crutches, difficulty is set by the person's own sovereign choice. Choosing the Solo path **is** the hidden "Maximum Hardcore" mode.

A Solo deliberately gives up clan warehouses, automated factories and a Community's free evacuation drones. Every run is balanced on the edge of permanent death. It's a path for mental extremists, demanding perfect knowledge of topography, anomaly timings and the habits of GameAI mutants. A Solo can survive, but autonomy costs constant resource scarcity and huge mental strain.

**Group survival and coordination.** Joining a Group automatically improves a human's odds of success, but it makes hard social demands. It isn't enough to gather four people and press a "Raid" button.

A Group in SNW is not a sum of avatars. It is a single combat organism. People have to physically get used to each other: read gestures, divide fields of fire, and understand without words who holds the perimeter and who packs the loot. If the team falls into discoordination, panic or selfishness, the whole Group's chance of evacuating drops toward zero. The Wilds punish a lack of cohesion immediately.

**Participant specialization.** As established, the character is a blank slate with no artificial classes (no "medic," "assault" or "engineer"). The living people at the monitors hold the specializations. Inside a seasoned team, specialization emerges naturally from experience, habits and personal talents:

- A player with great reflexes and ice-cold nerves takes the role of covering frontline.
- A person with strong topographic memory and a feel for anomalies becomes the navigator-scout.
- A player who has mastered the "dexterity" mechanics of crafting is recognized as the team's technician, repairing gear on a knee in a field shelter.

Everyone becomes a specialist in what they can actually do better than others.

**Why cooperation becomes a natural necessity.** The Wilds are not a stroll with the occasional monster. They are an aggressive hell. Picture the worst case: an endless zombie horde bears down on the team, ammo is nearly gone, GameAI mutants are flanking on the scent of blood, and the PDA is screaming a warning about an acid rain that will turn your armor to dust in three minutes.

A lone player has no chance. They physically don't have enough hands to shoot, reload, treat a wound and board up the door of an abandoned bunker at once.

The coordinated, rehearsed actions of a tight team are the only mathematical chance to survive. In Live Anyway, cooperation is not a moral choice, it is a hard survival need. The world is built so that selfishness leads to permanent character deletion, while collective intelligence, trust and mutual aid let humanity tame wild matter, build new Districts and rebuild civilization on the ruins of a dead Earth.

## Emergent History and Long-Term Engagement

Flow: Settlement (memory crystallizes) -> Private District (growing capability) -> split and crisis -> regional civilizations.

**How the world's history is written.** SNW's history is never written by scriptwriters. It begins the moment a player learns, through their own experience, that cooperation is absolutely necessary. That realization becomes action: they look for reliable friends, test them on raids, and build a circle of trust.

To lock the alliance into the physical world, the Group travels to the far edge of the map, deep into dangerous Wilds. They find an abandoned infrastructure node, set a perimeter and build a Frequency Antenna. A wave pulse clears the land of mutant nests and gives people their first sovereign dome of safety. From human trust fused with the physical structure of the Antenna, a Settlement is born.

**Growth of societies and trade centers.** A Settlement is a living magnet. The better a Community builds out its node, the more turrets, workshops and warm shelters it raises, and the harder it pulls in new independent Solos and Groups. The society grows exponentially, accumulating resources and capital.

When a Community hits the limit of local growth in the Zero "incubator," it triggers generation of a Private District and makes a mass migration. The old base instantly becomes abandoned ruins. But for the Community, it stays forever an **Island of Memory**. Months of real time later, passing those walls on distant raids, veterans will recall laying the first foundation, beating back night assaults by a horde, and splitting the last sip of clean water. The environment gains a mental past.

If a Private District is run by wise leaders with fair taxes and open borders, it quickly becomes a **Global Trade Center** of its region. While District Zero strangles player development with architectural limits, a successful Private District offers unlimited room for endgame resource trade and heavy industry, tying together the logistics chains of dozens of neighboring servers.

**Industrial regions, splits and economic crises.** The flip side of success is the unavoidable crisis of growth and the fluidity of human nature. When a District fills up with people and the Citadel's factories begin to burn through terawatts, the Society faces hard challenges:

- **Splits and migration.** A landscape or ideological crisis inevitably brews inside a huge clan. Part of the players may flatly disagree with the District Owner's economic or foreign policy, or the Society simply gets cramped inside one hex. The dissenting faction splits off: it moves to a distant frontier, builds an alternative Antenna and founds a sovereign clan, or migrates entirely to distant Districts and joins other cultural communities.
- **Economic crises.** An industrial region is viable only while its nuclear plant reactors are fueled. If the Community is mired in infighting and misses the deadline for buying nuclear batteries, or a hostile neighbor blocks transit Districts with an embargo and cuts off deliveries of sulfur and uranium, collapse follows. Industry freezes, turrets lose power and markets close. A Community crisis instantly turns a once-great District into a vulnerable, fading **ghost server**, open for assault and looting by outside forces. The whole hex map reacts to the shortage with a shift in prices.

**Regional civilizations.** As the map fills with Private Districts, the chaotic scatter of servers inevitably self-organizes into **Regional Civilizations**: macro-alliances of several hexes bound together not by the game's code but by shared economic interests, similar laws and culture.

Civilization is born through patronage and fractal similarity:

- A large, economically stable lead District takes young Communities developing in its territory under its wing.
- When those Communities are ready to create their own Private Districts, the patron District helps with resources, sending caravans of metal and electronics to neighboring empty hexes.
- The young states, launched by the leader, natively copy its internal charter, access rules, criminal code and Med Evacuation price policy.
- Around the founding District forms a powerful allied belt of ideologically and mentally friendly server-states. They automate raw-material trade on the exchange, build joint defense strategies, and together dictate terms to neighboring conglomerates, forming a unique sovereign geopolitical bloc on the face of digital reality.

**History created by the players.** In most traditional online games, world lore is static. Written by writers in a developer's office, packed into quest text, and identical for each of millions of players, it is a finished product the player merely consumes as a passive viewer.

In SNW: Live Anyway, history is a continuous, nonlinear process of physical change in matter and society, created exclusively by the players' own hands.

There are no frozen backdrops here. Every destroyed Citadel wall, every road laid through the Wilds, every river dried up by a dam, and every District wiped off the map by a Community's energy crisis are honest scars recorded by the server on the body of the world. Years into the project, the hex map will be a monumental memorial to human decisions, victories, betrayals and alliances.

New players will study this universe's lore not from invented books but from the real history of servers. They'll pass down by word of mouth the chronicles of the great blockade of District No. 5's trade routes, recall the name of the Head who first built a Regional Civilization on the eastern frontier, and explore the ruins of abandoned Settlements that remember the first days of settling this world. The game stops being an amusement ride. It becomes an autonomous digital reality that writes its own chronicle every second, through the will, intelligence and actions of living people.

**Why players stay.** The main problem of modern sandboxes and survival sims is **"end-game syndrome."** Once a player or clan has top gear, a maxed-out base and has killed the bosses, the game turns to routine. Then comes a wipe, and everything starts over.

Live Anyway removes this dead end at the architecture level. Players stay because the ceiling of their development keeps moving, opening whole new levels of gameplay. The game changes genre for the user step by step:

1. It starts as hardcore **Survival** (the Solo).
2. It grows into tactical **Co-op** (Group and Settlement).
3. It turns into a social **MMO strategy** (Society and Clan).
4. It reaches global **Geopolitics** (District ownership and Civilization).

Each step opens a new scale of influence over matter and society. A player stays not for abstract numbers or virtual gold, but to hold and expand their real influence on a living digital world.

**The milestones of ownership.**

- **Owning a Settlement.** The first step toward taming chaos: material proof that a Group could stand against a hostile environment. Building a Frequency Antenna turns a patch of deadly wasteland into a livable home. It becomes a foothold, a supply base and a personal fortress where every machine, turret and wall was built by your own hands and your friends'. It's also your first taste of responsibility: now the Community must defend its perimeter from zombies and keep the power on.
- **Owning a Society.** When a Settlement grows, it crystallizes into a Society (Clan). That means social weight and recognition within the simulation. It's the move from shared survival to division of labor: an internal hierarchy emerges with its own crafting masters, tactical assault specialists and logisticians. The Society starts setting terms on the market, accumulating capital in the shared warehouse, and preparing for the next big technological leap: expansion onto new hex servers. The leader becomes a full political player.
- **Owning a District.** The peak of a player's will in SNW: a sovereign digital state on the infinite hex map. The Owner no longer answers to developer rules or the AI Mayor. They become the source of law. They can set taxes alone, regulate exchange contracts, declare embargoes, execute violators via turrets and close access to whole hostile clans by branding them Persona Non Grata. But it's also a titanic burden: the Owner must keep citizens safe, supply the Med Center with rare nuclear batteries for evacuation drones, and defend the Citadel from espionage and military intervention by rivals. If the Head fails, residents abandon the state, reactors go dark, and the District is wiped or captured.

**Reputation and legacy.** In a world where matter remembers everything, Reputation and Legacy carry physical weight. A player's character can die permanently and lose all gear, but their name, nickname and record of achievements are stitched into the server chronicle forever.

- **District legacy.** Districts that held order for years, where honest trade flourished and Med Evacuation was affordable, are remembered by the community forever as great cultural centers.
- **Leader reputation.** A player who builds a successful Regional Civilization leaves a legacy that outlives generations of their characters. Their laws get copied, their name is respected by alliances and feared by enemies.
- **Valhalla.** The highest recognition of a player's reputation and legacy is being immortalized in Valhalla. Reaching the Pantheon's top 10 is the main intangible goal for veterans of the SNW world.

**The world one year after launch.** A year after servers start, SNW: Live Anyway becomes a complex, self-regulating geopolitical map no one could have designed by hand in a studio.

- Giant, player-developed industrial and agrarian regions grow around stable District Zeros.
- The hex map is covered with a network of Private Districts, bound by strong economic contracts and automated trade routes.
- Giant Districts emerge that monopolize uranium extraction, and independent Districts that act as banks.
- The Wilds landscape in inhabited hexes is completely transformed: players cut safe corridors, build hundreds of shelters and outposts, and physically push the chaos of mutants out to distant frontiers.
- Beside thriving trade republics lie grim, unpowered **ghost servers**: the ruins of civilizations built by clans who quit the game or fell to economic blockades. The world becomes truly alive and uneven.

**Several years in.** After years of continuous simulation, the project goes far beyond "online game" and becomes a full, durable, autonomous digital reality.

The world accumulates a huge layer of its own unique history made by millions of living people. Stable macro-civilizations take shape, each with its own cultural codes, political blocs and inter-server laws. Founding Districts are seen by newcomers as "ancient empires" with infrastructure developed to its absolute limit.

As technology advances and more capable neural-network models are gradually connected, the GameAI of Districts and the AI Mayor will understand the context of human relationships even better and produce subtler social and economic reactions from the environment. Whole generations of players will enter SNW not for shooting monsters, but for complex diplomacy, management of macro-economic flows, scientific study of the simulation of matter, or simply to live in a world where every person has an honest shot at becoming the Creator of a new civilization.

## Player Journey Example: Grom's Story

Flow: Solo (a fight for seconds) -> Group (a shared campfire) -> Society (the factory conveyor) -> Civilization (the birth of an empire).

The following is an illustrative walk through the vertical arc, told as one player's story.

**The Solo: a survival chronicle on the frontier.** A player named **Grom** materialized in the Citadel of District Zero with a basic pistol and a pack of crackers. For the first three days he never left the safe Outskirts (Ring 2), running the AI Mayor's simplest contracts, hauling parts. With enough earned for provisions and a first Med Card, curiosity got the better of him and he crossed into the Gray Zone, heading for the Wilds.

Acid rain caught him in the Gray lands. With no armor, he ducked into a half-collapsed concrete culvert. His PDA crackled with radiation readings: the culvert was a biological contamination site. Grom began to choke, his health dropped fast, and a GameAI mutant was patrolling just outside. He had 20 seconds left before blacking out. Instead of panicking, he used the PDA and manually called an emergency Med Evacuation. The Mayor's drone took him out unconscious. Grom woke on a bed in the Citadel Med Center. The Med Card was spent, but all his modest loot was still in his backpack. First lesson: the Wilds don't forgive going in without scouting.

**The Group: bonding at the campfire.** Grom realized solo survival in Ring 4 is extreme suicide. In a Citadel bar he met two other Solos: **Fox**, a sharp shooter, and **Doc**, who coordinated routes on the map better than anyone. They formed a Group on a verbal handshake of trust.

Their first run targeted an abandoned military depot in the Wilds. On the way back, packs stuffed with scarce copper, a pack of GameAI wolves came for them. Fox took a high position and held a field of fire. Grom took the close fight, covering Doc, who was hauling the heaviest crate. When Grom's rifle jammed, Doc dropped the cargo at once, bandaged his friend's wounded shoulder and handed him his spare shotgun. They got the resources to the Outskirts without losses. A circle of trust had been born, not scripted by code, but tempered in a fight.

**The Settlement: an Antenna in the wasteland.** The Group felt cramped in the Citadel, with the AI Mayor taking a huge tax on their haul. Teaming up with three more players, they loaded their savings onto a homemade cart and went to the far eastern edge of District Zero. In a gloomy forest they found the ruins of an old pumping station.

Grom opened the crafting interface at a workbench and spent the whole group's savings on a Frequency Antenna. When it was installed and fired up, the wave pulse hit the mutants' nervous systems: the howling around the station went silent, and the predators fled in panic. The system registered the station as a sovereign Settlement, and Grom became its Head. Within a week they ringed it with a log fence, built two automatic turrets against zombies, and raised a warm sealed shelter against acid storms. The ruins became a living, safe outpost.

**The Society: clan crystallization.** The light and warmth of the pumping station started drawing transit Solos. The Community grew. The Group became a full Society, with a hard division of labor: two players went all in on ore mining at a nearby mine, Doc became head logistician and ran the Settlement's shared Warehouse, and Grom took over weapon crafting, building his dexterity at the workbench.

The Settlement grew into an Industrial Zone: the Community built automatic Workshops that assembled ammo and optical sights many times faster than benches. The entire eastern Gray Zone of District Zero began to live by the Community's unwritten rules. Outsiders could rest in their shelters, but paid a share of raw materials for the use of the Workshops.

**The Great Transition: the first District.** At their technological peak, the Society hit the architectural ceiling of the AI Mayor: they were barred from building heavy factories and smelting uranium. Grom decided on the Great Transition. The Settlement Warehouse now held a critical stockpile of copper, iron and electronics.

The Head pressed the initiation button in the PDA. The system processed the request instantly and generated a new, empty hex, a Private District, to the east of District Zero. The Community went into Closed mode. All buildings, Workshops and Warehouses automatically materialized inside the new, procedurally generated Citadel at the center of the hex. The old pumping station in District Zero immediately became an abandoned set piece. For two weeks the District was cut off from the outside world by an "iron curtain." The Community worked hard inside Closed mode, installing the Citadel's defenses and setting up the first Factory conveyors.

**The trade region: Relay and Exchange.** When the Citadel was a fortress and the Factories began stamping out ammo in batches, Grom built a Relay in the middle of the city. The District opened to the entire infinite hex map.

Thanks to the District's Metallurgy specialization, the clan got a giant mine with cheap iron. In the PDA, Grom set minimal trade taxes and made Med Evacuation card prices as affordable as possible for guests. The District quickly became the region's main trade hub. Neighboring Districts short on metal queued up on the Exchange to sign contracts with Grom's District. The logistics system automatically moved iron from warehouse to warehouse, and in return the Community got streams of in-game currency and cheap agricultural provisions from the southern hexes.

**An economic crisis: the blockade loop.** Six months into the boom, the District hit a systemic crisis. Neighboring District No. 4, which sat on the shortest delivery path for the uranium ore feeding Grom's Factories, came under an aggressive rival clan. They declared a total economic embargo on Grom's Society and blocked transit in their PDA.

The logistics system had to recalculate the uranium route around it, through five distant neutral Districts. Delivery time grew fivefold, and the final price shot skyward. The District's Factories froze without fuel. With power short, the Community couldn't replace the disposable nuclear batteries in the Med Center in time. That very second, the PDA blocked Med Card sales. The District sank into chaos: guests rushed to leave the hex, since staying on a server without evacuation insurance meant risking permanent death. The great trade region became a fading, unpowered zone almost overnight.

**The birth of a civilization: the Frontier Empire.** The crisis forced Grom's Community to think strategically. Instead of a foolish head-on war with District No. 4, they used macro-diplomacy. Grom entered the Heads' closed chat in the PDA and made a secret defensive-economic Alliance with Districts No. 2 and No. 3, both suffering under the tyranny of clan No. 4.

Grom's Community funded the young clans in Districts No. 2 and No. 3, shipping thousands of ammo batches and sets of body armor from its Warehouse free of charge. The strengthened allies fully adopted the laws, charter and culture of Grom's District, making their servers fractal copies of it. Together the three Districts formed a powerful Regional Civilization, **"Steel Pact."**

They imposed a symmetrical collective embargo on District No. 4, cutting it off from energy and metal. Two weeks into the isolation, the hostile clan's Factories stopped, its reactor went dark and its turrets shut down for lack of batteries. The Steel Pact entered the unpowered Citadel of No. 4, and through the City Hall interface wiped the old Head's rights, capturing the District and joining it to their thriving Civilization. This great economic war was forever recorded in the living chronicle of the servers, created from the first step to the last by the will of real people.

## Closing: Why This World Matters

Flow: sovereign environment -> emergent interest -> breaking the fakery -> a future as a digital reality.

**What SNW: Live Anyway is.** It isn't just another online game. It is a manifesto and the foundation of a new genre: **Simulation-Native Worlds (SNW)**. It's a sovereign digital environment with no authored, imposed narrative. Players are full subjects and authors of the historical process. They set the direction of civilization themselves and carry absolute, hardcore responsibility for what they do.

True freedom of action here is limited only by the player's own principles, their technological capital and the firepower of their Community. In this universe, the only things forbidden or impossible are what a person, or a unified Society, decided to forbid and was able to defend by force of arms.

**Why it's interesting.** The project holds attention and strikes a deep chord because, inside it, you shape the fate of your character and the surrounding matter with your own hands.

Players are freed from the dictate of linear quests and on-rails plots that keep making them do what they don't want. Interest comes from honest, uncompromising cause and effect. If you win, it's thanks to your personal skill, focus and your team's cohesion. If you make a mistake and your character dies permanently, that was your choice and your responsibility. Every meter walked, every Frequency Antenna built and every District founded carries lasting value because it is tangible and written into the shared history of a living environment.

**The problem it solves.** The SNW genre goes after the biggest and most fundamental problem of the games industry since its birth: the total cardboard-and-fakery feel of virtual space, where everything is planned, scripted and static.

Traditional MMOs only imitate life. Their cities are empty set dressing, their NPCs are dead mannequins on animation rails, and their economy is a calculator that resets with every update. SNW destroys that illusion. By replacing frozen scripts with continuous world simulation, GameAI local memory and the sovereign legislation of Districts, Live Anyway turns a fake "theme park" into a real, **Causality-First** reality that lives, changes, and remembers what people did, even when nobody is looking.

**Where it can go.** The future of the SNW genre is a fully simulated, sovereign virtual space that, in time, no one will bother calling an ordinary "game."

As server capacity scales and local neural-network models develop, Live Anyway will grow beyond an entertainment product. It will become a durable digital universe that can exist and evolve on its own for decades: a world with its own genuine culture, complex economic crises, great eras and geopolitical alliances, written by millions of real human lives on the other side of the screen.

*Don't play in worlds. Live in them.*
