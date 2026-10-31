# EileenClara

Undergraduate, finishing my degree in computer science. I work on LLM inference systems —
mostly the part between a published result and a serving engine that holds up under load.

---

## What I'm working on

**KV-cache eviction in vLLM V1.** vLLM's V1 engine deleted the pluggable evictor
abstraction the ARC paper was built on, so the policy has to be re-attached by
reimplementing the free-block queue. I ported it, and wrote up the eleven adapter-layer
traps that stood in the way — [four of them fail silently](https://github.com/EileenClara/vllm-arc-evictor/blob/master/docs/migration-v0-v1.md),
which is why they cost more than the crashes did.

The port reproduces V0 within 0.3 pp. The result I find more interesting is the ablation:
on QuALITY, ARC's block-level ghost contributes **exactly zero**; freezing `p` at its best
value beats adaptive `p` by **0.81 pp**; and a two-queue policy with one shared ghost beats
ARC by **1.23 pp** — then loses **18.6 pp** on a short-hot-set workload, because removing
`p` also removed the floor it was quietly providing. That trade is the open problem.

→ **[vllm-arc-evictor](https://github.com/EileenClara/vllm-arc-evictor)** · `vLLM` `KV cache` `inference`

---

## Also

**Retrieval-augmented systems, in production.**
<!-- fill in: one sentence — what the system does, and one number that proves it works -->

**Multimodal fine-tuning.**
<!-- fill in: one sentence — base model, task, and the metric that moved -->

**Tooling.** [py-call-map](https://github.com/EileenClara/py-call-map) — a VS Code extension
that draws Python call graphs, Jupyter notebooks included. Built because tracing a
2000-line notebook by hand is a waste of an afternoon.

---

## How I work

I keep the negative results. When a fix does not move the number, that goes in the notes
too — "I tried this and it did not work" is most of what makes the next claim believable.
The vLLM write-up spends five sections on theories that turned out to be wrong, and that
is deliberate.

If you want to judge the style before deciding whether to work with me, read
[trap 1](https://github.com/EileenClara/vllm-arc-evictor/blob/master/docs/migration-v0-v1.md)
through trap 11. It is about eleven pages of things going wrong in specific ways.

## Contact

Open to research collaborations, and to a small number of engineering engagements —
inference optimization, vLLM internals, retrieval systems that need to actually ship.

Fastest route is an issue on any repository. Otherwise: `1429491464@qq.com`.
