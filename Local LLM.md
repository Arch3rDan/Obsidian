# llama.cpp

# Cisco's Foundation-sec-8B-Reasoning
Llama 3.1 base, might be worth exploring just the base!

!!! CVE identifiers tokenize into meaningless fragments, keep this in mind

### The retrieval gotchas

Default chunking is tuned for prose. Security artifacts are not prose. Log samples, config dumps, and pcap summaries chunk badly at defaults, and you'll get retrieval that looks broken when it's actually just mis-sized. Open WebUI exposes chunk size under Admin > Documents; the common fix is raising it to around 1500 with 200 overlap and re-embedding. [Elest](https://blog.elest.io/librechat-vs-openwebui-vs-lobe-chat-which-to-self-host-in-2026/)

Also worth separating in your head: "project memory" in the sense of persistent facts about you and your work is a different mechanism from document retrieval. Most tools give you the second and let you fake the first with a long system prompt. If you want real continuity, that's a component you'd build.

