The present file includes examples of the instruction text file exchanged during experiments
carried out for the submission of the paper entitled:

<< Autonomous reaction self-optimization using in-line high-field NMR spectroscopy >>

whose authors are:

Nour El Sabbagh,(a) Margherita Bazzoni,(a) Yuliia Horbenko,(a) Aurélie Bernard,(a)
Daniel Cortés-Borda,(a) Patrick Giraudeau,(a) François-Xavier Felpin,*(a) Jean-Nicolas Dumez*(a)

(a)	Nantes Université, CNRS, CEISAM UMR 6230, F-44000 Nantes (France)
 *	E-mail : Francois-Xavier.Felpin@univ-nantes.fr ; Jean-Nicolas.Dumez@univ-nantes.fr


In this paper, we introduce the concept of autonomous self-optimizing flow reactors guided by 
in-line high-field NMR spectroscopy. We designed an autonomous experimental setup, combining 
an automated flow reactor with a high-field NMR spectrometer and a feedback optimization algorithm.

For this, instruction text files have to be exchanged between the interface controlling the 
spectrometer on MATLAB and IconNMR/TopSpin on the spectrometer's computer.

We hereby present three examples of this instruction text file:

File		extset_1
Description	When IconNMR scans extset_1, it creates an experiment under the user name "Nour", for 
		the sample on holder "1" of the robot attached to the spectrometer, for which the lock
		and shim are applied on the deuterated solvent "EtOD". This will be experiment number 
		"1" in the dataset folder "240520_yield_optimization" with title "on flow exp: res time
		7.6 min - reag2: 1.2 equiv. - reag3: 0.08 equiv.". The parameter set saved under
		"PROTON_Nour" will be used for the acquisition, where the following parameters are 
		changed: relaxation delay to 5 sec ("d1,5"), number of scans to 1 ("ns,1"), frequency
		of channel 1 to 5 ppm ("o1,5").
Remarks		If the flow tube is attached instead, the holder number is not taken into account.
		If the dataset folder is not yet created, IconNMR will do so when running the experiment.
		If lock and shim prior experiment not asked for, the solvent is not taken into account.

File		extset_2
Description	When IconNMR scans extset_2, it starts the automation where all created and submitted 
		experiments available are handed to TopSpin to be launched one after the other.
Remarks		If automation is already running, IconNMR will ignore this instruction.
		If no experiments were created, automation will still start, and any new submitted 
		experiment will be directly lunched through TopSpin.

File		extset_3
Description	When IconNMR scans extset_3, it stops the automation where the current running experiment 
		is interrupted and all remaining submitted experiments will be on hold.
Remarks		If automation is already stopped, IconNMR will ignore this instruction.
		If no experiments were created, automation will still stop, and any new submitted 
		experiment will be set on hold.

