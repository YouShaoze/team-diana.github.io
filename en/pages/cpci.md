# Compact PCI

## cPCI-7432

![Cpci-7432](http://www.adlinktech.com/PD/photo/display/cPCI-7432+7433+7434/cPCI-7432+7433+7434_bimg_1.jpg)

### Pinouts

![pinout](/uploads/cpci7432pinout.png)
![pinout legend](/uploads/cpci7432pinout_legend.png)

Here follows some notes about the api. For further reference see the [PCI DASK manual](http://www.adlinktech.com/publications/manual/Software/PCIS-DASK-X/PSDASKFR.pdf)

```c++

// Read a single channel at port i [0-63]
// voltageRange is a value like AD_B_0_5_V (bipolar 5V)
AI_ReadChannel(adcCard, i, voltageRanges, &value))
// Convert the read raw value into a float result
AI_VoltScale(adcCard, range, *(int16_t*)(&value), &res);

// In general, you will want to use AI_VoltScale
```

*Note*: you have to specify if you want to sample unipolar or bipolar signal during the configuration:

```c++
AI_9116_Config(adcCard, MODE, trigMode, 0, 0, 0))
// MODE could be for instance: P9116_AI_UserCMMD|P9116_AI_UniPolar
```
then you will always have to specify only Unipolar or Bipolar range depending on this configuration


## cPCI-9116

![cPCI-9116](http://www.adlinktech.com/PD/photo/display/cPCI-9116/cPCI-9116_bimg_en_2.jpg)

### Pinouts

![pinout](/uploads/cpci9116pinout.png)
![pinout legend](/uploads/cpci9116pinout_legend.png)

### API

Here follows some notes about the api. For further reference see the [PCI DASK manual](http://www.adlinktech.com/publications/manual/Software/PCIS-DASK-X/PSDASKFR.pdf)

```c++

// Read a single channel at port i [0-63]
// voltageRange is a value like AD_B_0_5_V (bipolar 5V)
AI_ReadChannel(adcCard, i, voltageRanges, &value))
// Convert the read raw value into a float result
AI_VoltScale(adcCard, range, *(int16_t*)(&value), &res);

// In general, you will want to use AI_VoltScale
```

*Note*: you have to specify if you want to sample unipolar or bipolar signal during the configuration:

```c++
AI_9116_Config(adcCard, MODE, trigMode, 0, 0, 0))
// MODE could be for instance: P9116_AI_UserCMMD|P9116_AI_UniPolar
```
then you will always have to specify only Unipolar or Bipolar range depending on this configuration.

```c++

// Write a single bit at Line [0-7] of port Port 0 (cPCI9116 has only one port)
I16 DO_WriteLine (U16 CardNumber, U16 Port, U16 Line,
U16 State);

```

### Drivers

It may be possible that ADLink still does not publish linux 3.x drivers. In this case, email adlink and request the source code (better option anyway). Off course we already have the source so ask to other team members for a copy.

### See also
[io_adc](io_adc.md)


## cPCI-7841

![cPCI-7841](http://www.adlinktech.com/PD/photo/display/PCI-7841+cPCI-7841/PCI-7841+cPCI-7841_bimg_en_2.jpg)

![pinout](/uploads/cpci7841pinout.png)

See also:
 - [Elmo Solo Whistle](elmo_solo_whistle.md)
 - [CAN wiring](can-wiring.md)
 - [cPCI-7841 - Driver Issues](cpci-7841-driver.md)
 - [Learning - Network Protocols - CAN](http://0.0.0.0:8080/en/#!pages/network_protocols_learning.md#CAN)

### CANOpen

CANOpen comunication is implemented via a fork of ipa_canopen:

[team-diana/ipa_canopen](https://github.com/team-diana/ipa_canopen)

### Related specifications:

 -[DS305](http://www.canopensolutions.com/english/about_canopen/lss.shtml)
  The **Layer Setting Services (LSS)** allows to setup a CAN node.
 -[DS402](http://www.can-cia.org/index.php?id=530)
  The **CANopen device profile for drives and motion control** is the standard for motion control defined
  by the [CiA](http://www.can-cia.org/)

See [Elmo Solo Whistle](elmo_solo_whistle.md) for related implementations of these specifications.

### Configuration

```bash
sudo su
insmod p7841.ko # load the kernel module
sudo mknod /dev/PCI7841W0 c 250 0
sudo mknod /dev/PCI7841W1 c 250 1
sudo chmod a+rw /dev/PCI7841W0
sudo chmod a+rw /dev/PCI7841W1
./test7841 # run the example in order to be sure that the can work (remember to connect the wires between the two ports)
```

### Links

[Adlink - cPCI-7841](http://www.adlinktech.com/PD/web/PD_detail.php?pid=145)
