# Introduction
The existence and nature of a distinction between short and long term memory has been debated for over a century \cite{James1890,Jonides2008}. Associative buffer models, such as Raaijmakers and Shiffrin’s Search of Associative Memory \cite[SAM, ]{Raaijmakers1981}, present computational implementations of the highly influential theory of separate but interacting short and long-term memory processes \cite{Atkinson1968,Baddeley1974}.

The features of SAM illustrate the canonical dual-storage algorithm: Items to be recalled are entered into a temporary storage buffer, replacing prior items if the buffer is full, and therein form episodic associations with other buffer items, and perhaps also a context marker. Those associations then serve as cues for consecutive recalls, producing many of the familiar dynamics of list recall performance \cite{Davelaar2005}. 

The Linking via Active Maintenance Model aims to explore the biological feasibility of associative buffer memory theories by implementing them as neuronal networks. Additionally, advance the debate between dual- and single-memory models \cite{Brown2002,Howard2002,Cowan2008} by arguing that, when implemented neuronally, associative buffer networks incorporate temporal context dynamics \cite{Usher2008}. Finally, LAMM’s architecture is based upon prior work showing that buffer mediated associations are necessary to explain the effects of degraded stimuli on recall \cite{Piquado2010,Miller2010,Cousins2014}.

## Word list recall

- Is an experimental paradigm with long history as a model system for short term memory and rich behavioural phenomena.

Recall for sequentially presented lists of items has long been a key experimental paradigm for revealing hidden structure in memory dynamics. Dependencies on list-position, presentation timing, temporal contiguity, effects of rehearsal, intra- and inter-list interference, categorical and acoustic relatedness, and scaling laws have all been observed \cite{Murdock1962,Rundus1971,Kahana1996,Golomb2008,Grenfell-Essam2012,Cowan2008a,Farrell2011a} (more!). Disruptions and distractions have been used to probe the stages and modalities of memory encoding \cite{Carroll2012,Elliot1998,Spataro2013,Cowan2008} including the finding of a retroactive effect indicating that encoding into short term memory continues beyond the removal of the stimulus \cite{Rabbitt1968,Cousins2014}.

- several models proposed, notably differential memory for late list items key support for the idea of the short term memory buffer.

A key point of disagreement within the literature is whether memory for recently perceived list items is computed by the same processes that encode and retrieve general long term memory (LTM) (the 'unitary view'), or by dedicated, temporally limited 'short-term' processes (the 'dual-store' or 'dual-process' view) \cite{Raaijmakers1981a,Davelaar2005,Sederberg2008}. Generally, unitary models have relied on representations of distinctiveness between items to be remembered, which contain some invariance to timsecales \cite{Brown2002,Howard2002}, whilst dual-process models have posited a separate, short-term, actively maintained or reverberatory storage, or 'buffer' \cite{Baddeley1974,Raaijmakers1981,Davelaar2005} (more!). More recently, structural similarities have been pointed out between actual computational implementations of the different theories \cite{Usher2008}, and modeling has suggested that both distinctiveness and buffer mechanisms may be necessary \cite{Piquado2010,Miller2010,Cousins2014}. In most cases such short-term processes are assumed to contribute most strongly to memory for only very recently perceived stimuli, such as the ends of a word list, so that theoretical disagreement focuses on how these 'recent' items are remembered.


## Memory theories, summary of trends

- Buffers (active maintenance) vs similarity (interference)

The debate regarding the mechanisms operating in list recall tasks is a front in the larger debate about short-term memory in general: that between buffer maintenance and attention-driven theories. Buffer theories posit that the most recently perceived stimuli are maintained in short term memory buffers via active mechanisms \cite{Baddeley1974,Baddeley2010,Davelaar2005,Grossberg1978,Bradski1994}. This view has won empirical support, especially from electophysiological recordings from behaving primates \cite{Funahashi1989,Fuster1971,Fuster1973,Miyashita1988,Miyashita1988a}, coalescing into a 'standard model' of short term memory \cite{Goldman-Rakic1987,Goldman-Rakic1990,Courtney2004,Postle2006}.

Attention driven theories propose that short-term memory is simply the process of temporarily re-activating, or 'attending' to, memory representations stored in LTM \cite{Cowan1993,Cowan2008} (more?). (Such theories reject Baddeley's \cite{Baddeley1974} physical separation of short- from long-term processing, and instead propose a functional separation only, consistent with Atkinson & Shiffrin's \cite{Atkinson1968} original proposal, and, in fact, the Hebbian idea of 'transient memory' \cite{Hebb1949}). Multiple LTM memories can be reactivated at the same time, with only a subset of these being the 'focus' of attention as generally understood, allowing for gradations in the level of focus and active maintenance \cite{Cowan2008}: In the case of word list recall, the representation of the current word would be reactivated most strongly and be in 'focus', with less recent words fading to baseline.

In this way \cite{Cowan2008} leaves open the possibility for both decay of active maintenance and interference between stored representations as mechanisms of forgetting. This is a further site of contest between buffer and attentional theories \cite{Jonides2008}, with attentional theories traditionally operating on distinctiveness \site{Nairne1997,Brown2002,Brown2008,Howard2002} whereby the most distinctive 


- Whether there are dedicated memory modules or whether short term memory is effected by attentional processes \cite{Postle2006,Jonides2008,Courtney2004}
- \cite{Davelaar2005} and \cite{Rabbitt1968} -> \cite{Miller2010} necessity of buffers (dual mechanisms)

## Summary of modeling approaches
Process models, recall probability laws, biological mechanistic models

* Processes as algorithmic, simulated time dependent
* Recall laws as defining a probability for recalls given parameters
* Specific mechanistic/ biological implementations, \cite{Lisman1995,Grossberg1978}

Survey of important / relevant models

* process models \cite{Raaijmakers1981,Davelaar2005,Cousins2014}
* similarity models \cite{Howard2002,Brown2002,Brown2007}
* dual models? \cite{Sederberg2008,Piquado2010}
* Primacy/PFR \cite{Farrell2012a,Lehman2013}

Other models \cite{Szatmary2010,Machens2005}