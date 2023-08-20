# channelBWs Parser
online calculator: https://dustinchen26.github.io/bw

## Usage
```
● Usage: Parse Qcom UeCapabilityInformation supported channelBWs
> ref: 3GPP spec ETSI TS 138 306
> (Rule1) => For FR1, the bits in channelBWs-DL starting from the leftmost bit indicate 5, 10, 15, 20, 25, 30, 40, 50, 60 and 80MHz. ex: channelBWs-DL fr1 :{scs-30kHz '00010111 11'B},
> (Rule2) => For FR1, the leading/leftmost bit in channelBWs-DL-v1590 indicates 70MHz, and all the remaining bits in channelBWs-DL-v1590 shall be set to 0. ex:{scs-30kHz '10000000 00000000'B},
> (Rule3) => To determine whether the UE supports a channel bandwidth of 90 MHz, the network may ignore this capability for and validate instead the channelBW-90mhz and the supportedBandwidthCombinationSet. ex: channelBW-90mhz supported,
> (Rule4) => whether the UE supports a channel bandwidth of 100 MHz, ex: supportedBandwidthDL fr1 : mhz100
> ex: Compal UE mifi n78 SCS=30 support BW 20, 30, 40, 50, 60, 70, 80, 90, 100
```

## Example input
● Paste the UeCapabilityInformation below(it only process Rule1, the Rule 2,3,4 should check by yourself)
```
      {
        bandNR 78,
        channelBWs-DL fr1 : 
          {
            scs-15kHz '00000000 00'B,
            scs-30kHz '00010111 11'B,
            scs-60kHz '00000000 00'B
          },
```

## Output
```
bandNR: 78, scs-15kHz '00000000 00' Supported Bandwidths (scs-15kHz):  MHz
bandNR: 78, scs-30kHz '00010111 11' Supported Bandwidths (scs-30kHz): 20, 30, 40, 50, 60, 80 MHz
bandNR: 78, scs-60kHz '00000000 00' Supported Bandwidths (scs-60kHz):  MHz
```