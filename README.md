# TED-QDB: TED-talk Questions and Discourse Bank

This repository combines two existing annotation layers for six English TED talks:

- [TED-MDB](https://github.com/MurathanKurfali/Ted-MDB-Annotations): Discourse relations (in the framework of the Penn Discourse TreeBank); only the English portion.
- [TED-Q](https://github.com/amore-upf/ted-q): Evoked questions, obtained by presenting snippets to crowdsourcees and asking "Which question does this evoke?", as well as information about question triggers and answers.

The hope is that providing their integration in a convenient format will facilitate future research on the (mis)alignment of discourse relations and implicit questions. For more background read our [paper](https://aclanthology.org/2020.lrec-1.141/).

## Data

In the `data` you'll find:

- `questions.jsonl`: what you are likely interested in: evoked questions, with integrated information about discourse relations, see below.
- `sources.jsonl`: just the original ted-talks, with their IDs as referred to in the other files.
- `comparisons.jsonl`: averaged judgments of how 'similar' two questions (evoked by the same snippet) are, on a scale from 0 (unrelated) 3 (equivalent).

### Fields in `questions.jsonl`

Fields derived from TED-Q:

- `id`
- `source_id`: ID of the TED-talk, links into `sources.jsonl`.
- `source_cutoff`: the participant who entered the question saw the TED-talk up to this point (character offset)
- `question_text`: the question they entered.
- `trigger_span`: which words they highlighted as 'triggering' the question (character start and end). 
- `answer_text`: when more of the TED talk was revealed, participants would indicate whether their question was answered; if so, this key stores the answer in their own words.
- `answer_span`: which words they highlighted as answering their question (if any)
- `answer_score`: degree to which their question was answered, on a scale from unanswered (1) to completely answered (5).

Fields derived from TED-MDB:

- `snippet_has_arg1_of`: a list of PDTB senses, in case the snippet that evoked the question contains the first argument of a discourse relation (and _not_ the relation's connective or the second argument).
- `trigger_has_arg1_of`: a list of PDTB senses, in case, in addition to the previous, the question's trigger overlaps with the first argument.
- `answer_has_arg2_of`: a list of PDTB senses, in case the answer span overlaps with the second argument of a discourse relation.


## Attribution ##

If you use this resource, please cite our LREC paper introducing TED-Q:

```
    @inproceedings{westera2019lrec,
      title={TED-Q: TED Talks and the Questions they Evoke},
      author={Matthijs Westera and Laia Mayol and Hannah Rohde},
      booktitle = "Proceedings of the Twelfth International Conference on Language Resources and Evaluation (LREC'2020)",
      year = 	 "2020",
      month = 	 "May",
      date =     "13-15",
      address =  "Marseille, France",
      publisher = "European Language Resource Association (ELRA)",
    }
```

And also cite the authors of the TED-MDB dataset, part of whose annotations we included in this release:

```
    @article{zeyrek2019ted,
      title={TED Multilingual Discourse Bank (TED-MDB): a parallel corpus annotated in the PDTB style},
      author={Zeyrek, Deniz and Mendes, Amalia and Grishina, Yulia and Kurfali, Murathan and Gibbon, Samuel and Ogrodniczuk,    Maciej},
      journal={Language Resources and Evaluation},
      pages={1--38},
      year={2019},
      publisher={Springer}
    }
```

```
    @inproceedings{zeyrek2018multilingual,
      title={Multilingual Extension of PDTB-Style Annotation: The Case of TED Multilingual Discourse Bank.},
      author={Zeyrek, Deniz and Mendes, Amalia and Kurfali, Murathan},
      booktitle={LREC},
      year={2018}
    }
```