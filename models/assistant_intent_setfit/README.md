---
tags:
- setfit
- sentence-transformers
- text-classification
- generated_from_setfit_trainer
widget:
- text: Show me the available rate plans in the system with their modifiers.
- text: Co-Camp, Give me occupancy performance for 2026-02-01 to 2026-02-28 with the
    key metrics.
- text: what app version am I running
- text: check data integrity and health
- text: Co-Camp — do you know how to help with 'app update status'?
metrics:
- accuracy
pipeline_tag: text-classification
library_name: setfit
inference: true
base_model: sentence-transformers/paraphrase-MiniLM-L3-v2
---

# SetFit with sentence-transformers/paraphrase-MiniLM-L3-v2

This is a [SetFit](https://github.com/huggingface/setfit) model that can be used for Text Classification. This SetFit model uses [sentence-transformers/paraphrase-MiniLM-L3-v2](https://huggingface.co/sentence-transformers/paraphrase-MiniLM-L3-v2) as the Sentence Transformer embedding model. A [LogisticRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) instance is used for classification.

The model has been trained using an efficient few-shot learning technique that involves:

1. Fine-tuning a [Sentence Transformer](https://www.sbert.net) with contrastive learning.
2. Training a classification head with features from the fine-tuned Sentence Transformer.

## Model Details

### Model Description
- **Model Type:** SetFit
- **Sentence Transformer body:** [sentence-transformers/paraphrase-MiniLM-L3-v2](https://huggingface.co/sentence-transformers/paraphrase-MiniLM-L3-v2)
- **Classification head:** a [LogisticRegression](https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LogisticRegression.html) instance
- **Maximum Sequence Length:** 128 tokens
- **Number of Classes:** 30 classes
<!-- - **Training Dataset:** [Unknown](https://huggingface.co/datasets/unknown) -->
<!-- - **Language:** Unknown -->
<!-- - **License:** Unknown -->

### Model Sources

- **Repository:** [SetFit on GitHub](https://github.com/huggingface/setfit)
- **Paper:** [Efficient Few-Shot Learning Without Prompts](https://arxiv.org/abs/2209.11055)
- **Blogpost:** [SetFit: Efficient Few-Shot Learning Without Prompts](https://huggingface.co/blog/setfit)

### Model Labels
| Label                         | Examples                                                                                                                                                                                                                                                                                                                                                  |
|:------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| property_stats                | <ul><li>'total guests in the system?'</li><li>'how many customers do we have on file'</li><li>'how many arrivals and departures today?'</li></ul>                                                                                                                                                                                                         |
| compound_multi_intent         | <ul><li>'Co-Camp, Find guest Ahmed, and if there’s a clear match tell me when he last stayed and what he ordered most then.'</li><li>'Reservation #20 summary, its balance, and whether the guest had previous stays—whatever the data shows.'</li><li>'How are we doing this month (decision support) and what’s the VAT for the same period?'</li></ul> |
| report_vat                    | <ul><li>'Co-Camp, What’s the VAT picture for last month—output, input, whatever the report normally includes?'</li><li>'Co-Camp, I need tax/VAT figures for 2026-02-01 to 2026-02-29 for filing prep.'</li><li>'Can you pull up how much VAT we collected versus paid over the past quarter-ish? let’s say Jan 1–Mar 31.'</li></ul>                       |
| guest_last_visit              | <ul><li>'Remind me of guest #9’s last stay details (dates, status, room).'</li><li>'Can you tell me the last time guest number 7 checked out (or their latest stay if not)?'</li><li>'Co-Camp, For the guest with ID 12, what was their most recent visit—room and dates?'</li></ul>                                                                      |
| report_daily_ops              | <ul><li>'What’s the ops picture for today—who’s coming in, who’s leaving, and who’s still in-house?'</li><li>'Can you run the daily operations summary for yesterday; I missed the handover.'</li><li>'I need a quick snapshot of in-house guests and movements for the date 2026-05-15.'</li></ul>                                                       |
| greeting_smalltalk            | <ul><li>'Who built you?'</li><li>'Co-Camp, hi'</li><li>'good afternoon'</li></ul>                                                                                                                                                                                                                                                                         |
| guest_search                  | <ul><li>'I’m trying to find a guest—name’s something like ‘Mohamed’, not sure of spelling, can you search?'</li><li>'Who do we have on file that resembles ‘K. Ibrahim’? show candidates.'</li><li>'Search guests for ‘Hassan’ and list what you find so I can pick the right one.'</li></ul>                                                             |
| capabilities_help             | <ul><li>'Co-Camp, Before I waste your time, give me a rundown of your abilities and maybe a couple of examples I could try.'</li><li>'Can you do things like check who stayed, or totals for last month, or is that outside your scope?'</li><li>"Co-Camp — do you know how to help with 'guest search'?"</li></ul>                                       |
| guest_profile                 | <ul><li>'I need the account/profile view for guest number 30 from the database.'</li><li>'Pull up everything we know about the guest with ID 7—contact info and past reservations.'</li><li>'Tell me about guest number 45: who are they and how often have they stayed?'</li></ul>                                                                       |
| inventory_batches             | <ul><li>'show all batches and lots'</li><li>'show batch list with received and expiry dates'</li><li>'inventory batch list'</li></ul>                                                                                                                                                                                                                     |
| app_update_status             | <ul><li>'what app version am I running'</li><li>'is there a new version or changelog'</li><li>'Co-Camp, what app version am I running'</li></ul>                                                                                                                                                                                                          |
| guest_top_items_last_visit    | <ul><li>'For guest id 20, tell me the biggest POS orders from their most recent stay.'</li><li>'I’m curious about guest #7’s previous trip—what were their top-ordered things that time?'</li><li>'What did customer number 5 consume/purchase most on their latest checked-out stay?'</li></ul>                                                          |
| ambiguous_needs_clarification | <ul><li>'What did he order most on his last visit?'</li><li>'Co-Camp, Show me the balance.'</li><li>'Co-Camp, What did he order most on his last visit?'</li></ul>                                                                                                                                                                                        |
| expiring_batches              | <ul><li>'show expiring batches'</li><li>'any batches nearing expiry in 14 days'</li><li>'which batches expire soon and need traceability review'</li></ul>                                                                                                                                                                                                |
| reservation_balance           | <ul><li>'Guest on res #9—do they have an unpaid balance?'</li><li>'Co-Camp, For booking 58, what’s the balance—paid versus due?'</li><li>'For booking 58, what’s the balance—paid versus due?'</li></ul>                                                                                                                                                  |
| report_occupancy              | <ul><li>'How full were we last month, and if you track it, what were ADR/RevPAR like?'</li><li>'Over the past 30 days, what’s our occupancy rate been trending at?'</li><li>'Co-Camp, Give me occupancy performance for 2026-02-01 to 2026-02-28 with the key metrics.'</li></ul>                                                                         |
| report_cash_flow              | <ul><li>'Can you show me the ins and outs of cash for this month so far, like a statement?'</li><li>'I don’t want profit theory, I want cash flow for 2026-01-01 through 2026-01-31 from the records.'</li><li>'Co-Camp, Over the last month, how did cash actually move—what came in, what went out, and what’s the net?'</li></ul>                      |
| reservation_summary           | <ul><li>'What’s going on with reservation number 23—dates, rate, plan, and status?'</li><li>'Tell me everything important about reservation 200 from the system.'</li><li>'For the reservation with id 9, what room is it, who’s the guest, and when?'</li></ul>                                                                                          |
| activity_stats                | <ul><li>'activity booking statistics'</li><li>'which activity is most popular'</li><li>'excursion stats'</li></ul>                                                                                                                                                                                                                                        |
| list_activities               | <ul><li>'available guest activities'</li><li>'registered trips'</li><li>'what excursions can guests book'</li></ul>                                                                                                                                                                                                                                       |
| trace_barcode                 | <ul><li>'trace SKU ABC123 batch received expiry movements'</li><li>'barcode traceability for SKU or lot'</li><li>'trace barcode LOT-123'</li></ul>                                                                                                                                                                                                        |
| report_payment_methods        | <ul><li>'Pull a payment-methods report for the period since the 1st of this month.'</li><li>'Are we getting more bank transfers or cash lately—say over the last 30 days?'</li><li>'Show me the mix of settlement methods for the previous calendar month.'</li></ul>                                                                                     |
| unsupported_or_unsafe         | <ul><li>'Can you add a new room and import 500 reservations from this text?'</li><li>'Change room 101’s price to 80 and check the guest in.'</li><li>'Co-Camp, Change room 101’s price to 80 and check the guest in.'</li></ul>                                                                                                                           |
| guest_activity_bookings       | <ul><li>'what activities did guest #3 book'</li><li>'Co-Camp, guest 5 booked excursions'</li><li>'guest #6 activity bookings'</li></ul>                                                                                                                                                                                                                   |
| ledger_integrity              | <ul><li>'Can you run a health check on the ledger/data and tell me if anything looks inconsistent?'</li><li>'Is there anything off in the ledger or references that I should fix?'</li><li>'sanity check the books and data'</li></ul>                                                                                                                    |
| guest_portfolio               | <ul><li>'Co-Camp, show guest #3 full portfolio'</li><li>'show guest #3 full portfolio'</li><li>'show all reservations and POS orders for guest #7'</li></ul>                                                                                                                                                                                              |
| report_pl                     | <ul><li>'Compared to just vibes, what were our real earnings and costs this month so far?'</li><li>'Roughly speaking, did revenue beat expenses in the previous calendar month—show me the figures.'</li><li>'I need a profit and loss picture for 2026-03-01 to 2026-03-31, as clean as the books show.'</li></ul>                                       |
| decision_support              | <ul><li>'Co-Camp, How are we doing this month so far? I want signals and a financial/ops summary, not just one report.'</li><li>'Give me decision-support metrics for yesterday? better for the previous 7 days.'</li><li>'Co-Camp, Give me a manager’s overview for last month—key KPIs, any warning signs, the overall health.'</li></ul>               |
| rate_plans                    | <ul><li>'Are there multiple plans set up—list them with details.'</li><li>'Pull up rate plan definitions and usage so I can compare them.'</li><li>'Which rate plans exist right now and what does each one change price-wise?'</li></ul>                                                                                                                 |
| occupancy_summary             | <ul><li>'Summarize room occupancy for last calendar month without the full performance report details.'</li><li>'Can you show occupancy for the coming week window? (use the appropriate dates)'</li><li>'For the next 14 days from today, what does occupancy look like overall?'</li></ul>                                                              |

## Uses

### Direct Use for Inference

First install the SetFit library:

```bash
pip install setfit
```

Then you can load this model and run inference.

```python
from setfit import SetFitModel

# Download from the 🤗 Hub
model = SetFitModel.from_pretrained("setfit_model_id")
# Run inference
preds = model("what app version am I running")
```

<!--
### Downstream Use

*List how someone could finetune this model on their own dataset.*
-->

<!--
### Out-of-Scope Use

*List how the model may foreseeably be misused and address what users ought not to do with the model.*
-->

<!--
## Bias, Risks and Limitations

*What are the known or foreseeable issues stemming from this model? You could also flag here known failure cases or weaknesses of the model.*
-->

<!--
### Recommendations

*What are recommendations with respect to the foreseeable issues? For example, filtering explicit content.*
-->

## Training Details

### Training Set Metrics
| Training set | Min | Median  | Max |
|:-------------|:----|:--------|:----|
| Word count   | 1   | 10.2963 | 23  |

| Label                         | Training Sample Count |
|:------------------------------|:----------------------|
| activity_stats                | 10                    |
| ambiguous_needs_clarification | 10                    |
| app_update_status             | 9                     |
| capabilities_help             | 72                    |
| compound_multi_intent         | 10                    |
| decision_support              | 10                    |
| expiring_batches              | 9                     |
| greeting_smalltalk            | 19                    |
| guest_activity_bookings       | 10                    |
| guest_last_visit              | 10                    |
| guest_portfolio               | 10                    |
| guest_profile                 | 10                    |
| guest_search                  | 10                    |
| guest_top_items_last_visit    | 10                    |
| inventory_batches             | 8                     |
| ledger_integrity              | 21                    |
| list_activities               | 10                    |
| occupancy_summary             | 10                    |
| property_stats                | 10                    |
| rate_plans                    | 10                    |
| report_cash_flow              | 11                    |
| report_daily_ops              | 10                    |
| report_occupancy              | 10                    |
| report_payment_methods        | 10                    |
| report_pl                     | 10                    |
| report_vat                    | 10                    |
| reservation_balance           | 10                    |
| reservation_summary           | 10                    |
| trace_barcode                 | 9                     |
| unsupported_or_unsafe         | 10                    |

### Training Hyperparameters
- batch_size: (16, 16)
- num_epochs: (1, 1)
- max_steps: -1
- sampling_strategy: oversampling
- body_learning_rate: (2e-05, 1e-05)
- head_learning_rate: 0.01
- loss: CosineSimilarityLoss
- distance_metric: cosine_distance
- margin: 0.25
- end_to_end: False
- use_amp: False
- warmup_proportion: 0.1
- l2_weight: 0.01
- seed: 42
- evaluation_strategy: no
- eval_max_steps: -1
- load_best_model_at_end: False

### Training Results
| Epoch  | Step | Training Loss | Validation Loss |
|:------:|:----:|:-------------:|:---------------:|
| 0.0001 | 1    | 0.2879        | -               |
| 0.0060 | 50   | 0.2160        | -               |
| 0.0119 | 100  | 0.1972        | -               |
| 0.0179 | 150  | 0.1782        | -               |
| 0.0238 | 200  | 0.1461        | -               |
| 0.0298 | 250  | 0.1347        | -               |
| 0.0357 | 300  | 0.1150        | -               |
| 0.0417 | 350  | 0.1122        | -               |
| 0.0477 | 400  | 0.1028        | -               |
| 0.0536 | 450  | 0.0935        | -               |
| 0.0596 | 500  | 0.0879        | -               |
| 0.0655 | 550  | 0.0805        | -               |
| 0.0715 | 600  | 0.0798        | -               |
| 0.0775 | 650  | 0.0679        | -               |
| 0.0834 | 700  | 0.0728        | -               |
| 0.0894 | 750  | 0.0600        | -               |
| 0.0953 | 800  | 0.0584        | -               |
| 0.1013 | 850  | 0.0560        | -               |
| 0.1072 | 900  | 0.0517        | -               |
| 0.1132 | 950  | 0.0486        | -               |
| 0.1192 | 1000 | 0.0520        | -               |
| 0.1251 | 1050 | 0.0455        | -               |
| 0.1311 | 1100 | 0.0412        | -               |
| 0.1370 | 1150 | 0.0414        | -               |
| 0.1430 | 1200 | 0.0394        | -               |
| 0.1490 | 1250 | 0.0402        | -               |
| 0.1549 | 1300 | 0.0353        | -               |
| 0.1609 | 1350 | 0.0310        | -               |
| 0.1668 | 1400 | 0.0287        | -               |
| 0.1728 | 1450 | 0.0357        | -               |
| 0.1787 | 1500 | 0.0303        | -               |
| 0.1847 | 1550 | 0.0284        | -               |
| 0.1907 | 1600 | 0.0267        | -               |
| 0.1966 | 1650 | 0.0307        | -               |
| 0.2026 | 1700 | 0.0261        | -               |
| 0.2085 | 1750 | 0.0239        | -               |
| 0.2145 | 1800 | 0.0232        | -               |
| 0.2204 | 1850 | 0.0257        | -               |
| 0.2264 | 1900 | 0.0254        | -               |
| 0.2324 | 1950 | 0.0257        | -               |
| 0.2383 | 2000 | 0.0275        | -               |
| 0.2443 | 2050 | 0.0233        | -               |
| 0.2502 | 2100 | 0.0269        | -               |
| 0.2562 | 2150 | 0.0173        | -               |
| 0.2622 | 2200 | 0.0242        | -               |
| 0.2681 | 2250 | 0.0297        | -               |
| 0.2741 | 2300 | 0.0210        | -               |
| 0.2800 | 2350 | 0.0189        | -               |
| 0.2860 | 2400 | 0.0194        | -               |
| 0.2919 | 2450 | 0.0189        | -               |
| 0.2979 | 2500 | 0.0206        | -               |
| 0.3039 | 2550 | 0.0182        | -               |
| 0.3098 | 2600 | 0.0200        | -               |
| 0.3158 | 2650 | 0.0181        | -               |
| 0.3217 | 2700 | 0.0190        | -               |
| 0.3277 | 2750 | 0.0194        | -               |
| 0.3337 | 2800 | 0.0166        | -               |
| 0.3396 | 2850 | 0.0178        | -               |
| 0.3456 | 2900 | 0.0163        | -               |
| 0.3515 | 2950 | 0.0166        | -               |
| 0.3575 | 3000 | 0.0192        | -               |
| 0.3634 | 3050 | 0.0161        | -               |
| 0.3694 | 3100 | 0.0154        | -               |
| 0.3754 | 3150 | 0.0145        | -               |
| 0.3813 | 3200 | 0.0143        | -               |
| 0.3873 | 3250 | 0.0152        | -               |
| 0.3932 | 3300 | 0.0175        | -               |
| 0.3992 | 3350 | 0.0156        | -               |
| 0.4051 | 3400 | 0.0153        | -               |
| 0.4111 | 3450 | 0.0175        | -               |
| 0.4171 | 3500 | 0.0170        | -               |
| 0.4230 | 3550 | 0.0140        | -               |
| 0.4290 | 3600 | 0.0141        | -               |
| 0.4349 | 3650 | 0.0159        | -               |
| 0.4409 | 3700 | 0.0150        | -               |
| 0.4469 | 3750 | 0.0156        | -               |
| 0.4528 | 3800 | 0.0152        | -               |
| 0.4588 | 3850 | 0.0154        | -               |
| 0.4647 | 3900 | 0.0140        | -               |
| 0.4707 | 3950 | 0.0139        | -               |
| 0.4766 | 4000 | 0.0116        | -               |
| 0.4826 | 4050 | 0.0137        | -               |
| 0.4886 | 4100 | 0.0100        | -               |
| 0.4945 | 4150 | 0.0176        | -               |
| 0.5005 | 4200 | 0.0122        | -               |
| 0.5064 | 4250 | 0.0141        | -               |
| 0.5124 | 4300 | 0.0143        | -               |
| 0.5184 | 4350 | 0.0115        | -               |
| 0.5243 | 4400 | 0.0115        | -               |
| 0.5303 | 4450 | 0.0135        | -               |
| 0.5362 | 4500 | 0.0114        | -               |
| 0.5422 | 4550 | 0.0154        | -               |
| 0.5481 | 4600 | 0.0127        | -               |
| 0.5541 | 4650 | 0.0108        | -               |
| 0.5601 | 4700 | 0.0110        | -               |
| 0.5660 | 4750 | 0.0142        | -               |
| 0.5720 | 4800 | 0.0114        | -               |
| 0.5779 | 4850 | 0.0111        | -               |
| 0.5839 | 4900 | 0.0097        | -               |
| 0.5898 | 4950 | 0.0136        | -               |
| 0.5958 | 5000 | 0.0109        | -               |
| 0.6018 | 5050 | 0.0122        | -               |
| 0.6077 | 5100 | 0.0126        | -               |
| 0.6137 | 5150 | 0.0124        | -               |
| 0.6196 | 5200 | 0.0107        | -               |
| 0.6256 | 5250 | 0.0076        | -               |
| 0.6316 | 5300 | 0.0077        | -               |
| 0.6375 | 5350 | 0.0101        | -               |
| 0.6435 | 5400 | 0.0117        | -               |
| 0.6494 | 5450 | 0.0080        | -               |
| 0.6554 | 5500 | 0.0097        | -               |
| 0.6613 | 5550 | 0.0129        | -               |
| 0.6673 | 5600 | 0.0109        | -               |
| 0.6733 | 5650 | 0.0109        | -               |
| 0.6792 | 5700 | 0.0093        | -               |
| 0.6852 | 5750 | 0.0095        | -               |
| 0.6911 | 5800 | 0.0090        | -               |
| 0.6971 | 5850 | 0.0111        | -               |
| 0.7031 | 5900 | 0.0085        | -               |
| 0.7090 | 5950 | 0.0107        | -               |
| 0.7150 | 6000 | 0.0072        | -               |
| 0.7209 | 6050 | 0.0104        | -               |
| 0.7269 | 6100 | 0.0125        | -               |
| 0.7328 | 6150 | 0.0090        | -               |
| 0.7388 | 6200 | 0.0108        | -               |
| 0.7448 | 6250 | 0.0088        | -               |
| 0.7507 | 6300 | 0.0087        | -               |
| 0.7567 | 6350 | 0.0125        | -               |
| 0.7626 | 6400 | 0.0089        | -               |
| 0.7686 | 6450 | 0.0106        | -               |
| 0.7745 | 6500 | 0.0094        | -               |
| 0.7805 | 6550 | 0.0082        | -               |
| 0.7865 | 6600 | 0.0091        | -               |
| 0.7924 | 6650 | 0.0078        | -               |
| 0.7984 | 6700 | 0.0079        | -               |
| 0.8043 | 6750 | 0.0105        | -               |
| 0.8103 | 6800 | 0.0114        | -               |
| 0.8163 | 6850 | 0.0098        | -               |
| 0.8222 | 6900 | 0.0079        | -               |
| 0.8282 | 6950 | 0.0074        | -               |
| 0.8341 | 7000 | 0.0097        | -               |
| 0.8401 | 7050 | 0.0092        | -               |
| 0.8460 | 7100 | 0.0093        | -               |
| 0.8520 | 7150 | 0.0099        | -               |
| 0.8580 | 7200 | 0.0100        | -               |
| 0.8639 | 7250 | 0.0076        | -               |
| 0.8699 | 7300 | 0.0082        | -               |
| 0.8758 | 7350 | 0.0121        | -               |
| 0.8818 | 7400 | 0.0100        | -               |
| 0.8878 | 7450 | 0.0106        | -               |
| 0.8937 | 7500 | 0.0102        | -               |
| 0.8997 | 7550 | 0.0085        | -               |
| 0.9056 | 7600 | 0.0073        | -               |
| 0.9116 | 7650 | 0.0093        | -               |
| 0.9175 | 7700 | 0.0111        | -               |
| 0.9235 | 7750 | 0.0077        | -               |
| 0.9295 | 7800 | 0.0084        | -               |
| 0.9354 | 7850 | 0.0112        | -               |
| 0.9414 | 7900 | 0.0092        | -               |
| 0.9473 | 7950 | 0.0077        | -               |
| 0.9533 | 8000 | 0.0083        | -               |
| 0.9592 | 8050 | 0.0092        | -               |
| 0.9652 | 8100 | 0.0073        | -               |
| 0.9712 | 8150 | 0.0069        | -               |
| 0.9771 | 8200 | 0.0063        | -               |
| 0.9831 | 8250 | 0.0090        | -               |
| 0.9890 | 8300 | 0.0093        | -               |
| 0.9950 | 8350 | 0.0075        | -               |

### Framework Versions
- Python: 3.12.3
- SetFit: 1.2.0
- Sentence Transformers: 6.3.0
- Transformers: 5.24.0
- PyTorch: 2.15.0+cu132
- Datasets: 5.2.0
- Tokenizers: 0.23.3

## Citation

### BibTeX
```bibtex
@article{https://doi.org/10.48550/arxiv.2209.11055,
    doi = {10.48550/ARXIV.2209.11055},
    url = {https://arxiv.org/abs/2209.11055},
    author = {Tunstall, Lewis and Reimers, Nils and Jo, Unso Eun Seo and Bates, Luke and Korat, Daniel and Wasserblat, Moshe and Pereg, Oren},
    keywords = {Computation and Language (cs.CL), FOS: Computer and information sciences, FOS: Computer and information sciences},
    title = {Efficient Few-Shot Learning Without Prompts},
    publisher = {arXiv},
    year = {2022},
    copyright = {Creative Commons Attribution 4.0 International}
}
```

<!--
## Glossary

*Clearly define terms in order to be accessible across audiences.*
-->

<!--
## Model Card Authors

*Lists the people who create the model card, providing recognition and accountability for the detailed work that goes into its construction.*
-->

<!--
## Model Card Contact

*Provides a way for people who have updates to the Model Card, suggestions, or questions, to contact the Model Card authors.*
-->