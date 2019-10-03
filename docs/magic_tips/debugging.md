
NOTE: Unless otherwise stated, these commands are designed to be used from the MAGIC front end.

## Recovering from a crash

```
IF{O(%);O(%,1)},IF{O($);O($,%.TREE)},$FE("")
```

## Using %Z.ddc

```
%Z.ddc(A,B,C)
```

Arguments:

* A - String to display when debugger is run
* B - Specific device to invoke debugger code for
* C - Specific user mnemonic to invoke debugger code for

Example:

```
%Z.ddc("Check symbol table","WHUGHES.1","MEDITECH")
```

[Page that explains most of the features in %Z.ddc](https://staff.meditech.com/en/d/clientservices5xprogtraining/pages/mgdebuggers.htm)


## Modify a symbol in a MAGIC DDC

Find the correct symbol table with the "??" command. Concatenate the symbol table letter with the variable name and enclose in quotes and square braces. Preface expressions with a semicolon to execute them in a DDC.

Example: Modifying the `DvN` symbol on the C table from a DDC:

```
;1^["CDvN"]
```


## Get crash information from the front end

```
O(/S,$MAC[$MAC]_"S"),/R^OS,C(/U),IF{["AD"] O(/S,$FPH(["AD"])),/#"0,"^PGM,C(/U)},["AA"]:0X:0S:80T^LINE
NN("Program:":11L,PGM)N("Line:":11L,LINE)N("Error loc:":11L,["AB"])N("OS Version:",OS)N^#
```

Use this information in the `%WS.ERR("")` program in directory ME6:XXX.WSERR

More info about crash information and the WS.ERR utility can be found [here](https://docs.google.com/document/d/1taSN4YithwUzTs-zihCgysagtKwKtDee_Yrj7ohW-1E).


## Get all ASCII values of a string

```
$CHX("<STRING>")
```
