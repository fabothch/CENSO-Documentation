# Censorc keyword definitions

#### $GENERAL SETTINGS:

| keyword: | definition: |
| :--- | :--- |
| nconf | how many conformers should be considered. Either a number or the flag 'all'. |
| charge | molecular charge of the molecule under investigation. |
| unpaired | number of unpaired electrons in the molecule under investigation. |
| solvent | Solvent if the molecule is in solution phase, else `gas`. |
| ​prog\_rrho | QM-code used for the calculation of thermostatistical contributions. This is only feasible with xtb, since normally a large number of hessian calculations have to be performed. |
| temperature | Temperature \(in Kelvin\) used for the Boltzmann evaluations. |
| trange | temperature range which is used to calculate free energies at different temperatures \(considered in G\_mRRHO and dG\_solv\[only COSMO-RS\]\). The temperature range will only be evaluated if multitemp is set to `on`. |
| multitemp | Evaluate free energies at different temperatures defined in trange. |
| evaluate\_rrho | Option to consider /not consider thermostatistical contributions. |
| consider\_sym | Option to consider symmetry in the thermostatistical contribution \(only xtb\) |
| bhess | Calculate single point hessians \(SPH\) on the geometry, instead of "ohess" \(optimization + hessian calculation\). |
| imagthr | threshold for inverting imaginary frequencies for thermostatistical contributions \(in cm-1\). Internal defaults are applied if set to 'automatic'. |
| sthr | rotor cut-off \(cm-1\) used for the thermostatical contributions. Internal defaults are applied if set to 'automatic'. |
| scale | scaling factor for frequencies in vibrational partition function. Internal defaults are applied if set to 'automatic'. |
| rmsdbias | gESC related, using rmsdpot.xyz to be consistent to CREST |
| sm\_rrho | solvent model applied in the GFNn-xTB thermostatistical contribution calculation. |
| check | Terminate the CENSO run if too many calculations crash. |
| prog | QM code used for part0, part1 and part2, this can be TURBOMOLE or ORCA. |
| func | functional used in part1 \(prescreening\) and part2 \(optimization\) |
| basis | basis set used in combination with func in part1 \(prescreening\) and part2 \(optimization\). If basis is set to 'automatic' the basis set is chosen internally. |
| maxthreads | Used for parallel calculation. Maxthreads determines the number of independent calculations running in parallel. E.g. resulting in 4 independent single-point /optimization calculations. |
| omp | Used for parallel calculation. Omp determines the number of cores each independent calculation can use. Eg. maxthreads = 4 and omp = 5 resulting in 4 independent calculations and each independent calculation uses 5 cores. |
| cosmorsparam | Flag for choosing COSMO-RS parameterizations. If set to 'automatic' the input from the COSMO-RS input line is chosen. |

#### $PART0 - CHEAP-PRESCREENING - SETTINGS:

| keyword: | definition: |
| :--- | :--- |
| part0 | Option to turn the "cheap prescreening part" on or off.  |
| func0 | Functional used in part0. |
| basis0 | Basis set used in combination with func0. If basis0 is set to 'automatic' the basis set is chosen internally. |
| part0\_gfnv | GFN version employed in the thermostatistical contribution in part0.  |
| part0\_threshold | Threshold/Energy-window \(kcal/mol\) within which all conformers are considered. |

#### $PART1 - PRESCREENING - SETTINGS:

| keyword: | definition: |
| :--- | :--- |
| part1 | Option to turn the "prescreening part" on or off. |
| smgsolv1 | Additive solvation contribution employed in part1.  |
| part1\_gfnv | GFN version employed in the thermostatistical contribution in part1.  |
| part1\_threshold | Threshold/Energy-window \(kcal/mol\) within which all conformers are considered further. |

#### $PART2 - OPTIMIZATION - SETTINGS:

<table>
  <thead>
    <tr>
      <th style="text-align:left">keywords:</th>
      <th style="text-align:left">definition:</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">part2</td>
      <td style="text-align:left">Option to turn the &quot;optimization part&quot; on or off.</td>
    </tr>
    <tr>
      <td style="text-align:left">opt_limit</td>
      <td style="text-align:left">Threshold/Energy-window (kcal/mol) within which all conformers are fully
        optimized.</td>
    </tr>
    <tr>
      <td style="text-align:left">sm2</td>
      <td style="text-align:left">Implicit solvation model used in the optimization. (for the imiplicit
        effect on the geometry)</td>
    </tr>
    <tr>
      <td style="text-align:left">smgsolv2</td>
      <td style="text-align:left">Additive solvation model used for calculation of &#x3B4;G_solv in part2.
        (used to calculate contribution to free energy)</td>
    </tr>
    <tr>
      <td style="text-align:left">part2_gfnv</td>
      <td style="text-align:left">GFN version employed in the thermostatistical (G_mRRHO) contribution in
        part2.</td>
    </tr>
    <tr>
      <td style="text-align:left">ancopt</td>
      <td style="text-align:left">Using ANCoptimizer implemented in xTB for geometry optimization.</td>
    </tr>
    <tr>
      <td style="text-align:left">hlow</td>
      <td style="text-align:left">Lowest force constant in ANC generation, used with ancopt.</td>
    </tr>
    <tr>
      <td style="text-align:left">opt_spearman</td>
      <td style="text-align:left">Using the new &quot;ensemble-optimizer&quot;.</td>
    </tr>
    <tr>
      <td style="text-align:left">part2_threshold</td>
      <td style="text-align:left">
        <p>Boltzmann threshold in % within which all conformers are considered further.</p>
        <p>E.g. 90 --&gt; all conformers up to a sum of 90 % are considered.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">optlevel2</td>
      <td style="text-align:left">Optimization threshold in the geometry optimization. If set to &quot;automatic&quot;,
        internal defaults will be used.</td>
    </tr>
    <tr>
      <td style="text-align:left">optcycles</td>
      <td style="text-align:left">Number of optimization iterations performed within one cycle in the ensemble
        optimizer.</td>
    </tr>
    <tr>
      <td style="text-align:left">spearmanthr</td>
      <td style="text-align:left">Spearman rank correlation coeff. used to determine if PES during geometry
        optimization can be assumed parallel.</td>
    </tr>
    <tr>
      <td style="text-align:left">radsize</td>
      <td style="text-align:left">Setting of the radial grid size for func used in part2.</td>
    </tr>
    <tr>
      <td style="text-align:left">crestcheck</td>
      <td style="text-align:left">Automatically sort out conformers which might have become identical or
        rotamers during DFT geometry optimization. Check is performed using CREST
        (this is threshold based, so use with care).</td>
    </tr>
  </tbody>
