---
layout: archive
title: "Datasets"
permalink: /dataset/
author_profile: true
redirect_from:
  - /dataset
---

This page lists all the datasets we have collected and used in our papers. 
To access them, please send an email to me (suliya@iie.ac.cn).

## Ethereum DEFIER

We collected and reconstructed 42 real-world Dapp attack incidents, consisting of 126 semantic-similar transaction clusters with 58,555 transactions.
We manually annotated them and performed a measurement study on our paper [Evil Under the Sun: Understanding and Discovering Attacks on Ethereum Decentralized Applications](http://academicpages.github.io/files/evil.pdf).


### Format

| column                | type    | description                |
| -------------------- | -------- | -------------------- |
| event              | varchar  | the reported event name   |
| **HashKey**          | varchar  | the hash address of transaction          |
| controlUserAddress   | varchar  | the user who initiated the transaction    |
| gameName             | varchar  | the name of the game involved      |
| gameAddress          | varchar  | the address of the game involved         |
| txDate               | Datetime | the time of transaction             |
| txMethod             | varchar  | the name of the function called     |
| smartContractAddress | varchar  | the first contract address called|
| smartContractName    | varchar  | the first contract name called   |
| group             | varchar  | the related attacking group name    |
| stage             | varchar  | the related attack stage           |

### Citation

> @inproceedings{su2021evil,
>  title={Evil Under the Sun: Understanding and Discovering Attacks on Ethereum Decentralized Applications},
>  author={Su, Liya and Shen, Xinyue and Du, Xiangyu and Liao, Xiaojing and Wang, XiaoFeng and Xing, Luyi and Liu, Baoxu},
>  booktitle={30th $\{$USENIX$\}$ Security Symposium ($\{$USENIX$\}$ Security 21)},
>  publisher={USENIX},
>  year={2021}
> }


