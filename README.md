# BMW X5 (G05) Coding with E-SYS

## 1. Hide "Emergency call system malfunction"

```
    DKOMBI4 (Instrument Cluster)
        300A CC_Konfiguration
            CC_MELDUNG_0296 -> nicht_aktiv
            CC_MELDUNG_0297 -> nicht_aktiv
            CC_MELDUNG_0298 -> nicht_aktiv
            CC_MELDUNG_0299 -> nicht_aktiv
            CC_MELDUNG_0300 -> nicht_aktiv
        3004 ERM_Konfiguration
            ST_ECAL_ALIVE -> nicht_aktiv
            ST_ECAL_TIMEOUT -> nicht_aktiv
```

## 2. Disable trunk opening from keyfob unless the doors are unlocked

```
    BDC_BODY3 (Body Domain Controller) 
        VAM_DISABLE_OPEN_LID_AT_NOT_UNLOCKED > aktiv
```


## 3. Soft trunk open/close

```
    HKFM2 (Tailgate Function Module)
        3011 APPL_PLG_SPEED_PROFILE
            ProfileOpenStartNode1PwmPlg (0x00 0xC8) -> 0x00 0xA0
            ProfileOpenStartNode2PwmPlg (0x02 0x62) -> 0x00 0xA0
            ProfileCloseStopNode1PwmPlg (0x02 0x62) -> 0x00 0xA0
            ProfileCloseStopNode2PwmPlg (0x02 0x62) -> 0x00 0xA0

    HEX VALUES IN ASC ORDER
    000A 00A0 00BE 00C8 00FA 017C 0212 0226
```

## Check the current version of psdzdata the car has

If your car is absolutely new you should have 3.57.2 on your car and your psdzdata will be too old.

You can connect E-Sys with your car, regardless of the i-level of E-Sys and the i-level from the car. Click on VCM and there on the folder Master. Now you can read out the current i-level from your car and you should know which psdzdata you will need.

Export Mode > VCM > Master (tab) > I-Steaps (section) > Read --> Integration steps

- There's no regional specification for the psdzdata.
- When you read out an ECU from your car, E-Sys is looking in your psdzdata folder for the corresponding file for the ECU. If your psdzdata is too old you will not be able to read the CAFD from an ECU, that's all.

## Links

- [https://bimmercode.app/cars/g05/](https://bimmercode.app/cars/g05/)
