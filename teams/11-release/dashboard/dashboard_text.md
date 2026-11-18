# ERA V5 Lab: dashboard text

**Date:** 18 Nov 2026
**Owner:** Release

This page gives one plain sentence for each panel on the public dashboard of the ERA V5 lab of The School of AI.
Monitoring built the dashboard. It shows how the training runs of the lab are going. The words follow the public
glossary in `glossary.md`.

| Panel | What it shows |
|---|---|
| Training Loss (Next-Token) | It shows how well the model predicts the next token of its training text at each training step, and a lower loss is better. |
| Training Loss (Step-Bucket Mean) | It shows the next-token training loss averaged over groups of consecutive training steps, so the long-term trend is easier to see. |
| Held-Out Validation Loss | It shows the next-token loss on held-out text, which is set aside from training, next to the training loss for comparison. |
| Held-Out Validation Bits per Byte | It shows the held-out loss per byte instead of per token, so readers can compare runs with different tokenizers on the same validation text. |
| Learning Rate Schedule | It shows the learning rate, which helps set the size of each update to the model, at each training step. |
| Tokens per Byte (All Text & by Language) | It shows the tokens per byte of text for all languages together and for each language, where a lower value means fewer tokens. |
| Mixture-of-Experts Load Balance | It shows how evenly the model spreads tokens across its experts, by comparing the busiest expert with the average in the least balanced layer. |

---

## Review record (remove this section before publishing)

This record is public, like the rest of the pull request. Put only public facts in it: yes or no, and links to
public pull requests. Never link to the CAP chat. Chat links are internal.

How to fill it:

1. The panel names and the panel list come from the public dashboard of Monitoring,
   `teams/08-monitoring/grafana/public_v1.json` ([#495](https://github.com/theschoolofai/era-v5-lab/pull/495)).
2. The words follow the public glossary ([#497](https://github.com/theschoolofai/era-v5-lab/pull/497),
   [#578](https://github.com/theschoolofai/era-v5-lab/pull/578)).
3. Monitoring checks that each sentence is true for its panel. The lead of Monitoring gives an OK.
4. Run `python teams/11-release/style/check_style.py <this file> --numbers` and clear every error.
5. TSAI approves the public panels and this text. Then the G11 lead merges it, and Release sends the
   approved text to Monitoring for the panel descriptions.

| Panel | Public panel | Source | Monitoring OK |
|---|---|---|---|
| Training Loss (Next-Token) | `id 2` | [#495](https://github.com/theschoolofai/era-v5-lab/pull/495) | no |
| Training Loss (Step-Bucket Mean) | `id 9` | [#495](https://github.com/theschoolofai/era-v5-lab/pull/495) | no |
| Held-Out Validation Loss | `id 20` | [#495](https://github.com/theschoolofai/era-v5-lab/pull/495) | no |
| Held-Out Validation Bits per Byte | `id 25` | [#495](https://github.com/theschoolofai/era-v5-lab/pull/495) | no |
| Learning Rate Schedule | `id 4` | [#495](https://github.com/theschoolofai/era-v5-lab/pull/495) | no |
| Tokens per Byte (All Text & by Language) | `id 23` | [#495](https://github.com/theschoolofai/era-v5-lab/pull/495) | no |
| Mixture-of-Experts Load Balance | `id 27` | [#495](https://github.com/theschoolofai/era-v5-lab/pull/495) | no |

- [ ] `check_style.py` gives no errors
- [ ] The text has no number that TSAI has not approved
- [ ] The text names teams only, and no person
- [ ] Nothing from the internal list in `public_internal.md`
- [ ] The lead of Monitoring gave an OK
- [ ] The G11 lead reviewed the pull request
- [ ] TSAI approved on: [DD Mon YYYY]
- [ ] Merged after TSAI approved
- [ ] Release sent the approved text to Monitoring
