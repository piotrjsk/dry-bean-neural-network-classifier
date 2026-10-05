# 🫘 Dry Bean Neural Network Classifier

Projekt nauczania maszynowego poświęcony klasyfikacji siedmiu gatunków fasoli zwyczajnej (*Phaseolus vulgaris L.*) przy użyciu wielowarstwowych perceptronów (MLP) zaimplementowanych w bibliotece **PyTorch**.

---

## 📋 Opis projektu

Głównym celem projektu jest zbudowanie i porównanie architektur sieci neuronowych pod kątem precyzji klasyfikacji cech morfologicznych nasion fasoli. Zbiór danych pochodzi z repozytorium **UCI Machine Learning Repository**.

### Kluczowe elementy i eksperymenty:
* **Analiza i obróbka danych (EDA):** Standaryzacja cech (`StandardScaler`), analiza korelacji oraz podział na zbiory treningowy, walidacyjny i testowy.
* **Badanie architektury sieci:** Porównanie modeli o różnej liczbie warstw ukrytych oraz dopasowanie funkcji aktywacji (`ReLU`, `Tanh`, `LeakyReLU`).
* **Optymalizacja procesu uczenia:** Porównanie optymalizatorów (`Adam` vs `SGD`) oraz badanie wpływu regularyzacji (`Weight Decay` / L2 penalty).
* **Zapobieganie przeuczeniu:** Zastosowanie mechanizmu *Early Stopping* na podstawie straty walidacyjnej (*Validation Loss*).

---

## 📁 Struktura projektu

```text
dry-bean-neural-network-classifier/
├── data/
│   └── dry_bean_dataset.xlsx          # Zbiór danych UCI
├── notebooks/
│   └── dry_bean_classification.ipynb  # Główny Jupyter Notebook z eksperymentami
├── .env.example                       # Przykładowe zmienne środowiskowe
├── .gitignore                          # Pliki ignorowane przez system Git
├── README.md                          # Dokumentacja projektu
└── requirements.txt                   # Lista wymaganych bibliotek Python
```


DO ZROBIENIA