# Class06: R Function
Yasmeen (PID:A18116120)

- [Background](#background)
- [A second function](#a-second-function)
  - [A new cool function](#a-new-cool-function)

## Background

Functions are at the heart of uisng R. Everything we do involves calling
and using functions (from data input, analysis to results output).

All functions in R have at least 3 things:

1.  A **name** the thing we use to call the function.
2.  One or more input **arguments** that are comma separated
3.  The **body**, lines of code between curly brackets {} that does the
    work of the function.

\##A first fuction

Let’s write a silly wee function to add some numbers:

``` r
add <- function(x) {
  x+1
}
```

Let’s try it out

``` r
add(100)
```

    [1] 101

Will this work

``` r
add( c(100,200,300))
```

    [1] 101 201 301

Modify to be more useful and add more than just 1

``` r
add <- function(x, y=1) {
  x + y
}
```

``` r
add(100, 10)
```

    [1] 110

Will this work?

``` r
add(100)
```

    [1] 101

``` r
plot(1:10, col="blue", typ="b")
```

![](class06_files/figure-commonmark/unnamed-chunk-7-1.png)

``` r
log(10, base=10)
```

    [1] 1

> **N.B** Input arguments can be either **required** or **optional**.
> The later have a fall-back default that is specified in the function
> code with an equals sign.

``` r
#add(100,200,300)
```

## A second function

All functions in R look like this

``` r
name <- function(arg) {
  body()
}
```

The `sample` function in R..

``` r
sample(1:10, size= 4)
```

    [1] 1 3 8 2

> Q. Write the code to genrate a random 12 nucleotide long DNA
> sequences?

``` r
bases <- c("A", "C", "G", "T")
sample(bases, size=12, replace= TRUE)
```

     [1] "G" "C" "T" "A" "A" "G" "G" "G" "A" "A" "G" "A"

> Q. Write a first version function called `generate_dna()` that
> generates a user specified length random `n` DNA sequences?

``` r
name <- function(arg) {
  body()
}
```

``` r
generate_dna <- function(n=6) {
  bases <- c("A", "C", "G", "T")
  sample(bases, size =n, replace = TRUE)
}
```

``` r
generate_dna(100)
```

      [1] "A" "A" "G" "C" "C" "A" "T" "T" "T" "C" "T" "C" "T" "A" "G" "T" "T" "T"
     [19] "G" "C" "G" "T" "C" "G" "C" "A" "T" "C" "C" "C" "C" "T" "C" "T" "G" "A"
     [37] "T" "C" "T" "C" "T" "T" "G" "G" "A" "C" "G" "T" "T" "C" "T" "G" "T" "T"
     [55] "T" "C" "A" "G" "C" "A" "C" "A" "T" "T" "G" "T" "T" "T" "C" "G" "G" "G"
     [73] "G" "G" "G" "T" "G" "A" "A" "T" "T" "G" "T" "T" "G" "T" "G" "T" "G" "G"
     [91] "G" "A" "G" "T" "G" "A" "C" "T" "A" "C"

> Q. Modify you rfunction to return a FASTA like sequence so rather than
> \[1\] “G” “C” “A” “A” “T” we want “GCAAT”

``` r
generate_dna <- function(n=6) {
  ans <- sample( c("A", "C", "G", "T"), size =n, replace= TRUE)
  ans <- paste(ans, collapse = "")
  return(ans)
  x <- "poopoopants"
  x
}
```

``` r
generate_dna(10)
```

    [1] "AGCAAGAAGG"

``` r
#Example pattern (not using your bases)
x <- c("H", "E", "L", "L", "O")

paste(x, collapse= "****")
```

    [1] "H****E****L****L****O"

``` r
# returns "HELLO"
```

``` r
x <- 100
x <- 10 
x <- 300
x
```

    [1] 300

> Q. Give the user an option to return FASTA format output sequnce or
> standard multi-element vector format

``` r
generate_dna <- function(n=6, fasta=TRUE) {
  ans <- sample( c("A","C", "G", "T"), size =n, replace = TRUE)
  
  if(fasta) {
    ans <- paste(ans, collapse = "")
    cat("Hello...")
  } else {
    cat("... is it me you are looking for...")
  }
  
  return(ans)
}
```

``` r
generate_dna(10)
```

    Hello...

    [1] "TCTCCACTTA"

``` r
generate_dna(10, fasta=F)
```

    ... is it me you are looking for...

     [1] "T" "T" "T" "C" "T" "A" "A" "G" "A" "A"

### A new cool function

> Q. Write a function called `generate_protein()` that generates a user
> specified length protein sequence in FASTA format?

``` r
genrate_protein <- function() {
  
  aa <- c(
    "A", "R", "N", "D", "C", "Q", "E", "G", "H", "I", "L", "K", "M", "F", "P", "S","T", "W", "Y", "V")
  
}
```

``` r
genrate_protein <- function(n, fasta=TRUE) {
  
  aa <- c(
    "A", "R", "N", "D", "C", "Q", "E", "G", "H", "I", "L", "K", "M", "F", "P", "S","T", "W", "Y", "V")
  ans <- sample(aa, size=n, replace= T)
  ans <-paste(ans, collapse = "")
  return(ans)
}
```

> Q. Use your new `generate_protein()` function to generate all sequnces
> between length 6 and 12 amino-acids in length and check of any of
> these are unique in nature (i.e. found in the NR database at NCBI)?

``` r
genrate_protein(6)
```

    [1] "VDTPCW"

``` r
genrate_protein(7)
```

    [1] "FYRKTFE"

``` r
genrate_protein(8)
```

    [1] "ICMFWDTK"

``` r
genrate_protein(9)
```

    [1] "MYYEPPNPA"

``` r
genrate_protein(10)
```

    [1] "AVYRTEELML"

``` r
genrate_protein(11)
```

    [1] "EWYIFSLFPSR"

``` r
genrate_protein(12)
```

    [1] "DWIDDDIEHTKT"

or we could do a `for()` loop:

``` r
for(i in 6:12) {
  cat(">", i, sep="", "\n")
  cat( genrate_protein(i), "\n" )
}
```

    >6
    ANMGYK 
    >7
    KCMTLLN 
    >8
    RVRFGSTW 
    >9
    VFEYNGCEL 
    >10
    WMCDDVNLQV 
    >11
    ARQHMNSIRWN 
    >12
    ELPNRPPQQGII 
