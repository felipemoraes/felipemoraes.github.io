---
layout: post
title: "Effectiveness of Dynamic Search Systems"
date: 2017-07-05 16:25:06 -0700
comments: false
---

Back in 2016, I decided to take an Information Theory course at UFMG lectured by Mário S. Alvim as part of my Master's coursework. In this course, Mário asks his students to write a report about a topic in information theory (not covered by him during the semester) or to model something in their research field using concepts of information theory. I decided to go with the latter, however, I chose a topic of Mário expertise, information flow, and then I wrote a short report on how we could model information flow in dynamic information retrieval. 

Months later, Mário and I reviewed the report and together with my Master's supervisor, Rodrygo Santos, we decided to make this modeling available to the IR community. Thus, we got this study accepted as a short paper at ICTIR 2017:

```bibtex
@inproceedings{moraes2017ictir-b,
  author = {Felipe Moraes and Mário S. Alvim and Rodrygo L. T. Santos},
  title = {Modeling Information Flow in Dynamic Information Retrieval},
  booktitle = {Proceedings of the 3rd ACM International Conference on the 
    Theory of Information Retrieval},
  year = {2017},
  address = {Amsterdam, The Netherlands}
}
```

Here's the abstract of our paper:

> User interaction with a dynamic information retrieval (DIR) system can be seen as a cooperative effort towards finding relevant information. In this cooperation, the user provides the system with evidence of his or her information need (e.g., in the form of queries, query reformulations, relevance judgments, or clicks). In turn, the system provides the user with evidence of the available information (e.g., in the form of a set of candidate results). Throughout this conversational process, both user and system may reduce their uncertainty with respect to each other, which may ultimately help in finding the desired information. In this paper, we present an information-theoretic model to quantify the flow of information from users to DIR systems and vice versa. By employing channels with memory and feedback, we decouple the mutual information among the behavior of the user and that of the system into directed components. As a result, we are able to measure: (i) by how much the DIR system is capable of adapting to the user; and (ii) by how much the user is influenced by the results returned by the DIR system. We discuss implications of the proposed framework for the evaluation and optimization of DIR systems.

I hope that this paper inspires some researchers in bringing information theory foundations to IR.
