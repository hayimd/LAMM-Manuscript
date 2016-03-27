## Analaysis of dynamics

* correlations showing memory activity driven mainly by projective connectivity
* recall of words vs initial biases, c.f receptive fields -- seemingly a broad null result
  - BUT at least show \(\Delta W\) vs intial \(W\) 
* recall vs list length scales as power law \cite{Murdock1962} (Fig. \ref{scaling})
sequences dont always follow strongest links, c.f. \cite{Romani2013} transition model
  - comparison of recall plasticity vs none sequences
* recall increases with rehearsal for early items \cite{Rundus1971,Lansner2013} (Fig. S\ref{rehearsal})

LAMM is partly motivated by the question of how the computational idea of a buffer might be implemented biologically. Since the aim is not to re-represent all of LTM in an vast array of primary buffers -- the combinatorial explosion warned of by Baddeley's critics \cite(Postle2006} -- the challenge becomes how to identify a limited number of memory activity states with certain stimuli temporarily. LAMM's answer to this is to reinforce already heterogeneous biases in connectivity via synaptic potentiation, in a one-shot, online learning process. Associative short term potentiation as recently identified by \citet{Erickson2010} (ASTP) provides an ideal candidate plasticity, with a fast onset and medium-term decay. Given the dependence on both pre- and post-synaptic firing rates and post-synaptic bursting, \citet{Miller2010} propose a 'quadruplet' rule of two pre- and two post-synaptic spikes in their spike-timing dependent model for ASTP. For our rate model units, we take the most general interpretation in which synaptic increases depend on a threshholded product of the pre- and post-synaptic rates (Eq. \ref{potent}).

We should like to know, therefore, how much the initial heterogeneity contributes to the dynamics in LAMM, and how much varies trial to trial. Variability may allow more flexible encoding, especially for disambiguating repeated items in complex lists where it is desirable that the same item can be bound to  different memory activities in different contexts. On the other hand, heterogeneity in the item-memory connections is needed to ensure that new items are able to evoke different memory activity and not just reinforce those active. Fig. \ref{memcorrs}a shows correlations in the memory activity representing activations of different items in different lists. For a given initialisation of network connectivity, the memory activity representing an item is highly consistent over different lists, indicating that memory activity is largely driven by the initial item-memory connectivity, and only slightly affected by prior history. By contrast, memory activity exhibits no knowledge of list position, showing no correlation between memory activity for the same item positions in different lists (\ref{memcorrs}b). \ref{memcorrs}c confirms the dependence on initial connectivity, showing strong correlation in memory representations of a single item between lists, but not between network initialisations.



## Analysis of robustness <-- not done

* what effect to parameter changes have?
 * how much heterogeneity is there built in?
 * how does this compare to large paramter changes?