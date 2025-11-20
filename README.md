# Packet Signature Detector

Python-based lab for experimenting with machine-learning packet signature detection in cybersecurity contexts. The project ships as a self-contained notebook that synthesizes packet payloads, injects malicious keyword signatures, trains a Naive Bayes model, evaluates performance, and raises alerts for suspicious payloads using only standard data-science libraries.

## Features
- Synthetic packet payload generator with customizable malicious keyword dictionary.
- Multinomial Naive Bayes pipeline combining text n-grams and keyword-hit scores via `scikit-learn`.
- Evaluation outputs (classification report, confusion matrix) plus human-readable alert logs.
- Helper function `detect_malicious_packets` for scoring arbitrary payloads and extracting matched signatures.

## Requirements
- Python 3.9+
- `pandas`, `numpy`, `matplotlib`, `scikit-learn`, `scipy`
- Optional: `nltk` if you extend tokenization or text preprocessing.

Install dependencies (user scope, no admin needed):

```
python3 -m pip install --user pandas numpy matplotlib scikit-learn scipy
```

## Usage
1. **Open the notebook**: launch `packet_signature_detector.ipynb` in Jupyter, VS Code, or Google Colab.
2. **Run all cells** top-to-bottom to synthesize data, train the model, and view evaluation plots.
3. **Inspect alerts**: sample payloads at the end of the notebook demonstrate how malicious signatures are flagged.
4. **Bring your own data**: replace `synthesize_packets` with a parser that loads payloads from PCAP/IDS logs and refresh `MALICIOUS_KEYWORDS` from threat intel feeds.
5. **Automate detection**: call `detect_malicious_packets(payloads)` from your pipeline to produce probabilities and keyword hits, then forward `ALERT` messages into monitoring/SIEM tooling.

## Repository Notes
- Executed notebook artifacts (`packet_signature_detector-ran.ipynb`) are ignored by default via `.gitignore`; keep them local unless you need the captured output.
- Local Jupyter/IPython config directories (`.jupyter/`, `.ipython/`) are also ignored to keep the repo clean.

## Next Steps
- Swap in real packet captures for the synthetic dataset.
- Expand the keyword/signature list and retrain regularly as new intel arrives.
- Persist the trained pipeline or export it for deployment in detection services.

