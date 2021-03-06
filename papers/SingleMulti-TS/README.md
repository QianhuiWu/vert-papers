# Single-/Multi-Source Cross-Lingual NER via Teacher-Student Learning on Unlabeled Data in Target Language

This repository contains the open-sourced official implementation of the paper:

[Single-/Multi-Source Cross-Lingual NER via Teacher-Student Learning on Unlabeled Data in Target Language](https://www.microsoft.com/en-us/research/publication/single-multi-source-cross-lingual-ner-via-teacher-student-learning-on-unlabeled-data-in-target-language/) (ACL 2020).  
_Qianhui Wu, Zijia Lin, Börje F. Karlsson, Jian-Guang Lou, Biqing Huang_

If you find this repo helpful, please cite the following:

```tex
@inproceedings{wu2020singlemultits,
    title={Single-/Multi-Source Cross-Lingual NER via Teacher-Student Learning on Unlabeled Data in Target Language},
    author={Qianhui Wu and Zijia Lin and B{\"{o}}rje F. Karlsson and Jian-Guang Lou and Biqing Huang},
    year={2020},
    booktitle={2020 Annual Conference of the Association for Computational Linguistics (ACL 2020)},
    url={https://www.microsoft.com/en-us/research/publication/single-multi-source-cross-lingual-ner-via-teacher-student-learning-on-unlabeled-data-in-target-language/},
}
```

For any questions/comments, please feel free to open GitHub issues.


## 🎥 Overview

In this paper, we propose a teacher-student learning method for single-/multi-source cross-lingual NER, via using source-language models as teachers to train a student model on unlabeled data in the target language.
The proposed method does not rely on labelled data in the source languages (only on a trained model) and it is capable of leveraging extra information from unlabelled target-language data, which addresses the limitations of previous label-projection and model-transfer based methods.
We also propose a language similarity measuring method based on language identiﬁcation, to better weight different teacher models in the multi-teacher scenario.
Extensive experiments on benchmark datasets show that our method outperforms the previous state-of-the-art approaches.

![image](https://cdn.nlark.com/yuque/0/2020/png/104214/1592232619080-006df32b-ad05-4967-9ba1-38c344e0ffbb.png)


## 🎯 Quick Start

### Requirements

- python 3.7
- pytorch 1.0.0
- [HuggingFace PyTorch Pretrained mBERT](https://github.com/huggingface/pytorch-transformers.git) (2019.10.27)

Other pip package show in `requirements.txt`.

```bash
pip3 install -r requirements.txt
```

The code may work on other python and pytorch version. However, all experiments were run in the above environment.


### Train and Evaluate

For _Linux_ machines,

```bash
# Single-Source mode:
bash scripts/run_single.sh

# Multi-Source mode:
bash scripts/run_multi.sh
```

For _Windows_ machines,

```cmd
<!-- Single-Source mode: -->
call scripts/run.single.bat

<!-- Multi-Source mode: -->
call scripts/run.multi.bat
```

## 🍯 Datasets

We use the following widely-used benchmark datasets for the experiments:

- CoNLL-2002 [Tjong Kim Sang, 2002](https://www.aclweb.org/anthology/W02-2024/) for Spanish [es] and Dutch [nl] NER;
- CoNLL-2003 [Tjong Kim Sang and De Meulder, 2003](https://www.aclweb.org/anthology/W03-0419/) for English [en] and German [de] NER;

All datasets are annotated with 4 entity types: LOC, MISC, ORG, and PER. Each dataset is split into training, dev, and test sets.

All datasets are CoNLL-style and BIO tagging scheme. In this repo, we only publish a small data sample to validate the code. You can download them from their respective websites: [CoNLL-2003](http://www.cnts.ua.ac.be/conll2003/ner.tgz), and [CoNLL-2002](http://www.cnts.ua.ac.be/conll2002/ner.tgz).
And place them in the correct locations: `data/conll/ner/${language}/${train_type}.txt`.


## 📋 Results

We report the zero-resource cross-lingual NER results of the proposed Single/Multi-TS approach on the 3 target languages, alongside those reported by prior state-of-the-art methods.

* Performance comparisons on Single-Source:

|                                                                                  | es        | nl        | de        |
| -------------------------------------------------------------------------------- | --------- | --------- | --------- |
| [Tackstrom _et_ _al_.[2012]](https://www.aclweb.org/anthology/N12-1052/)         | 59.30     | 58.40     | 40.40     |
| [Tsai _et_ _al_.[2016]](https://www.aclweb.org/anthology/K16-1022/)              | 60.55     | 61.56     | 48.12     |
| [Ni _et_ _al_.[2017]](https://www.aclweb.org/anthology/P17-1135/)                | 65.10     | 65.40     | 58.50     |
| [Mayhew _et_ _al_.[2017]](https://www.aclweb.org/anthology/D17-1269/)            | 65.95     | 66.50     | 59.11     |
| [Xie _et_ _al_.[2018]](https://www.aclweb.org/anthology/D18-1034/)               | 72.37     | 71.25     | 57.76     |
| [Wu and Dredze [2019]](https://www.aclweb.org/anthology/D19-1077/)               | 74.50     | 79.50     | 71.10     |
| [Moon _et_ _al_.[2019]](https://arxiv.org/abs/1912.01389)                        | 75.67     | 80.38     | 71.42     |
| [Wu _et_ _al_.[2019]](https://www.aaai.org/Papers/AAAI/2020GB/AAAI-WuQ.5015.pdf) | 76.75     | 80.44     | 73.16     |
| **Single-TS**                                                                    | **76.94** | **80.89** | **73.22** |

* Performance comparisons on Multi-Source:

|                                                                                  | es        | nl        | de        |
| -------------------------------------------------------------------------------- | --------- | --------- | --------- |
| [Tackstrom _et_ _al_.[2012]](https://www.aclweb.org/anthology/N12-1052/)         | 61.90     | 59.90     | 36.40     |
| [Rahimi _et_ _al_.[2019]](https://www.aclweb.org/anthology/P19-1015/)            | 71.80     | 67.60     | 59.10     |
| [Chen _et_ _al_.[2019]](https://www.aclweb.org/anthology/P19-1299/)              | 73.50     | 72.40     | 56.00     |
| [Moon _et_ _al_.[2019]](https://arxiv.org/abs/1912.01389)                        | 76.53     | **83.35** | 72.44     |
| **Multi-TS**                                                                     | **78.00** | 81.33     | **75.33** |


## Contributing

This project welcomes contributions and suggestions. Most contributions require you to agree to a
Contributor License Agreement (CLA) declaring that you have the right to, and actually do, grant us
the rights to use your contribution. For details, visit https://cla.opensource.microsoft.com.

When you submit a pull request, a CLA bot will automatically determine whether you need to provide
a CLA and decorate the PR appropriately (e.g., status check, comment). Simply follow the instructions
provided by the bot. You will only need to do this once across all repos using our CLA.

This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).
For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or
contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.
