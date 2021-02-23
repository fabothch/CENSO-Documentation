# Thresholds

CENSO is a threshold based sorting algorithm. The thresholds have been determined for typical drug-like organic molecules up to 100 atoms. For cases with high flexibility or very different conformer ordering between SQM/FF and DFT it can be necessary to increase the thresholds. If your target quantity is an averaged ensemble free energy, be sure not to use small energy windows in part0 and part1, as this can falsely reduce the ensemble size.

In the following the employed thresholds are listed and their use is explained:

#### Part0 - Cheap Prescreening:

part0\_threshold = g\_thr\(0\)  

* cml:        -part0\_threshold 
* censorc: part0\_threshold

part0\_threshold g\_thr\(0\) is an energy window /threshold in kcal/mol within which all conformers are considered. The CENSO internal default for g\_thr\(0\) = 4.0 kcal/mol. The sorting threshold is designed to remove conformers very high lying in electronic energy \(E\).

#### Part1 - Prescreening:

In part1 two sorting steps are applied. One based on g\_thr\(1\) with improved energy and solvation description and one on G\_thr\(1\) where thermostatistical contributions have been calculated additionally.

part1\_threshold = g\_thr\(1\) and G\_thr\(1\) 

* cml:        -part1\_threshold 
* censorc: part1\_threshold

part1\_threshold g\_thr\(1\) is an energy window /threshold in kcal/mol within which all conformers are considered. The CENSO internal default for g\_thr\(1\) = 3.5 kcal/mol. The sorting threshold g\_thr\(1\) is designed to remove high lying conformers based on improved electronic energy \(E\) and solvation contributions \(dG\_solv\). G\_thr\(1\) sorting is based on full free energy including thermostatistical contributions \(G\_mRRHO\). Both, g\_thr\(1\) and G\_thr\(1\) use the same base threshold e.g. 3.5 kcal/mol and G\_thr\(1\) can be automatically increased as a function of the standard deviation of G\_mRRHO in the structure ensemble, indicating high structural diversity and possibly larger errors \(fuzzy sorting\).

#### Part2 - Optimization:

In part2 two sorting thresholds are applied. One which is applied during geometry optimization and one Boltzmann sum threshold.

threshold applied during optimization G\_thr\(opt,2\):  

* cml:       -opt\_limit
* censorc: opt\_limit

Spearman-threshold for testing for parallel PES: 

* cml:       -spearmanthr
* censorc: spearmanthr

Boltzmann sum threshold G\_thr\(2\): 

* cml:        -thrpart2 
* censorc: part2\_threshold

The internal default for G\_thr\(opt,2\) is set to 2.5 kcal/mol. During the geometry optimization the initial threshold G\_thr\(opt,2\) is increased by 60 % \(or at least 1.5 kcal/mol\). If the PES can be assumed parallel \(tested by a Spearman rank coefficient\) the threshold is decresed until it reaches the initial value. All conformers with \(free\) energies above the G\_thr\(opt,2\) threshold are discarded and all conformers below G\_thr\(opt,2\) will by fully DFT optimized. The last threshold employed in part2  is a Boltzmann sum threshold G\_thr\(2\) and all populated conformers of the ensemble, up to the Boltzmann population \(in %\) are considered further.

#### Part3 - Refinement:

In part3 a Boltzmann sum threshold is employed.

Boltzmann sum threshold G\_thr\(3\): 

* cml:         -thrpart3
* censorc: part3\_threshold

Based on high level free energies Boltzmann weights are calculated and all conformers up to the Boltzmann sum threshold \(in %\) are considered further.

#### Part4 - NMR properties:

In part4 only Boltzmann sum thresholds of part2 G\_thr\(2\) or part3 G\_thr\(3\) are applied. It is possible to calculate part4 using Boltzmann weights from part1, but since there is no Boltzmann sum threshold in part1, in this case, the threshold G\_thr\(2\) is used. The NMR properties are calculated on populated conformers up to the Boltzmann threshold in %.

#### Part5 - Optical rotatory dispersion:

In part4 only Boltzmann sum thresholds of part2 G\_thr\(2\) or part3 G\_thr\(3\) are applied. It is possible to calculate part5 using Boltzmann weights from part1, but since there is no Boltzmann sum threshold in part1, in this case, the threshold G\_thr\(2\) is used. The OR property is calculated on populated conformers up to the Boltzmann threshold in %. For optical rotation it is necessary to include almost the entire ensemble e.g. 99 %

