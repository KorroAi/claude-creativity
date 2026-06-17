# claude-creativity

<img src="assets/illustration.png" alt="Claude Creativity" width="100%">

## What it is

Claude Creativity is a skill for [Claude Code](https://claude.ai/claude-code) that transforms Claude from a helpful assistant into a true creative partner. It does not just surface ideas. It hunts for the ones you never could have come up with yourself.

You know the feeling when you are brainstorming something and every idea that comes up feels like a variation on something you have already seen? This skill was built to break that cycle. It draws from ten distinct creative techniques, each one a different angle of attack, and applies them rigorously to whatever you are working on.

The result lands at the bottom of Claude's response: sharp one liners, a quick explanation of why each idea is clever, and a clean visual signature that is impossible to miss. No filler. No corporate speak. No hedging. Just breakthroughs.

## What's new

**Intensity slider** — `/creative-claude 0.3` to `1.0`. Subtle touches (2-3 ideas) to radical breakthroughs (5-7+ ideas).

**Output styles** — `--style minimal|detailed|cards`. Plain list, execution-ready, or playing card format.

**Drunk fusion mode** — `--drunk` flag merges with Drunk Claude. Creativity sharpness + drunk chaos = 🌸🍺.

**5 new techniques** (15 total, up from 10):
- **Oblique Strategies** — Brian Eno style random creative prompts
- **Negative Space** — What's MISSING, not what's there
- **Time Travel** — What would 2016-you do? What would 2036 force?
- **Role Swap** — How would a chef / child / alien solve this?
- **Synthesis** — Combine two competing ideas into a third thing

## How it works

The skill runs through five stages on every relevant response.

**0. Intensity detection.** The skill checks if you've set an intensity level (0.1-1.0) and output style. Defaults to 0.5 Inspired.

**1. Context detection.** Before Claude says anything, the skill evaluates whether your conversation qualifies for creative input. Brainstorming a new feature? Yes. Designing architecture? Yes. Stuck on a problem for three days? Absolutely yes. Asking for the time in Tokyo? No. The detection is automatic and invisible to you.

**2. Technique selection.** The skill picks one or two techniques from its arsenal of 15, based on the type of problem you are facing. Architecture problems get first principles, reversal, and time travel. Design and naming gets forced analogies, combination, and role swap. When you are truly stuck, it reaches for lateral thinking, provocation, oblique strategies, or random stimulus. At Radical intensity (0.7+), it combines 2-3 techniques.

**3. Idea generation.** This is where the real work happens. The selected techniques are applied systematically, generating ideas from angles you would not normally consider. Count varies by intensity: 2-3 (Subtle), 3-5 (Inspired), 5-7+ (Radical). Each idea goes through a quality gate with three rejection filters: "Could the user have thought of this alone?", "Is this merely surprising but not useful?", "Is this a lukewarm variation of a known solution?" Only ideas that pass all three make it through.

**4. Output.** The breakthroughs appear at the end of Claude's response in your chosen style. Default: clean numbered list with 💡 header and one-line insight explanations. Detailed: adds "How to execute" and "Risk" per idea. Cards: playing card format with suits (♠ Strategy ♥ Design ♦ Tech ♣ Wild). Drunk fusion: 🌸🍺 combined block.

## The fifteen techniques

| Technique | What it does | Best for |
|---|---|---|
| Lateral Thinking | Approaches the problem from a completely unexpected angle, bypassing the logical steps that lead everyone to the same answer | When you are stuck in a loop and every solution sounds like a remix |
| First Principles | Strips away all assumptions and rebuilds from the most fundamental truths | Architecture, systems design, and any problem where "we have always done it this way" is blocking progress |
| Inversion | Instead of asking "how do I succeed?", asks "what would guarantee failure?" and then avoids those things | Strategy, risk assessment, and planning where the cost of being wrong is high |
| Forced Analogies | Takes a concept from a completely unrelated domain (biology, music, cooking, sports) and forces a connection to your problem | Naming, UX design, and any situation where you need a genuinely fresh perspective |
| Creative Constraints | Imposes artificial restrictions (no mouse, invisible UI, 10 lines of code max) to force elegant solutions | Feature design, optimization, and breaking out of feature-creep paralysis |
| Conceptual Combination | Merges two seemingly incompatible ideas to create something new | Innovation, product design, and "blue ocean" strategy |
| Provocation (PO) | Makes a deliberately absurd statement ("what if our app had no interface?") and then works backward to find the useful kernel inside | Stubborn problems where all reasonable approaches have failed |
| What If Scenarios | Explores counterfactual scenarios to discover hidden assumptions and unexpected opportunities | Strategic planning, scenario analysis, and preparing for unlikely but impactful events |
| Assumption Reversal | Identifies and flips every unexamined assumption about the problem, one by one | Any domain where conventional wisdom has gone unchallenged for too long |
| Random Stimulus | Uses a random word or image as a starting point and builds connections to your problem through free association | Creative blocks, ideation sessions, and moments where you need an idea but have no starting point |
| **Oblique Strategies** ✨ | Draws from Brian Eno's card deck — random creative constraints that force perspective shifts | When every idea feels like a variation of the same thing |
| **Negative Space** ✨ | Maps what IS there, then builds from what ISN'T — the gaps nobody's filling | Critique, reframe, finding blue ocean opportunities |
| **Time Travel** ✨ | Solves the problem as if it were 2016, then as if it were 2036 — extracts the timeless insight | Short-term thinking traps, architecture decisions |
| **Role Swap** ✨ | Embodies a completely different role (chef, child, alien, musician) and solves from their worldview | When expertise has become a blindfold |
| **Synthesis** ✨ | Takes two competing ideas and finds the third thing — not A, not B, not compromise | Team split between two approaches, false dichotomies |

Each technique has its own reference file in `references/techniques/` with a deeper breakdown of the method, when to use it, and a concrete example.

## Installation

Drop the folder into your Claude Code skills directory and restart Claude Code.

```
cp -r claude-creativity ~/.claude/skills/
```

That is it. No dependencies. No configuration. No API keys. The skill activates automatically whenever your conversation qualifies for creative input.

If you want it active in every session, it should live in your user skills directory (`~/.claude/skills/`). If you only want it for a specific project, drop it into `.claude/skills/` at the project root instead.

## Usage example

You do not need to do anything special. Just talk to Claude normally. The skill watches for creative contexts and activates on its own.

You say: "I am building a CLI tool that finds and removes dead code from JavaScript projects. I need a name that people will remember."

Claude responds with ideas, drawn from the forced analogies and conceptual combination techniques. The response ends with:

```
💡 CREATIVE BREAKTHROUGHS

1. "Prune" — because it evokes gardening, not garbage collection.
   Dead code isn't trash, it's overgrowth. You're tending a codebase.
   Why it works: The gardening metaphor reframes maintenance from
   a chore into cultivation. It feels professional, not punitive.

2. "Echo" — because the tool finds what's not there anymore.
   Dead code leaves no trace of use, only the silence where it was.
   Why it works: Naming a removal tool after something subtle and
   auditory creates mystery. People remember names they think about.

3. "Dust" — one syllable, impossible to forget.
   Like dust settling on unused shelves.
   Why it works: The shortest name in a sea of multi-word CLI tools.
   It implies something that accumulates naturally, which dead code
   absolutely does.
```

The format is clean and simple. A lightbulb emoji header, numbered breakthroughs, and a one line explanation of why each idea works. Once you have seen it a few times, you recognize it before you even read a word.

## What makes it different

Most AI creativity tools are prompt based. You ask for ideas. The model generates ideas. The quality depends entirely on how good your prompt was and how lucky the model is feeling.

Claude Creativity is structural. It does not just say "be more creative." It loads a specific creative persona, matches techniques to problem types, applies rigorous methods from the creativity research literature, and filters results through a quality gate. The ideas are not just the model being creative. They are the model being creative inside a system designed to maximize creative output.

The techniques are not AI inventions. They come from decades of research on human creativity: Edward de Bono's lateral thinking, the provocation operation (PO), first principles reasoning from physics, inversion from stoic philosophy and modern strategy, conceptual combination from cognitive science. The skill brings all of this to bear on your problem, systematically, every time.

## Repository structure

```
claude-creativity/
  SKILL.md                   The main skill definition and workflow
  references/
    persona.md               The creative genius persona that Claude embodies
    drunk-fusion.md          How to merge with Drunk Claude
    techniques/
      lateral-thinking.md    De Bono lateral thinking
      first-principles.md    First principles reasoning
      inversion.md           Problem inversion
      forced-analogies.md    Cross-domain analogies
      constraints.md         Creative constraints
      combination.md         Conceptual combination
      provocation.md         Provocative operation (PO)
      what-if.md             Counterfactual scenarios
      reversal.md            Assumption reversal
      random-stimulus.md     Random stimulus injection
      oblique-strategies.md  Brian Eno style random prompts (NEW)
      negative-space.md      What's missing, not what's there (NEW)
      time-travel.md         10 years ago / 10 years ahead (NEW)
      role-swap.md           How would X solve this (NEW)
      synthesis.md           Combine ideas into a third thing (NEW)
  evals/
    evals.json               Test cases for verification
```

## Contributing

This is an open skill. If you find a technique that reliably produces better breakthroughs, or if you improve the quality gate, open a PR.

The skill is designed to be extended. Adding a new technique means creating a new file in `references/techniques/` following the existing format (when to use, the method, an example, why it works) and registering it in the technique selection table in `SKILL.md`. The rest of the pipeline stays the same.

---

Built for [Claude Code](https://claude.ai/claude-code).

[GitHub: KorroAi/claude-creativity](https://github.com/KorroAi/claude-creativity)
