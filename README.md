<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [Evaluating Gender Bias in Machine Translation](#evaluating-gender-bias-in-machine-translation)
  - [Requirements](#requirements)
  - [Install](#install)
  - [Running our experiments](#running-our-experiments)
  - [Adding an MT system](#adding-an-mt-system)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

# Evaluating Gender Bias in Machine Translation

This repo contains code and data for reproducing the experiments in "Evaluating Gender Bias in Machine Translation" (Stanovsky et al., 2019).

## Requirements
* [fast_align](https://github.com/clab/fast_align) -- install and point an environment variable called FAST_ALIGN_BASE to its root folder (the one containing a `build` folder).

## Install
`./install.sh`

## Running our experiments 
This is the entry point for all our experiments: [scripts/evaluate_all_languages.sh](scripts/evaluate_all_languages.sh).
Run all of the following from the  `src` folder. Output logs will be written to the given
path.
* For the general accuracy number, run:

        ../scripts/evaluate_all_languages.sh ../data/aggregates/en.txt  path/to/output/folder/

* For evaluating *pro*-sterotypical translations, run:

        ../scripts/evaluate_all_languages.sh ../data/aggregates/en_pro.txt  path/to/output/folder/

* For evaluating *anti*-sterotypical translations, run:

        ../scripts/evaluate_all_languages.sh ../data/aggregates/en_anti.txt  path/to/output/folder/

## Adding an MT system
1. Translate the file in `data/aggregates/en.txt` to the languages in our evaluation method.
2. Put the transalations in `translations/your-mt-system/en-targetLanguage.txt` where each sentence is in a new line, which has the following format `original-sentence ||| translated sentence`. See [this file](translations/aws/en-fr.txt) for an example.
3. Add your translator in the `mt_systems` enumeration in the [evaluation script](scripts/evaluate_all_languages.sh).

