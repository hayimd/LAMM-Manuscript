# Methods
## Representations in LAMM

* episodes are encoded in theoretically two ways:
 1. in the changes in activation-based plasticity that result from the sequence of activated words and memory units.  
 2. in any persistent activity still in the memory module at list end -- this activity should preferentially represent/store late list items, and thus be more related to recency effect.  
     * [^ can check this!.. have i already?]
     * Fig 4.18 (S\ref{buffer}) from thesis perhaps shows that recall for early items depends on final memory activity being similar to those items' memory activity, but that middle to late items generally did not have memory activity that correlated with memory state at list end. SO... early items need the buffer, but late ones dont? [Should look at this again]

LAMM proposes a novel, general purpose and type-agnostic memory network characterised by temporary plasticity, limited capacity and active maintenance. This network (referred to herein as the 'memory layer') receives input from, and helps to reactivate, a second network which is assumed to encode the natural language lexicon (the 'item layer'). Moreover, the memory layer is limited in its representational capacity, so that memory network is not simply a 1-1 copy of the lexicon. Although the short term memory theory of LAMM does not depend upon the specifics of long term storage of lexical knowledge, we assume that words are stored and represented in the brain such that they may be perceived discretely and uniquely, and that upon hearing a known word clearly, perception quickly settles upon a single answer. We thus represent word perception and discrimination in LAMM as the unique and exclusive activation of a subset of neurons, with elevated activity in each subset coding a different word and forming an attractor in the neural dynamics -- a so-called winner take all network \cite{Amit1995,Brunel2000}.

Like the winner-take-all dynamic of the item layer, the memory network is also shaped by mutually-excitatory connections within subgroups of neurons and lateral inhibition between them, in order that these subgroups may achieve elevated firing while suppressing other subgroups. Weaker lateral inhibition in the memory layer however allows multiple such subgroups to be active simultaneously, a dynamic called k-winners-take-all. Such elevated activity of a few subgroups in LAMM constitutes the active memory of the item which evoked it, with the identification between item representations and its memory correlates defined by these item-memory excitatory connections.

However, multiple lexicon items may excite the same memory subgroups -- since the memory layer is restricted in size -- so the initial connectivity is not enough to uniquely define a memory to item mapping: This is instead encoded by short term synaptic potentiation \cite{Erickson2010} between item and memory network subgroups during the presentation process. This potentiation temporarily allows memory activity to preferentially excite only certain words' neurons in the lexicon, and vice versa, when before learning such activity may have equally excited other words as well. In this sense, learning in LAMM constitutes a honing of connectivity, or receptive fields (Supplementary Fig. S\ref{mem_rfs}), during each list presentation. These changes are assumed to decay over several minutes.

## Network structure and dynamics

* External excitation to both networks represent afferents from other/ related networks, and attentional control [^ some kind of network structure citation? If LAMM is in PFC, then what are its inputs?]
    * Eg different levels of excitation to memory and lexicon used to kick start recall (increase to memory net, decrease to lexicon).
 
For computational convenience, the networks in this work have been modeled in a coarse-grained fashion using rate-model neuron units, which represent the neuron subgroups mentioned above \cite{Brunel2000,Renart2004}. This approximation assumes that these subgroups share similar inputs and correlated behaviour.

For the simulations shown herein, networks of sizes 90 (60/30 memory/item) and 180 (120/60 memory/item) rate-model cells were used. 1 in 5 units were assigned to each layer's inhibitory population, whose connections projected locally within each layer, but not between them. Each excitatory unit received a large recurrent self-connection, and only very weak lateral connections. For full connectivity details, see Table XX.

