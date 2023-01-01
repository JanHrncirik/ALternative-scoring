# # ALternative-scoring
/Alternative Scoring – Gliding, FOR NATIONAL, CONTINENTAL, AND WORLD GLIDING CHAMPIONSHIPS CLASS D (gliders) Including Class DM (motorgliders). 7 February 2022

## **Read Me - Alternative scoring with penalty seconds**
Final program debugged version 12/30/2022
The script "IGC_Annex_A_scoring_2023_with_penalty" enables the scoring of gliding competitions according to the calculation formula published in the document "Alternative Scoring - Gliding" dated February 7, 2022.
[https://www.fai.org/sites/default/files/altscoring.pdf](https://www.fai.org/sites/default/files/altscoring.pdf)
Without entering parameters in the window "Properties of the competition day" - line Pilots[i].Tag checks the flights in the usual way. In the Results, for the purpose of continuous calculation control, the display of Sp0, Spm and k parameters has been added.
Sp0 – Highest Provisional Score (SP) of the Day
Spm – Median Provisional Score (SP) of the Day, excluding competitors with SP = 0.
k – number of competitors whose scores were used to calculate Spm. The number of competitors whose score is not equal to 0.
## **PEV**
After entering the PEVWaitTime parameters, PEVStartWindow checks the correctness of the departure performed according to paragraph 7.4.2 b The PEV start stated in document Annex A to Section 3 – Gliding.
[https://www.fai.org/sites/default/files/sc3a_2022.pdf](https://www.fai.org/sites/default/files/sc3a_2022.pdf)
The number of PEV starts in the program is limited to 3. The program ignores further pressing of the PEV marker within 30 seconds. This time can be set in the constants of program.
PevStartTimeBuffer = 30;
If "AllUserWrng" in "DayTag" is set to 0, it will only display a start-message in the pilot warnings in case of a wrong start. When set to 1, it will display all and correct departures as well.
## **Interpolation of starting speed according to DAEC SWO 7.3.5**
Enter "MaxStSpd2=130" in DayTag to get interpolation and user alerts if average initial speed is greater than 130 km/h
## **Penalty second**s
The program can evaluate the start altitude, start groundspeed and height difference between start and arrival and the exceedance of these values will be rated with seconds added to the competitor's flight time. It will then reduce the speed of the competitor. Vo, T0 parameters for scoring are calculated only after these corrections.
This should allow the organizer to set the start altitude, for example, 300 m below the predicted altitude of the cloud bases and to set the preferred altitude on arrival. The aim is to increase safety before start and upon arrival.
The parameter settings are displayed in the results for review.
The output of the evaluation is in the pilot's warning window. I assume copying the output to the "Comments" window so that it can be seen in the results.
The following penalty values are set in the constants of program (values can be changed):
GPS ground speed - 5 seconds per 1 km/h (taken from GP).
Altitude AMSL - 2 seconds per 1 m (taken from GP).
[https://www.fai.org/sites/default/files/sgp-rules-v9.1_0.pdf](https://www.fai.org/sites/default/files/sgp-rules-v9.1_0.pdf)
Loss of height - 1 second per 1 m. (Taken from CPS. 6.3.6 [https://sk.gcup.eu/public/docs/rules/gcup_20150121_en.pdf](https://sk.gcup.eu/public/docs/rules/gcup_20150121_en.pdf))
### #### Example:
Entry into daily parameters
PEVWaitTime=5 PEVStartWindow=8 MaxStSpd=170 MaxStAlt=1900 MaxFinishIsBelowSt=1520
### Output warning
Start speed higher by 18.15 km/h, penalty seconds = 91; Start height exceeded by 260 m, penalty seconds = 520; Altitude loss between departure and arrival exceeded by 238 m penalty seconds = 238; Time added to the flight 00:14:09;
## **Other**
Other program options were preserved from the original script IGC_Annex_A_scoring_2021, of which this script is a modification. They are described in the initial header of the script.


# Read Me – Alternatívne bodovanie s trestnými sekundami
Konečný súbor, odladený variant 30.12.2022
Skript „IGC_Annex_A_scoring_2023_with_penalty“ umožňuje bodovanie plachtárskych súťaží podľa výpočtového vzorca publikovaného v dokumente športového poriadku „Alternative Scoring – Gliding“ zo dňa 7. februára 2022. 
[https://www.fai.org/sites/default/files/altscoring.pdf](https://www.fai.org/sites/default/files/sc3a_2022.pdf)
Bez zadania parametrov v okne „Vlastnosti súťažného dňa“ -riadok Pilots[i].Tag kontroluje lety bežným spôsobom. Vo výsledkoch pre účely priebežnej kontroly výpočtov pribudlo zobrazenie parametrov Sp0, Spm a k.
Sp0 – Najvyššie predbežné skóre (SP) dňa
Spm – Stredné predbežné skóre (SP) dňa, s výnimkou pretekárov s SP = 0. 
k – počet pretekárov, ktorých skóre bolo použité pre výpočet Spm. Počet pretekárov, ktorých skóre nie je rovné 0.
## PEV
Po zadaní parametrov PEVWaitTime, PEVStartWindow kontroluje správnosť odletu vykonávaného podľa odseku 7.4.2 b The PEV start, dokumentu Annex A to Section 3 – Gliding.
[https://www.fai.org/sites/default/files/sc3a_2022.pdf](https://www.fai.org/sites/default/files/sc3a_2022.pdf)
Počet odletov PEV je v programe obmedzený na 3. Program ignoruje ďalšie stlačenie markeru PEV v priebehu 30 sekúnd. Tento čas je možné nastaviť v konštantách programu. 
PevStartTimeBuffer = 30;
Ak je "AllUserWrng" v “DayTag“ nastavené na 0, zobrazí vo varovaniach pilota odlet-správu len v prípade nesprávneho odletu. Pri nastavení na 1 zobrazí všetky aj správne odlety.
### Interpolácia štartovacej rýchlosti voči zemi podľa DAEC SWO 7.3.5
Zadajte „MaxStSpd2=130“ do DayTag, aby ste získali interpoláciu a upozornenia používateľa, ak je priemerná počiatočná rýchlosť vyššia ako 130 km/h
## Trestné sekundy
Program môže vyhodnocovať výšku odletu, rýchlosť odletu voči zemi a rozdiel výšky medzi odletom a príletom a prekročenie týchto nastavených hodnôt oceniť sekundami, ktoré pridá k času letu pretekára. Následne zníži rýchlosť pretekára. Parametre Vo, T0 pre bodovanie sú počítané až po týchto korekciách.
Toto má umožniť organizátorovi nastaviť výšku odletu napríklad 300 m pod predpovedanú výšku základní a nastaviť preferovanú výšku na prílete. Cieľom je zvýšiť bezpečnosť pred odletom a na prílete.
Nastavenia parametrov sú pre kontrolu zobrazené vo výsledkoch. 
Výstup vyhodnotenia je do okna varovania pilota. Predpokladám kopírovanie výstupu do okna „Poznámka“, aby ho bolo vidieť vo výsledkoch.
V konštantách programu sú nastavené nasledovné hodnoty penalizácie (hodnoty je možné meniť):
Rýchlosť oproti zemi GPS – 5 sekúnd za 1 km/h (prevzaté z GP).
Výška AMSL – 2 sekundy za 1 m (prevzaté z GP).
[https://www.fai.org/sites/default/files/sgp-rules-v9.1_0.pdf](https://www.fai.org/sites/default/files/sgp-rules-v9.1_0.pdf)
Strata výšky – 1 sekúnd za 1 m. (Prevzaté z CPS. 6.3.6 [https://sk.gcup.eu/public/docs/rules/gcup_20150121_en.pdf](https://sk.gcup.eu/public/docs/rules/gcup_20150121_en.pdf))
### Príklad:
#### Zadanie do denných parametrov
PEVWaitTime=5 PEVStartWindow=8 MaxStSpd=170 MaxStAlt=1900 MaxFinishIsBelowSt=1520
#### Výstupné varovanie
Start speed higher by  18,15 km/h, penalty seconds =  91;  Start height exceeded by  260 m, penalty seconds =  520;  Altitude loss between departure and arrival exceeded by  238 m  penalty seconds =  238;  Time added to the flight 00:14:09; 
Iné
Ďalšie možnosti programu boli zachované z pôvodného skriptu IGC_Annex_A_scoring_2021, ktorého je tento skript modifikáciou. Sú opísané v úvodnej hlavičke skriptu.
