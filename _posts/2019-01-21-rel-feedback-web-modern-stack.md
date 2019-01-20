---
published: false
layout: post
title: Relevance Feedback on your Web modern stack
---
## Relevance Feedback on your Web modern stack

Relevance feedback is a solid chapter of information retrieval research with many open-sourced implemantion such as [Indri](https://www.lemurproject.org/indri.php), [Anserini](https://github.com/castorini/Anserini) and [Terrier](http://terrier.org/). Together with my PhD supervisor, Claudia Hauff, we wrote a paper about bringing Indri to the modern Web stack and it was recently published as a demo at ECIR 2019. 

````
@inproceedings{moraes2019nodeindri,
  title={node-indri: moving the Indri toolkit to the modern Web stack},
  author={Moraes, Felipe and Hauff, Claudia},
  booktitle={ECIR},
  year={2019}
}
````

**node-indri** is a Node.js module that acts as a wrapper around the Indri toolkit, and thus makes an established IR toolkit accessible to the modern web stack. 

node-indri was implemented with the idea to expose many of Indri's functionalities and provides direct access to document content and retrieval scores for web development (in contrast to, for instance, the [Pyndri](https://github.com/cvangysel/pyndri) wrapper). 

This setup reduces the amount of glue code that has to be developed and maintained when researching search interfaces, which today tend to be developed with specific JavaScript libraries such as React.js, Angular.js or Vue.js.


After developing node-indri, we immedeately incorporated it to [SearchX](http://felipemoraes.github.io/searchx), the open-source collaborative search that I have developed in the last almost two years of PhD. You can find blog posts about it here on [Claudia's webpage](https://chauff.github.io/2018-07-21-collaborative-search/).

SearchX's backend supports the inclusion of many IR backends such as Elasticsearch and Bing API calls. In order to include node-indri as one of the supported backends, we implemented a
_Searcher_ class to provide search results (with or without snippets) in a pagination
manner leveraging feedback documents. 

This class exposes the functionalities of Indri's _QueryEnvironment_ and _RMExpander_ classes through the method search which returns a list of search results in a paginated manner. When a Searcher object is instantiated, it takes a configuration object as argument. When a call to search() is made and no feedback documents are provided as argument, the standard query likelihood model is employed, otherwise the [relevance feedback expander RM3](https://dl.acm.org/citation.cfm?id=383972) is. Depending on the configuration settings, the returned result list may contain document snippets (as provided by Indri's _SnippetBuilder_), document scores, document text and other metadata. An example of this can be found in the image below (notice bold terms on the snippets showing expanded terms for the X query).


Another class we implemented was _Reader_ to enable the rendering of a document’s content when a user has clicked on it, and _Scorer_ to enable our backend to have direct access to documents’ scores for reranking purposes. 

All of these aforementioned classes was used in our user study (more than 300 crowdworkers recruited) published as an Information Retrieval journal [article](https://link.springer.com/article/10.1007/s10791-018-09350-9). 

In our paper we also presented an efficiency analysis of node-indri, comparing it to Indri and Pyndri. We indexed two standard test corpora—Aquaint and ClueWeb12B—with Indri and measured the execution time for 10k queries of the TREC 2007 Million Query track across the three toolkits. Table below presents the overall query execution time of the three toolkits. 

|            | Aquaint     | ClueWeb12B   |
|------------|-------------|--------------|
| Indri      | 29s (0.30s) | 1645s ( 20s) |
| Pyndri     | 25s (1.22s) | 2262s (340s) |
| node-indri | 25s (0.58s) | 2058s (338s) |

As you can see from the table, node-indri can  be  efficiently  used  in  modern  web  backend  development with comparable efficiency to Indri and Pyndri. 

The node-indri repository is open-sourced at [https://github.com/felipemoraes/node-indri](https://github.com/felipemoraes/node-indri).


