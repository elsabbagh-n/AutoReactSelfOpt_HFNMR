# AutoReactSelfOpt_HFNMR

This repository includes MATLAB scripts allowing to autonomously control a Bruker high-field NMR spectroscopy, as well as NMR dataset of experiments carried out for the submission of the paper entitled

    Autonomous reaction self-optimization using in-line high-field NMR spectroscopy

whose authors are

    Nour El Sabbagh,(a) Margherita Bazzoni,(a) Yuliia Horbenko,(a) Aurélie Bernard,(a) Daniel Cortés-Borda,(a) Patrick Giraudeau,(a) François-Xavier Felpin,*(a) Jean-Nicolas Dumez*(a)

    (a)  Nantes Université, CNRS, CEISAM UMR 6230, F-44000 Nantes (France)
     *   E-mail : Francois-Xavier.Felpin@univ-nantes.fr ; Jean-Nicolas.Dumez@univ-nantes.fr


In this paper, we introduce the concept of autonomous self-optimizing flow reactors guided by in-line high-field NMR spectroscopy. We designed an autonomous experimental setup, combining an automated flow reactor with a high-field NMR spectrometer and a feedback optimization algorithm.

## Dataset
The folder

    _dataset
      
contains Bruker datasets of the experiments carried out in this work. It includes five types of experiments :

  (i)	1D 1H NMR spectra with a WET block for solvent suppression were acquired on samples of the prepared stock solutions to identify peaks of the reagents and catalyst (see Figure S2 in ESI);
  
  (ii)	Continuous 1D 1H NMR spectra with a WET block for solvent suppression  were acquired following the launch of two flow reaction runs to monitor the arrival of the mixture of interest in NMR detection zone;
  
  (iii)	1D 1H NMR spectra with a WET block for solvent suppression  were acquired to screen the reaction mixture of different flow reaction runs with different residence times;
  
  (iv)	1D 1H NMR spectra with a WET block for solvent suppression  were acquired to screen the reaction mixture of different flow reaction runs during the autonomous self-optimization to maximize the yield and throughput.

  (v) 1D 1H and 13C NMR spectra acquired on sample of the purified product in an NMR tube.

  (vi) 1D 1H NMR spectra with a WET block for solvent suppression were acquired at high and low-field on the same reaction sample in an NMR tube.

### (i) NMR profile of the prepared stock solutions:
The subfolder in _dataset with the same title contains: 

    Experiments	  #5	stock solution of the limiting reagent	(S1)
		          #7	stock solution of the excess reagent	(S2)
		          #9	stock solution of the catalyst		(S3)
  
    Description	  samples introduced into a 5 mm NMR tube


### (ii) Monitoring of the arrival of the mixture of interest to the detection zone:
The subfolder in _dataset with the same title contains: 

    File		  1- Plateau search major change
    
    Experiments	  #1 to #42
    
    Description	  on flow acquisition using the flow tube
		          flow rate of 0.450 mL/min
		          reaction run with 10.0 min residence time, 1.53 equiv of citral, 0.04 equiv of catalyst
		          reaction run launched at 09:13:46
		          previous reaction conditions: only ethanol in flow system


    File		  2- Plateau search minor change
    
    Experiments	  #114 to #146
    
    Description	  on flow acquisition using the flow tube
		          flow rate of 0.433 mL/min
		          reaction run with 10.4 min residence time, 1.59 equiv of citral, 0.05 equiv of catalyst
		          reaction run launched at 10:33:40
		          previous reaction conditions: 10 min residence time, 1.43 equiv of citral, 0.08 equiv of catalyst


