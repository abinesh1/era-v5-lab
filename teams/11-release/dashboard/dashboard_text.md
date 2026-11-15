# ERA V5 Lab: dashboard text

**Date:** 15 Nov 2026
**Owner:** Release

This page explains the public dashboard of the ERA V5 lab of The School of AI. Monitoring built the dashboard. It
shows how the training runs of the lab are going. Each panel has one plain sentence below.

## Words on this page

- A token is a small piece of text, such as a word or a part of a word. A tokenizer is the tool that splits text into tokens.
- A byte is the basic unit that a computer uses to store text.
- A step is one round of training. In each step, the model reads a batch of text and updates itself.
- Loss measures how wrong the guesses of the model are. A lower loss is better.
- Held-out text is text that the model never trains on. It tests the model on text it has not seen.
- A GPU (graphics processing unit) is the chip that does the work of training. FLOPs (floating-point operations) are the calculations that a GPU does.
- Some panels are about the mixture-of-experts layers of the model. In these layers, a router sends each token to a few small parts of the layer, called experts.

## Learning

| Panel | What it shows |
|---|---|
| Next-token loss | It shows how well the model predicts the next token of the training text at each step. |
| Multi-token prediction loss | It shows the same kind of loss for a second output head that learns to predict a token further ahead in the text. |
| Validation loss | It shows the loss on held-out text, next to the training loss for comparison. |
| Validation bits per byte | It shows how well the model predicts held-out text per byte instead of per token, so readers can compare runs with different tokenizers. |
| Loss over groups of steps | It shows the next-token loss averaged over groups of steps, so that the long-term trend is easier to see. |
| Learning rate | It shows the learning rate, the setting that controls how big a change each step makes to the model. |

## Training health

| Panel | What it shows |
|---|---|
| Gradient norm | It shows the size of the gradients, the changes that each step wants to make, before the training caps them at a set limit. |
| Gradient clipping rate | It shows the share of steps in which the training scaled the gradients down to that limit. |
| Update-to-weight ratio | It compares the size of each change to the model with the size of the model, and very large or tiny values warn of trouble. |

## Speed and hardware

| Panel | What it shows |
|---|---|
| Throughput (tokens per second) | It shows how many tokens the training processes each second, so a drop points to a slowdown even when the loss looks fine. |
| Model FLOPs utilisation (MFU) | It shows the share of the top calculating speed of the GPUs that the training really uses. |
| Data loader wait time | It shows how long each step waits for the next batch of text, so a rise points to a slow data feed. |
| GPU memory used by training | It shows how much GPU memory the training program itself uses for the model and the values it needs to train it. |
| Total GPU memory used | It shows all the memory in use on each GPU by every program, so it is higher than what the training program alone uses. |
| GPU power | It shows how much electrical power each GPU draws, which tells readers how hard the GPUs are working. |
| GPU temperature | It shows the temperature of each GPU every second, because a GPU that gets too hot slows itself down. |
| GPU temperature and heat slowdown | It shows the temperature of a GPU at each step, and marks the steps where heat made that GPU slow itself down. |

## Text

| Panel | What it shows |
|---|---|
| Tokens per byte | It shows how many tokens the model reads for each byte of text, for all the text and for each language. |

## Mixture of experts

| Panel | What it shows |
|---|---|
| Unused experts | It counts the experts that the router has almost stopped using, and a healthy run has none. |
| Unused experts by layer | It shows the same count for each layer on its own, so readers can see which layers are losing experts. |
| Least-used expert | It shows the share of the work that the least-used expert gets, compared with a fair share, as an early warning. |
| Router imbalance | It shows how much more work the busiest expert gets than the average expert, in the layer where the work is most uneven. |
| Expert load imbalance | It shows the same imbalance as a ratio: the share of the busiest expert divided by the average share. |

---

## Review record (remove this section before publishing)

This record is public, like the rest of the pull request. Put only public facts in it: yes or no, and links to
public pull requests. Never link to the CAP chat. Chat links are internal.

