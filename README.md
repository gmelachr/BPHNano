# nanoAOD producer customized for BPH analysis 

The focus is on B -> mumu X analyses.
Based on the code of RK 2018 (BParkingNano)

## Getting started

```shell
cmsrel CMSSW_15_1_X
cd CMSSW_15_1_X/src
cmsenv
git cms-init
```
Architecture should be el8 or el9

## Add the BPHNano package and build everything

```shell
git clone -b CMSSW_15_1_X git@github.com:gmelachr/BPHNano.git ./PhysicsTools
git cms-addpkg PhysicsTools/NanoAOD 
scram b -j 8 
```
or https equivalent

## To run on a test file

```shell
cd PhysicsTools/BPHNano/test/
cmsenv 
cmsRun run_bphNano_cfg.py
```

## cmsDriver command
```shell
cmsDriver.py --conditions 140X_dataRun3_Prompt_v4 --datatier NANOAOD --era Run3,run3_nanoAOD_pre142X --eventcontent NANOAOD --filein root://cms-xrd-global.cern.ch//store/data/Run2024C/ParkingDoubleMuonLowMass0/MINIAOD/PromptReco-v1/000/379/415/00000/b40397b5-61c6-4887-8f4e-025e8ca925ee.root --fileout file:/tmp/gmelachr/BPH_test_data.root --nThreads 4 -n -1 --no_exec --python_filename BPH_test.py --scenario pp --step NANO --customise=PhysicsTools/BPHNano/nanoBPH_cff.nanoAOD_customizeMuonBPH --customise=PhysicsTools/BPHNano/nanoBPH_cff.nanoAOD_customizeDiMuonBPH --customise=PhysicsTools/BPHNano/nanoBPH_cff.nanoAOD_customizeTrackBPH --customise=PhysicsTools/BPHNano/nanoBPH_cff.nanoAOD_customizeBToKshortLL --customise=PhysicsTools/BPHNano/nanoBPH_cff.nanoAOD_customizeLambdabToLambdaLL  --customise=PhysicsTools/BPHNano/nanoBPH_cff.nanoAOD_customizeBToKLL --customise=PhysicsTools/BPHNano/nanoBPH_cff.nanoAOD_customizeBToTrkTrkLL
#era modifier run3_nanoAOD_pre142X required in order to run in CMSSW_15_X miniAODs produced with CMSSW_14 or previous releases 
```