### (iii) Screening reaction mixtures of different residence times:
The subfolder in _dataset with the same title contains: 

    Experiments	  #1,3,5,7,9,11
    
    Description	  on flow acquisition using the flow tube
		          reaction runs with 1.2 equiv of citral, 0.08 equiv of catalyst and with residence times of 3, 7.6, 13.2, 18.8, 24.4, 30 min, respectively
		          flow rate of 1.500,0.592,0.341,0.239,0.184,0.150 mL/min, respectively


    Experiments	  #2,4,6,8,10
    
    Description	  without flow acquisition using the flow tube
		          reaction runs with 1.2 equiv of citral, 0.08 equiv of catalyst and with residence times of 3, 7.6, 13.2, 18.8, 24.4 min, respectively


### (iv) Screening reaction mixtures during autonomous self-optimization:
The subfolder in _dataset with the same title contains: 

    File		  1- Yield optimization
    
    Experiments	  #1 to #30
    
    Description	  on flow (odd numbered experiments) and without flow (even numbered experiments) acquisition using the flow tube


    File		  2- Throughput optimization
    
    Experiments	  #1 to #30
    
    Description	  on flow (odd numbered experiments) and without flow (even numbered experiments) acquisition using the flow tube


### (v) 1H and 13C NMR profile of the purified product:
The subfolder in _dataset with the same title contains: 

    Experiments	  #1	1D 1H NMR spectrum
		          #2	1D 13C NMR spectrum

    Description	  sample introduced into a 5 mm NMR tube


### (vi) High vs low-field NMR screening of the reaction mixture:
The subfolder in _dataset with the same title contains: 

    Experiments	  #1	1D 1H NMR spectrum at high-filed (Bruker)
		          #2	1D 1H NMR spectrum at low-filed (Magritek)

    Description	  samples introduced into a 5 mm NMR tube


### (vii) HRMS analysis on the purified product:
The subfolder in _dataset with the same title contains: 

    File		  HRMS_results

    Description	  1.49 g were analyzed through HRMS
		          MeOH/H2O (95/5)


## Matlab scripts
The folder

    _HFC_interface
      
contains Matlab scripts allowing autonomous control of Bruker high-field NMR spectrometer.

In the subfolder

    _HFC_interface/matlab_scripts
    
we provide the Matlab scripts that allowed the automatic control of the high-field spectrometer, through WLAN, in our autonomous self-optimization platform.

Using our HFC interface to control the high-field NMR spectrometer, instruction text files have to be exchanged between the interface on MATLAB and IconNMR/TopSpin on the spectrometer's computer.

In the subfolder

    _HFC_interface/example_of_instruction_files
      
we hereby present three examples of this instruction text file:

    File		extset_1
    
    Description	When IconNMR scans extset_1, it creates an experiment under the user name "Nour", for the sample on holder "1" of the robot attached to the spectrometer, for which the lock and shim are applied on the deuterated solvent "EtOD". This will be experiment number "1" in the dataset folder "240520_yield_optimization" with title "on flow exp: res time 7.6 min - reag2: 1.2 equiv. - reag3: 0.08 equiv.". The parameter set saved under "PROTON_Nour" will be used for the acquisition, where the following parameters are changed: relaxation delay to 5 sec ("d1,5"), number of scans to 1 ("ns,1"), frequency of channel 1 to 5 ppm ("o1,5").
  
    Remarks		If the flow tube is attached instead, the holder number is not taken into account.
		        If the dataset folder is not yet created, IconNMR will do so when running the experiment.
		        If lock and shim prior experiment not asked for, the solvent is not taken into account.


    File		extset_2
    
    Description	When IconNMR scans extset_2, it starts the automation where all created and submitted experiments available are handed to TopSpin to be launched one after the other.
  
    Remarks		If automation is already running, IconNMR will ignore this instruction.
		        If no experiments were created, automation will still start, and any new submitted experiment will be directly lunched through TopSpin.


    File		extset_3

    Description	When IconNMR scans extset_3, it stops the automation where the current running experiment is interrupted and all remaining submitted experiments will be on hold.
  
    Remarks		If automation is already stopped, IconNMR will ignore this instruction.
		        If no experiments were created, automation will still stop, and any new submitted experiment will be set on hold.


