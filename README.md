# hse\_hw2\_chip

[Colab](https://colab.research.google.com/drive/1Y8K70zhbJTSiIjMBAaAUMBVQOGsylmwG)

**TODO permissions**

## Часть 1

### FastQC / MultiQC

Количество чтений

![](img/fastqc_sequence_counts_plot.svg)

Большинство чтений с высоким качеством

![](img/fastqc_per_sequence_quality_scores_plot.svg)

Заметно падение качества в конце чтений из ENCFF630PTQ (контроль)

![](img/fastqc_per_base_sequence_quality_plot.svg)

Много N в 36 основании чтений из ENCFF630PTQ (этим объясняется падение качества на предыдущем графике)

![](img/fastqc_per_base_n_content_plot.svg)

Есть проблемы с ENCFF630PTQ (см. выше). Также заметна неравномерность в распределении оснований (Per Base Sequence Content), но это может быть нормальной ситуацией для chip-seq.

![](img/fastqc-status-check-heatmap.svg)

Удаление ридов с низким качеством:

```bash
trimmomatic SE -phred33 ENCFF630PTQ.fastq ENCFF630PTQ_trimmed.fastq LEADING:3 TRAILING:3 SLIDINGWINDOW:4:15 MINLEN:36
```

Повторный анализ качества:

![](img/fastqc_per_base_sequence_quality_plot_2.svg)

![](img/fastqc_per_base_n_content_plot_2.svg)
