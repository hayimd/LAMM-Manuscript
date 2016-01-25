# Methods
Representation

* firing rate models, approximate groups of similarly connected neurons at single units
* attractor states in network, corresponding to bistability of unit firing rates
 * may have 1 or more units firing at elevated rates persistently
* model both the long term memory for words (lexicon) and a dedicated but type-independent memory module
 * lexicon is coded localist, with distince units representing different words; but assume in reality that there is a degree of distributed coding, where word representatiosn share active neurons, representing semantic of other informative relationships between words [< need citation for localist lexicon, check Paul's papers]
 * memory module is designed to hava a measure of distributed/overlapping representaiton, in order to ecode conjunctions and context. (cf \cite{Howard2002,Davelaar2005})
* episodes are encoded in theoretically two ways:
 1. in the changes in activation-based plasticity that result from the sequence of activated words and memory units.  
 2. in any persistent activity still in the memory module at list end -- this activity should preferantially represent/store late list items, and thus be more related to recency effect.  
     * [^ can check this!.. have i already?]

Network structure

* Two layer network. 1st representing the lexicon, WTA. 2nd the memory module, designed as a k-winners take all attractor net [< but weakly so? strenghtened by plasticity? CHECK THIS, noplastic.]
* Inhibitory units within each layer inhibit own layer units but not those in other layer.
* Excitatory units have strong self and interlayer connections, but weak lateral connectivity to units within their own layer. Exc. units project connections to both own and other layer inhibitory cells.
* All excitatory connections are plastic, and change according to short-term associative potentiating rule, approximating ASTP \cite{Erickson2010a}. Max potentiation is ~ 40%, but differs by connection type. Connection and plastiity parameters can be found in Table X.
* External excitation to both networks represent afferents from other/ related networks, and attentional control [^ some kind of network structure citation? If LAMM is in PFC, then what are its inputs?]
    * Eg different levels of excitation to memory and lexicon used to kick start recall (increase to memory net, decrease to lexicon).
* All units have non-linear synaptic dynamics (faciliation and depression), as well as spike rate adaptation.  

Networks composed of rate model cells \cite{Brunel2002b,Renarr2004}, representing groups of correlated, similarly connected neurons. They obey following dynamics
\[ r(i,t) = F_{r-i}\left[\mathbf{W}(t)\cdot\vec{S}(t) + i_{\sigma}(t) \right]^+\]
where \(F_{r-i}(i)\) is the neural rate response function to current input, chosen to be largely linear but with smooth bounds, in our case the sigmoid functions
\[F_{r-i}(i)=\frac{r_{max}-r}{(1+\exp(i_{th.}-i_0)/i_{width})^{\alpha}}\]
with \(\alpha=1,0.5\) for the lexicon and memory cells respectively. The lower value of \(\alpha\) gives memory units a faster response at low current values, in order to simulate fast spiking inhibitory neurons. Synaptic dynamics are contained in the overall pre-synaptic gating variable for each unit _j_, \(S_j(t)\), which depends on two other variables representing the neutransmitter vesicle release and availability probabilities, \(p_j(t)\) and \(D_j(t)\). These together obey
\[ \frac{\tau_p}{1+rf\tau_p}  \dot{p} = -p + \frac{p_0+rf\tau_p}{1+rf\tau_p} \]
\[ \frac{\tau_D}{1+rp\tau_D}    \dot{D} = -D + \frac{1}{1+rpD} \]
\[ \frac{\tau_S}{1+rpD s_0\tau_S} \dot{S} = -S + \frac{rpDs_0\tau_S}{1+rpDs_0\tau_S} \].
\(s_0\) represents the proability that a post-synaptic conductance channel will be open, but we do not define different values for different target units.
Model units also 


Model choices

- Exact connectivity is arbitrary..
    - Projections from lexicon to memory are slightly sparse, in order to increase selectivity [< this perhaps is why the network is so strongly driven by I->M connections!]
    - Levels of faciliation, depression, adaptation [< chosen... how?] 
    - Levels of max potentiation, chosen via optimisation over total recall probability.