</table>

#### $PART3 - REFINEMENT - SETTINGS:

<table>
  <thead>
    <tr>
      <th style="text-align:left">keywords:</th>
      <th style="text-align:left">definitions:</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">part3</td>
      <td style="text-align:left">Option to turn the &quot;refinement part&quot; on or off.</td>
    </tr>
    <tr>
      <td style="text-align:left">prog3</td>
      <td style="text-align:left">QM code used for part3 this can be TURBOMOLE or ORCA.</td>
    </tr>
    <tr>
      <td style="text-align:left">func3</td>
      <td style="text-align:left">functional used in part3 (refinement)</td>
    </tr>
    <tr>
      <td style="text-align:left">basis3</td>
      <td style="text-align:left">
        <p>basis set employed in combination with func3.</p>
        <p>If basis3 is set to &apos;automatic&apos; the basis set is chosen internally.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left">smgsolv3</td>
      <td style="text-align:left">Additive solvation model used for calculation of &#x3B4;G_solv in part3.</td>
    </tr>
    <tr>
      <td style="text-align:left">part3_gfnv</td>
      <td style="text-align:left">GFN version employed in the thermostatistical contribution in part3.</td>
    </tr>
    <tr>
      <td style="text-align:left">part3_threshold</td>
      <td style="text-align:left">
        <p>Boltzmann threshold in % within which all conformers are considered further.</p>
        <p>E.g. 90 --&gt; all conformers up to a sum of 90 % are considered.</p>
      </td>
    </tr>
  </tbody>
</table>

#### $PART4 SETTINGS:

| keywords: | definitions: |
| :--- | :--- |
| part4 | Option to turn the "NMR property part" on or off. |
| couplings | Perform coupling constant calculations \[options are on or off\]. |
| progJ | QM code \(TM, ORCA\) used for coupling constant calculations. |
| funcJ | Density functional employed for the coupling constant calculation. |
| basisJ | basis set employed with the DFA \(funcJ\) for coupling constant calculations. |
| sm4J | implicit solvent model employed in the coupling constant calculation. |
| shieldings | Perform shielding constant calculations \[options are on or off\]. |
| progS | QM code \(TM, ORCA\) used for shielding constant calculations. |
| funcS | Density functional employed for the shielding constant calculation. |
| basisS | basis set employed with the DFA \(funcS\) for shielding constant calculations. |
| sm4S | implicit solvent model employed in the shielding constant calculation. |
| reference\_1H | Reference molecule to convert 1H shielding constants to shifts e.g. TMS. |
| reference\_13C | Reference molecule to convert 13C shielding constants to shifts e.g. TMS. |
| reference\_19F | Reference molecule to convert 19F shielding constants to shifts e.g. CFCl3. |
| reference\_29Si | Reference molecule to convert 29Si shielding constants to shifts e.g. TMS. |
| reference\_31P | Reference molecule to convert 31P shielding constants to shifts e.g. TMP. |
| 1H\_active | Calculate 1H NMR properties \[options are on or off\]. |
| 13C\_active | Calculate 13C NMR properties \[options are on or off\]. |
| 19F\_active | Calculate 19F NMR properties \[options are on or off\]. |
| 29Si\_active | Calculate 29Si NMR properties \[options are on or off\]. |
| 31P\_active | Calculate 31P NMR properties \[options are on or off\]. |
| resonance\_frequency | Resonance frequency of the experimental spectrometer \(in Hz\). |

#### $OPTICAL ROTATION PROPERTY SETTINGS:

| keywords: | definitions: |
| :--- | :--- |
| optical\_rotation | Option to turn the "OR property part" on or off. |
| funcOR | Functional employed to calculate the optical rotatory \(OR\) dispersion. |
| funcOR\_SCF | Functional to generate converged MOs. |
| basisOR | Basis set employed for the OR calculation. |
| frequency\_optical\_rot | List of frequencies in nm to evaluate OR at e.g. \[589.0\]. |