How to fill it:

1. Monitoring sends the list of public panels (due D3). Remove every row above that is not on the list, and add a
   row for each public panel that is missing.
2. Use the panel names that Monitoring gives. The names above are suggestions from Release.
3. Monitoring checks that each sentence is true for its panel. The lead of Monitoring gives an OK.
4. Architecture checks the words about mixture-of-experts layers and multi-token prediction. The lead gives an OK.
5. Write `[number: waiting for TSAI]` for any number that TSAI has not approved yet. The text above has no numbers.
6. Run `python teams/11-release/style/check_style.py <this file> --numbers` and clear every error.
7. TSAI approves this pull request before the G11 lead merges it. Then Release sends the approved text to Monitoring
   for the public panels.

The source of every panel is the private dashboard `teams/08-monitoring/grafana/private_v1.json`, its notes in
`teams/08-monitoring/grafana/README.md` and the metric list `teams/08-monitoring/metrics/metric_list_v1.yaml`.

| Panel | Private panel | On the public list | Monitoring OK |
|---|---|---|---|
| Next-token loss | `id 2` Loss (next-token) | waiting for Monitoring | no |
| Multi-token prediction loss | `id 3` Loss (multi-token prediction) | waiting for Monitoring | no |
| Validation loss | `id 20` Validation loss | waiting for Monitoring | no |
| Validation bits per byte | `id 25` Validation bits per byte | waiting for Monitoring | no |
| Loss over groups of steps | `id 9` Loss (next-token), mean per bucket | waiting for Monitoring | no |
| Learning rate | `id 4` Learning rate | waiting for Monitoring | no |
| Gradient norm | `id 17` Gradient norm | waiting for Monitoring | no |
| Gradient clipping rate | `id 19` Gradient clipping rate | waiting for Monitoring | no |
| Update-to-weight ratio | `id 24` Update-to-weight ratio | waiting for Monitoring | no |
| Throughput (tokens per second) | `id 5` Throughput | waiting for Monitoring | no |
| Model FLOPs utilisation (MFU) | `id 7` Model FLOPs utilization | waiting for Monitoring | no |
| Data loader wait time | `id 18` Loader Wait Time | waiting for Monitoring | no |
| GPU memory used by training | `id 6` GPU memory allocated | waiting for Monitoring | no |
| Total GPU memory used | `id 26` GPU memory used | waiting for Monitoring | no |
| GPU power | `id 11` GPU power | waiting for Monitoring | no |
| GPU temperature | `id 12` GPU temperature | waiting for Monitoring | no |
| GPU temperature and heat slowdown | `id 22` GPU temperature and thermal throttle | waiting for Monitoring | no |
| Tokens per byte | `id 23` Tokens per byte | waiting for Monitoring | no |
| Unused experts | `id 13` MoE Dead Experts Count | waiting for Monitoring | no |
| Unused experts by layer | `id 16` MoE Dead Experts by Layer | waiting for Monitoring | no |
| Least-used expert | `id 15` MoE Weakest Expert Utilization | waiting for Monitoring | no |
| Router imbalance | `id 21` MoE Router MaxVio | waiting for Monitoring | no |
| Expert load imbalance | `id 27` MoE Expert Load Imbalance | waiting for Monitoring | no |

- [ ] Monitoring sent the list of public panels, and the rows match it
- [ ] `check_style.py` gives 0 errors
- [ ] The text has no number that TSAI has not approved
- [ ] The text names teams only, and no person
- [ ] Nothing from the internal list in `public_internal.md`
- [ ] The lead of Monitoring gave an OK
- [ ] The lead of Architecture gave an OK on the words about experts and multi-token prediction
- [ ] The G11 lead reviewed the pull request
- [ ] TSAI approved on: [DD Mon YYYY]
- [ ] Merged after TSAI approved
- [ ] Release sent the approved text to Monitoring
