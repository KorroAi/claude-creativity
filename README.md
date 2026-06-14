![Uploading Gemini_Generated_Image_7xj4th7xj4th7xj4.png…]()

## What it is

Claude Creativity is a skill for [Claude Code](https://claude.ai/claude-code) that transforms Claude from a helpful assistant into a true creative partner. It does not just surface ideas. It hunts for the ones you never could have come up with yourself.

You know the feeling when you are brainstorming something and every idea that comes up feels like a variation on something you have already seen? This skill was built to break that cycle. It draws from ten distinct creative techniques, each one a different angle of attack, and applies them rigorously to whatever you are working on.

The result lands at the bottom of Claude's response in a signature block that is impossible to miss: a cherry blossom, unicode borders, sharp one-liners, and a quick "why it is clever" for each idea. No filler. No corporate-speak. No hedging. Just breakthroughs.

## How it works

The skill runs through four stages on every relevant response.

**1. Context detection.** Before Claude says anything, the skill evaluates whether your conversation qualifies for creative input. Brainstorming a new feature? Yes. Designing architecture? Yes. Stuck on a problem for three days? Absolutely yes. Asking for the time in Tokyo? No. The detection is automatic and invisible to you.

**2. Technique selection.** The skill picks one or two techniques from its arsenal of ten, based on the type of problem you are facing. Architecture problems get first principles and reversal. Design and naming gets forced analogies and conceptual combination. When you are truly stuck, it reaches for lateral thinking, provocation, or random stimulus.

**3. Idea generation.** This is where the real work happens. The selected techniques are applied systematically, generating ideas from angles you would not normally consider. Each idea goes through a quality gate with three rejection filters: "Could the user have thought of this alone?", "Is this merely surprising but not useful?", "Is this a lukewarm variation of a known solution?" Only ideas that pass all three deserve the creative block.

**4. Output.** The breakthroughs appear at the end of Claude's response in the signature cherry blossom block. They are sharp, one-sentence insights with a single line explaining the clever angle underneath. No fluff, no technique labels, no hedging.

## The ten techniques

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

A session might go like this.

You say: "I am building a CLI tool that finds and removes dead code from JavaScript projects. I need a name that people will remember."

Claude responds with ideas, drawn from the forced analogies and conceptual combination techniques. The response ends with:

```
╭─ 🌸 𝙲𝚁𝙴𝙰𝚃𝙸𝚅𝙸𝚃𝚈 𝙱𝚁𝙴𝙰𝙺𝚃𝙷𝚁𝙾𝚄𝙶𝙷𝚂 ─────────────────────╮
│                                                          │
│  1. "Prune" — because it evokes gardening, not garbage.  │
│     Dead code isn't trash, it's overgrowth. You're       │
│     tending a codebase, not cleaning a landfill.          │
│     🎯 Why it's clever: The gardening metaphor            │
│        reframes code maintenance from a chore into        │
│        cultivation. It feels professional, not punitive.  │
│                                                          │
│  2. "Echo" — because the tool finds what's not           │
│     there. Dead code leaves no trace of use.              │
│     🎯 Why it's clever: Naming a removal tool after       │
│        something subtle and auditory creates mystery.     │
│        People remember names they have to think about.    │
│                                                          │
│  3. "Dust" — one syllable, impossible to forget.         │
│     Like dust settling on unused shelves.                │
│     🎯 Why it's clever: The shortest possible name        │
│        in a sea of multi-word CLI tools. It also          │
│        implies something that accumulates naturally,      │
│        which dead code absolutely does.                   │
│                                                          │
╰──────────────────────────────────────────────────────────╯
```

The block always uses the unicode corner characters, the cherry blossom marker, the small caps header text, and the target markers on the "why it is clever" lines. This is the signature. Once you have seen it a few times, you will recognize it before you even read a word.

## The output format

Every creative block follows the same structure.

The header is framed with unicode box-drawing characters and marked with a cherry blossom. Inside, each breakthrough gets a number, a single sharp sentence describing the idea, and a target marker with one line explaining the clever angle. The number of ideas varies with the situation but never drops below three.

The ideas are not labeled with the technique that generated them. The technique is invisible to the reader. The ideas stand on their own.

The block sits at the very end of Claude's response, after the normal answer. It is additive, never a replacement. You get the helpful answer you were expecting, and then you get the breakthroughs you were not.

## What makes it different

Most AI creativity tools are prompt-based. You ask for ideas. The model generates ideas. The quality depends entirely on how good your prompt was and how lucky the model is feeling.

Claude Creativity is structural. It does not just say "be more creative." It loads a specific creative persona, matches techniques to problem types, applies rigorous methods from the creativity research literature, and filters results through a quality gate that would make a journal editor proud. The ideas are not just the model being creative. They are the model being creative inside a system designed to maximize creative output.

The techniques are not AI inventions. They come from decades of research on human creativity: Edward de Bono's lateral thinking, the provocation operation (PO), first principles reasoning from physics, inversion from stoic philosophy and modern strategy, conceptual combination from cognitive science. The skill brings all of this to bear on your problem, systematically, every time.

## Repository structure

```
claude-creativity/
  SKILL.md                   The main skill definition and workflow
  references/
    persona.md               The creative genius persona that Claude embodies
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
  evals/
    evals.json               Test cases for verification
```

## Contributing

This is an open skill. If you find a technique that reliably produces better breakthroughs, or if you improve the quality gate, open a PR.

The skill is designed to be extended. Adding a new technique means creating a new file in `references/techniques/` following the existing format (when to use, the method, an example, why it works) and registering it in the technique selection table in `SKILL.md`. The rest of the pipeline stays the same.

---

Built for [Claude Code](https://claude.ai/claude-code). The cherry blossom block is the signature. If you see it, you know Claude Creativity is working.

[GitHub: KorroAi/claude-creativity](https://github.com/KorroAi/claude-creativity)
