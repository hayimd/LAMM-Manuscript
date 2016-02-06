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

Networks composed of rate model cells \cite{Brunel2002b,Renart2004}, representing groups of correlated, similarly connected neurons. They obey following dynamics
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
A short-term memory network which uses synaptic linking must also have a mechanism for the weakening of those links. The form of plasticity employed in the model is based on a fast-activating, but temporary, bidirectional potentiation of up to 50%, and decaying to baseline over approximately 20 minutes \cite[ASTP, ]{Erickson2010a}. ASTP appears to require both consecutive pre- and post-synaptic spiking, which we simplify in the rate-model as a saturating Hebbian rule: Taking the product of each unit's firing rate above a smoothed threshold
\[\Delta W_{i\leftarrow j} = \frac{1}{1+ \exp(-(r_i-\rho_{post})/\gamma)}\frac{1}{1+\exp(-(r_j-\rho_{pre})/\gamma)} \]
is the maximum potentiation increment for the synapse from unit j to unit i, with dynamics
\[\dot{W}_{i\leftarrow j} = \frac{W_{i\leftarrow j}^0 - W_{i\leftarrow j}(t)}{\tau_{fall}} + \Delta W_{i\leftarrow j} \frac{W_{i\leftarrow j}^{max} - W_{i\leftarrow j}(t)}{\tau_{rise}}. \]
Rate thresholds, \(\rho\), and threshold steepness, \(\gamma\), were fit by the optimization, while rate contants \(\tau_{rise} = .5 \textrm{ s}\) and \(\tau_{fall} = 185 \textrm{ s}\) were estimated from the data in \cite{Erickson2010a}.


Model choices

- Exact connectivity is arbitrary..
    - Projections from lexicon to memory are slightly sparse, in order to increase selectivity [< this perhaps is why the network is so strongly driven by I->M connections!]
    - Levels of faciliation, depression, adaptation [< chosen... how?] 
    - Levels of max potentiation, chosen via optimisation over total recall probability.
