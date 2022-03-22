<hr>
<a href="https://github.com/RandomDebugError/flipperzero-firmware-1/releases">
  <img src="https://i.imgur.com/Nto2Rie.png" align="center" alt="42 Edition" title="42 Edition">
</a>

<hr>
<h3 align="center">
  A collection of IR files and walkthrough for the <a href="https://flipperzero.one">Flipper Zero</a> device.<br><br>
  <a href="#">
    <img src="https://img.shields.io/badge/Powered%20by-Dolphins-blue" alt="Powered by dolphins" height=24>
    <img src="https://img.shields.io/badge/Approved%20by-RandomDebugError-brightgreen" alt="Approved by RandomDebugError" height=26 title="Why Bother">
    <img src="https://img.shields.io/badge/Hack-The%20Planet-orange" alt="Hack the planet" height=26>
  </a>
</h3>
<hr>

<!-- Shout out to Lurat for html-->


# **For Flipper Zero Use**

## The Flipper Zero currently supports the tranmission of the following types of IR Protocols:
* NEC
* NECext (also possibly known as NECx2)
* NEC42
* NEC42ext 
* RC5 
* RC5X
* RC6 
* Samsung32 
* SIRC (also possibly known as Sony12)
* SIRC15
* SIRC20


## To manually create a Remote using the code:

1. Open a code editor (I prefer VS Code).
2. Locate a file in this repository that you would like to make a remote for.
3. Using the format shown in Sony.ir to create your .ir file (using any available commands that you would like to have from this repository).
    * Make sure that the naming convention is similar to already existing versions (exp. if you want Enter it needs to be Menu_enter. begin typing what you want and         you may be prompted for what the system wants. Alternatively look at existing .ir file for naming conventions).
4. Leave the "type" attribute (shown in Sony.ir line6) as parsed.
5. Choose the appropriate "protocol" (shown in Sony.ir line 6) for the file in the repository (shown in 1,-1.csv line 2 under protocol).
    * Use the exact naming convention shown above. If protocol is different from what you know, double check list above as some may have alternative names/ use trial-and-error/ critical thinking.
6. Set the first part of the "address" attribute (shown in Sony.ir line 7) to the same as the device (shown in 1,-1.csv line 2 under device).
    * Note this may need the subdevice code as the device code (exp. 01 02 00 00 if the subdevice is listed as 2) or might need the subdevice as the device (02 00 00         00 if the subdevice is 2).
7. Set the first part of the "command" attribute (shown in Sony.ir line 8) equal to the hex version of the "function" attribute from this repository (shown in 1,-1.csv    line 2 under function). Exp. VOLUME UP function of 1,-1.csv is 18 in decimal, this translates to 12 in Hexidecimal thus in Sony.ir it is shown in line 32 as 12 00      00 00.
   * If you need a quick Dec to Hex Converter: https://www.rapidtables.com/convert/number/decimal-to-hex.html
8. Repeat steps for all commands and save as IR file.
9. Add to Flipper and test for functionality.
10. If testing is successful, add file to https://github.com/Lucaslhm/Flipper-IRDB or submit to DJ(Lurat) on Flippers Github for addition to a repository.
11. Also If you have an IR file not included in this repository, ADD IT. This HUGE repository only exists due to people contributing to it!


## Sony.ir
![vs](https://i.imgur.com/nTnBC2g.png)

## 1,-1.csv
![csv](https://i.imgur.com/EJIGLBB.png)











# irdb

![ir](https://cloud.githubusercontent.com/assets/2480569/9023330/cc63e7fe-3897-11e5-94cb-8cb145971fd2.png)

One of the largest crowd-sourced, manufacturer-independent databases of infrared remote control codes on the web, and aspiring to become the most comprehensive and most accurate one. Think of it as the "Wikipedia of infrared remote control codes".

## Usage

This database contains infrared remote control codes in a very space-efficient way, using protocol, device, subdevice, function notation. Using this information, you can render signals to raw timings, Pronto Hex, or other formats using software like [IrScrutinizer](https://github.com/bengtmartensson/harctoolboxbundle) or [MakeHex](https://github.com/probonopd/MakeHex).

## Accessing

If you would like to access this database from your product (e.g., app) it is suggested that you do not bundle the database as a whole but access it dynamically at runtime. By doing so, your product will benefit from updates of the database automatically.

To access the database with any amount of traffic, it is recommended to use a content delivery network (CDN). For example, instead of accessing files from GitHub locally, you chould access them over a service like [jsdelivr.net](https://www.jsdelivr.com/) like this:

```
https://cdn.jsdelivr.net/gh/probonopd/irdb@master/codes/index
https://cdn.jsdelivr.net/gh/probonopd/irdb@master/codes/Samsung/TV/7,7.csv
```

## Contributing

1. Check whether the code you want to contribute is already in the database
2. If it is not, click the "edit" button to change/edit a file
3. Follow the naming conventions for files, `<manufacturer>/<devicetype>/<device>,<subdevice>.csv`
4. Make sure the file contains the codes in ascending order of the `function` column
5. Create a pull request and state the device you have used to create the file in the comment

## Examples

In this section, projects and products will be listed which include or access irdb.
* [irdb.tk](http://irdb.tk) website that allows you to search the database and render codes in various formats
* [IrScrutinizer](https://github.com/bengtmartensson/harctoolboxbundle) software that can import infrared remote signals from irdb, scrutinize them, and send them using various sending devices
* [DIYRemote](https://github.com/shannah/DIYRemote) Android app that allows you to browse the [irdb.tk](http://irdb.tk) website and test the IR codes live on Android devices that have an IR emitter.  Also allows you to create your own custom universal remote controls using HTML.

## License

You may include or access this database from your product (e.g., app) provided that you follow the terms of the [irdb License](https://github.com/probonopd/irdb/blob/master/LICENSE.md).


