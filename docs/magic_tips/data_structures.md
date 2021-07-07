# Printing Data Structures

## Output RAF data to a local file

**NOTE: These commands will only work in directories with NPR available.**

Save to file - $G Styling with RAF name and head node:
```
^<<:RAF[segments]>>^RAF,RAF%0~(",":32)^BASE,RAF#0~(" ":49_("$%&*?\/:!"))^PFX
""^X^LN,K(/RPT),IF{[RAF] (PFX_"["_BASE_"] = ")^/RPT[LN+1^LN,"1"],I([RAF]~("^":32))N^/RPT[LN,"2"]}
DO{>([RAF,X],Y)^X (PFX_"["_BASE_","_X~(",":32)_"] = ")^/RPT[LN+1^LN,"1"],I(Y~("^":32))N^/RPT[LN,"2"]}
D(30)_"DS"^#,#T[0]^/PATH,%Z.copy.raf.to.pc.flat(^/RPT,/PATH,"","N"),D(30)_"sh_"_{/PATH}^#
```

Save structure to temp file and open it:
```
^<<:RAF[segments]>>^RAF,RAF%0~(",":32)^BASE,RAF#0~(" ":49_("$%&*?\/:!"))^PFX
""^X^LN,K(/RPT),IF{[RAF] (PFX_"["_BASE_"] = ")^/RPT[LN+1^LN,"1"],I([RAF]~("^":32))N^/RPT[LN,"2"]}
DO{>([RAF,X],Y)^X (PFX_"["_BASE_","_X~(",":32)_"] = ")^/RPT[LN+1^LN,"1"],I(Y~("^":32))N^/RPT[LN,"2"]}
D(30)_"DpD"_(D(1,6))^#,#T[0]'#"4\"_"Local\Temp\"_S(0)_".txt"^/PATH
%Z.copy.raf.to.pc.flat(^/RPT,/PATH,"","N"),D(30)_"sh_"_{/PATH}^#
```

* Replace `<<:RAF[segments]>>` with the structure you're printing (do not replace the `^`)


## Print packed data to front end

```
<PACKED DATA>^X
0^CT,IF{E(X#0)'=L(X|0) N("Not packed data.")^#;DO{X IF{U(X)^Y N("Piece",CT:2L,"-",Y:0X)^#},CT+1^CT}}
```

* Broke out into two lines in case the packed data location is a long string

Example:

```
:GXA["2"]^X
0^CT,IF{E(X#0)'=L(X|0) N("Not packed data.")^#;DO{X IF{U(X)^Y N("Piece",CT:2L,"-",Y:0X)^#},CT+1^CT}}
```


## Safely print subscripts to screen

When printing delimited subscript values to screen, append `:0X` to the variable. This will replace the unprintable characters with spaces.

Example:
```
""^CT^X,DO{>*AA[X]^X,N(X:0X)^#,CT+1^CT<50}
```

You can also use translation (`~`). `X~(",":32)` will convert unprintable characters to commas. You can use any character in place of the comma (such as "^").
