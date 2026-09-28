# NSA Codebreaker Challenge — Structure, Skills, and Strategy

> Project knowledge file. This captures the *recurring shape* of the challenge and
> general strategy. It is **not** a leak of the 2026 tasks — those are not public
> until launch. Once the real scenario drops, paste the actual task list into a chat
> and we'll map tools and approach to it.

## The 2026 cycle at a glance

- **Runs:** Friday, September 25, 2026 (12:00 EST) through January 20, 2027.
- **Official site:** https://nsa-codebreaker.org/home
  - Register: https://nsa-codebreaker.org (link on the home page)
  - Rules/FAQ: https://nsa-codebreaker.org/FAQ
  - Technical resources (incl. VM setup guidance): https://nsa-codebreaker.org/resources
  - Get Help tab: bottom of the site (for site/technical issues during the event)
- **Format:** a single continuous mission-oriented scenario broken into tasks that
  escalate in difficulty. Early tasks are approachable; later ones are genuinely hard
  and multi-step. Your final score is the sum of task scores.
- **Scoring / divisions:** schools are ranked by the cumulative points of their
  *registered students* (not alumni/faculty). Schools are grouped into divisions by
  number of registered participants. Your progress contributes to Cedarville's score.
- **Per-participant binaries:** each player receives a slightly different set of
  challenge binaries/files. Solutions are not transferable between people — a
  structural anti-cheat, and a reason published writeups won't hand you your answer.

## Rules that matter (read the real FAQ, but the gist)

- **Solo.** Tasks are to be solved on your own. Collaborating with other people to
  solve a task is cheating. You don't misrepresent others' work as your own, don't
  claim ownership of material you didn't create, and don't post spoilers.
- **Tools and research are encouraged.** Using disassemblers, debuggers, docs,
  search, tutorials, and reference material is how the challenge is meant to be played.
  The line is between *learning how to solve* (fine) and *getting the specific answer
  from an outside source* (not fine).
- **Run untrusted binaries in a VM.** The challenge binaries are believed safe, but
  standard practice — and NSA's own advice — is to analyze/run them inside an isolated
  virtual machine. Some past-year binaries have tripped antivirus heuristics; that's
  expected for RE artifacts.

## Recurring skill categories

The scenario theme changes yearly (past themes have included ransomware-as-a-service
rings, compromised defense-industrial-base supply chains, and "tech-savvy adversary"
communication tools), but the underlying skills recur. Expect a mix drawn from:

| Category | What it tends to look like |
|---|---|
| **Software reverse engineering** | Static analysis of provided ELF/PE binaries in Ghidra: recover logic, find hidden checks, understand a custom format or algorithm. The backbone of most years. |
| **Cryptanalysis / cryptography** | Identify and attack a scheme — weak/custom crypto, misused primitives, bad RSA parameters, homebrew ciphers, key/nonce reuse. Understanding the math is the task, not running a magic tool. |
| **Forensics** | Carve/inspect files, analyze disk or memory images, extract hidden data, reconstruct artifacts, follow a chain of evidence. |
| **Protocol / network analysis** | Reverse a custom protocol from packet captures, decode framed messages, sometimes parse protobuf or a bespoke wire format. |
| **Vulnerability research & exploit development** | Find a bug class in a provided vulnerable binary and craft input that triggers it, against the challenge's own sandboxed target. Later tasks. |
| **Programming / scripting** | Automate an analysis, brute-force a bounded space, implement a decoder, or drive a service. Usually Python. |
| **Rotating specialty topics** | Depending on the year: blockchain/ledger analysis, signals/RF, embedded/firmware, drone/hardware, mobile. Don't over-prepare these until the scenario tells you they're relevant. |

Difficulty ramps hard between early and late tasks. Points are weighted toward the
harder tasks, so completion depth matters more than speed on the easy ones.

## A general working method (per task)

This is the loop to internalize — the tutor side of this project exists to make each
step faster, not to skip steps.

1. **Read the task prompt carefully and fully.** The narrative usually tells you the
   category, the goal, and often a strong hint about the technique. Re-read it when stuck.
2. **Triage the artifact before diving in.** `file`, `strings`, `xxd`/`hexdump`,
   `binwalk`, `checksec` on a binary; `capinfos`/protocol hierarchy on a pcap;
   `exiftool`/`binwalk` on media. Build a picture before opening the heavy tools.
3. **Form a hypothesis about the category and mechanism.** "This is a custom cipher,"
   "this is a format-string bug," "this protocol frames length-prefixed messages."
4. **Reach for the right primary tool** (see the toolkit reference file) and confirm or
   kill the hypothesis. Static RE -> Ghidra. Dynamic behavior -> GDB/pwndbg, ltrace/strace.
   Crypto -> understand the scheme, then Python/CyberChef. Forensics -> carving/memory tools.
5. **Take notes as you go.** Addresses, offsets, constants, hypotheses, dead ends.
   Multi-step tasks punish you for not writing things down.
6. **Automate the boring part** once you understand it — a decoder, a solver, a driver
   script — rather than doing it by hand repeatedly.
7. **Verify against the task's own check.** Each participant's answer is specific to
   their binaries; the site validates it. If it's wrong, your *understanding* is the
   thing to fix, not the answer to fish for elsewhere.

## How to use this project effectively

- **When a task drops:** paste the prompt (and what you've already observed) into a
  chat here. Ask for the *category read* and a *first-move plan*, not the answer.
- **When you're stuck:** say what you tried and where it broke. Ask to escalate hints
  by degrees — concept, then technique, then how-I'd-approach-it — and take the final
  step yourself.
- **When you hit unfamiliar territory:** ask for a focused primer on the concept
  (a bug class, a crypto scheme, a file format, a protocol pattern) with a tiny worked
  example on *made-up* data, then apply it to your real artifact yourself.
- **For skill-building between tasks:** past challenges (2019+) are archived on the
  resources page and are fair game to practice on and discuss freely.

## Environment setup checklist

- An isolated Linux VM (a Kali or Ubuntu VM is typical; setup guidance is on the
  challenge's Technical Resources page). Snapshot it clean before running binaries.
- Ghidra installed (see toolkit file for the current version and source).
- A working Python 3 environment with the CTF/crypto/exploit libraries listed in the
  toolkit file.
- A scratch/notes system you actually use.
