# Курсовой проект: влияние обогащения данных на качество и устойчивость моделей

## Цель

Сравнительный анализ влияния ручного и искусственного обогащения данных на качество и устойчивость обучения моделей машинного обучения. Текущий этап посвящён воспроизводимому EDA исходного датасета RuReviews. Синтетические данные не генерируются, модели не обучаются.

## Структура проекта

```text
.
├── README.md
├── docs/
├── notebooks/
├── reports/
├── data/
├── src/
├── pyproject.toml
└── uv.lock
```

Каталог `data/` и файлы `*.csv` исключены из Git. Исходный CSV должен находиться локально по указанному пути; в репозиторий он не добавляется.

## Окружение

- Python `>=3.12`; проверено на Python `3.12.4`.
- Управление зависимостями: [uv](https://docs.astral.sh/uv/).
- Основные библиотеки: pandas 3.1.0, numpy 2.5.4, matplotlib 3.11.2, seaborn 0.13.2, scipy 1.18.1, scikit-learn 1.9.1.
- Jupyter: jupyterlab 4.6.4, ipykernel 7.4.0, nbconvert 7.17.2, nbformat 5.11.1.
- Параметры зафиксированы в `pyproject.toml` и `uv.lock`; точные версии выполнения — в `reports/environment.txt`.

## Запуск

Из корня проекта:

```powershell
uv sync --locked
```

Проверить наличие файла `data/women-clothing-accessories.3-class.balanced.csv`, затем открыть ноутбук:

```powershell
uv run jupyter lab
```

Открыть `notebooks/01_rureviews_eda.ipynb`, выбрать kernel `Python 3 (uv)` / `python3` и выполнить все ячейки сверху вниз.

Альтернативный воспроизводимый запуск без JupyterLab:

```powershell
uv run jupyter nbconvert --to notebook --execute --inplace notebooks/01_rureviews_eda.ipynb --ExecutePreprocessor.timeout=900 --ExecutePreprocessor.kernel_name=python3
```

Команда перезаписывает outputs ноутбука и обновляет `reports/eda_metrics.json`, `reports/environment.txt` и графики в `reports/figures/`.
