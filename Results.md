# Results

## That the model recalls as broadly intended

* can recall sequences imperfectly (Figure \ref{sequence})

The firing-rate model LAMM \cite{Cousins2014} successfully encodes and recalls item lists after a single presentation. Figure \ref{sequence} shows the activities of the 90 rate units during the experimental task. An item list consisting 12 of the 24 item units (cells 61-84) is presented to the network as a sequence of short external inputs (black bars beneath the x-axis), lasting 200 ms, every 2s. This presentation is perceived by the LTM item layer by the excitation of each item unit into its stable high firing state, until it is kicked back down by the increased lateral inhibition (disynaptic, through inhibitory cells 85-90) evoked by the excitation of the next unit. Item activation evokes memory layer activity via strong, slightly sparse (?%) excitatory projections between the layers, which in turn project back to the items, although more weakly and uniformly (Table ?). During this activity, associative short term plasticity (ASTP) continuously strengthens connections from excitatory cells by up to ~35% (Table ?), including to inhibitory populations, both within and between layers.

After the last 2s presentation period (broken magenta line), external currents to the layers are slightly altered (Table ?), while a short increased input to the inhibitory Item layer units halts activity in the Item layer, easing off after 200 ms (solid magenta line). Thereafter, the network is left to evolve on its own, resulting in the spontaneous reactivation of 8 of the 12 presented items [_Check this, and run longer!_], which are recorded as recalled items. Note that plasticity is ongoing during the recall stage and is not switched off (Fig S?), as in other models \cite{Lansner2013}.

Although items are often recalled in sequential order, recall also jumps around the list. This is quantified by the conditional response probability curves \cite[CRP, ]{Howard1999}, which compute the probability, over all lists presented, of recalling the word presented at position \(i+j\) after recalling the word presented at position \(i\). Figure \ref{crp} shows that LAMM's output ordering well matches experimental behaviour, and is producing free recall. On the other hand, LAMM's overall recall behaviour, as characterised by the serial position curves, is not consistent with the data (Fig \ref{listlength}), showing a largely flat average dependence on presentation position and neither primacy nor recency. Interestingly, LAMM does exhibit the correct scaling of reduced overall recall for longer lists, which we will return to later.

LAMM's has random connectivity between all units, with the variability most strong in the inter-layer projections. Aside from this 'quenched' noise, the dynamics shown in Figure \ref{sequence} are deterministic. In the presence of white noise applied to each unit's input currents LAMM's overall recall performance decreases (Fig. \ref{noise}). This is due to the increased variability in the currents kicking the behaviour out of weakly attracting recall trajectories and into the more strongly attracting ones, which are usually short cycles (e.g 1212.., 123123..) \cite[c.f ]{Romani2013}. These short cycles are likely formed by the strongest item-item transitions [_I think I can check this.._], often the \(+1\) transitions between successive items.



 * compare with behavioural data
* recall depends on list length (Fig \ref{listlength})
* recall depends on list orderings (Fig. \ref{projectivity})
* recall worsens with noise; worsens with recall phase plasticity (Fig. \ref{noise})



