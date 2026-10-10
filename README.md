# Прогноз по доходам и расходам

Телефонная кампания банка: звонок стоит $2, согласие на срочный депозит приносит $10. Логистическая регрессия решает, кому звонить. Модель выбирается по прибыли, а не только по ROC-AUC.

Разбор: [`term_deposit_profit.ipynb`](term_deposit_profit.ipynb).

На пяти фолдах при пороге 0.5 средняя прибыль около **$1 485** (разброс около $230), операторам уходит около **$640** на фолд. Снижение порога примерно до 0.2 поднимает полноту и прибыль примерно до **$2 700**. Коэффициент регуляризации на это почти не влияет: лучшее `C` меняется от запуска к запуску. Прибыль настроенной модели выше на каждом фолде (парный t-критерий, p ≈ 0.0001).

## Данные

[UCI Bank Marketing](https://archive.ics.uci.edu/dataset/222/bank+marketing), файл `bank-additional/bank-additional-full.csv`. В репозиторий не входит.

```bash
wget https://archive.ics.uci.edu/ml/machine-learning-databases/00222/bank-additional.zip
unzip bank-additional.zip
```

S. Moro, P. Cortez, P. Rita. *A Data-Driven Approach to Predict the Success of Bank Telemarketing.* Decision Support Systems, 2014.

## Запуск

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
jupyter lab term_deposit_profit.ipynb
```