All rate-model cells obey the following dynamics:
\[ r(i,t) = F_{r-i}\left[\mathbf{W}(t)\cdot\vec{S}(t) + \mathbf{i}_{\sigma}(t) \right]^+ \]
where \(\mathbf{W}(t)\) are the connections between cells, \(\vec{S}(t)\) is the vector of pre-synaptic gating variables, and \(\mathbf{i}_{\sigma}\) are Gaussian noise traces in the currents for each cell. The function \(F_{r-i}(i)\) defines the neural rate response to current input, chosen to be largely linear but with smooth bounds, in our case the sigmoid functions
\[F_{r-i}(i)=\frac{r_{max}-r}{\left(1+\exp(i_{th.}-i_0)/i_{wd}\right)^{\alpha}}\]
with \(\alpha=1,0.5\) for the lexicon and memory cells respectively. The lower value of \(\alpha\) gives memory units a faster response at low current values, in order to simulate fast spiking inhibitory neurons. 
Synaptic dynamics are contained in the overall pre-synaptic gating variable for each unit _j_, \(S_j(t)\), which depends on two other variables representing the neutransmitter vesicle release and availability probabilities, \(p_j(t)\) and \(D_j(t)\). These together obey
\[ \frac{\tau_p}{1+r\,f\,\tau_p}  \dot{p} = -p + \frac{p_0+r\,f\,\tau_p}{1+r\,f\,\tau_p} \]
\[ \frac{\tau_D}{1+r\,p\,\tau_D}    \dot{D} = -D + \frac{1}{1+r\,p\,D} \]
\[ \frac{\tau_S}{1+r\,p\,D\,s_0\,\tau_S} \dot{S} = -S + \frac{r\,p\,D\,s_0\,\tau_S}{1+r\,p\,D\,s_0\,\tau_S}. \]
Constant \(s_0\) represents the probability that a post-synaptic conductance channel will be open, but we do not define different values for different target units.
Model units also experience spike rate adaptation, which lowers the gain of the unit after a period of continuous activation. This is modeled as an additional hyperpolarizing current \cite{Benda2003}
\[ \frac{\tau_a}{1+r\,\alpha_0\,\tau_a} \dot{a} = -a + \frac{r\,\alpha_0\,\tau_a}{1+r\,\alpha_0\,\tau_a}. \]
A short-term memory network which uses synaptic linking must also have a mechanism for the weakening of those links. The form of plasticity employed in the model is based on a fast-activating, but temporary, bidirectional potentiation of up to 50%, and decaying to baseline over approximately 20 minutes \cite[ASTP, ]{Erickson2010}. ASTP appears to require both consecutive pre- and post-synaptic spiking, which we simplify in the rate-model as a saturating Hebbian rule: Taking the product of each unit's firing rate above a smoothed threshold
\[\label{potent} \Delta W_{i\leftarrow j} = \frac{1}{1+ \exp(-(r_i-\rho_{post})/\gamma)}\frac{1}{1+\exp(-(r_j-\rho_{pre})/\gamma)}\]
is the maximum potentiation increment for the synapse from unit j to unit i, with dynamics
\[\dot{W}_{i\leftarrow j} = \frac{W_{i\leftarrow j}^0 - W_{i\leftarrow j}(t)}{\tau_{fall}} + \Delta W_{i\leftarrow j} \frac{W_{i\leftarrow j}^{max} - W_{i\leftarrow j}(t)}{\tau_{rise}}. \]
Rate thresholds, \(\rho\), and threshold steepness, \(\gamma\), were fit by the optimization, while rate contants \(\tau_{rise} = .5 \textrm{ s}\) and \(\tau_{fall} = 185 \textrm{ s}\) were estimated from the data in \cite{Erickson2010}.

Free recall trials were simulated by successively providing input current pulses to a random subset of item cells, generally lasting 200 ms, every 2 seconds. Following the final 2s presentation interval, a decaying extra stimulus to the inhibitory item cells suppressed activity in the item layer, after which the network was left to run independently. Only the external background currents to the cell populations distinguish the recall stage from presentation: background current to excitatory memory units was roughly halved, whilst all other cells received slight increases. No other parameter changes are made.

Words are considered to be recalled if their item layer units are excited to the high firing rate at any point during the recall period. Repeated reactivations were ignored, so that for determining the recall output order, on the first reactivation is counted. Recall and transition measures were computed as in \cite{Cousins2014}, whence human behavioural data for 7 word lists is taken; data for 5 and 10 word lists is from [Did Katie publish these?]. Computation was performed in MATLAB (_Mathworks_, Natick MA), using the Brandeis High Performance Computing Cluster for the larger simulations. Several model parameters were optimised for greatest overall recall performance as far as practicable, however the model space is very large and a full optimisation is not feasible. 

[Model choices?]

