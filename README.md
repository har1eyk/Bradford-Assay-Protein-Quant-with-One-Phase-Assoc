# Bradford-Assay-Protein-Quant-with-One-Phase-Assoc
The Bradford method is a popular biochemical technique for determining the concentration of protein. 

A common kit like the Thermo Fisher Scientific (cat. no. 23236, http://bit.ly/2DaYy7C) uses the Coomassie Brilliant Blue G-250 dye molecule. In the presence the protein, a conformational state in the dye is stabilized resulting in a color change. The color change is proportional to the amount of protein and can be detected by a spectrophotometer reading absorbance at 595 nm. 

## [PlyCB](http://www.rcsb.org/structure/4F87) reacts with Dye
![Image of Bradford](https://raw.githubusercontent.com/har1eyk/Bradford-Assay-Protein-Quant-with-One-Phase-Assoc/master/images/Bradford.assay.figure.jpg)


Precise protein concentration is an important characteristic for downstream experiments like ELISAs, protein-protein interactions and isothermal titration calorimetry.

Although the dye and protein react in a proportional manner and can be characterized with a linear model, high concentrations of protein will stabilize most dye molecules causing saturation. Saturation causes a bowing in the data, and can be seen with the bovin serum albumin (BSA) standards recommended by the kit. The curve is better approximated by a non-linear regression method.

# Non-linear Regression One Phase Association
I was taught to use a linear model as it's simple and accurate for lower protein concentrations. However, a linear model results in greater error when calculating unknown high protein concentrations. 

Other non-linear regression models like second-order polynomials can approximate the data but also can fail at the lower or higher ends. Growth curves or enzymatic models fit the data to an "S" curve. 

I recently discovered that a [one phase association](https://www.graphpad.com/guides/prism/7/curve-fitting/index.htm?reg_exponential_association.htm) model best approximates all standard-BSA protein concentrations recommended by the provider.
Y=(Y0 - Plateau)*exp(-K*X) + Plateau
![Wolfram Alpha One Phase Assocation](https://raw.githubusercontent.com/har1eyk/Bradford-Assay-Protein-Quant-with-One-Phase-Assoc/master/images/one.phase.association.equation.wa.jpg)

WA link: https://www.wolframalpha.com/input/?i=Solve%5BY%3D(Y0+-+P)*e%5E(-K*X)+%2B+P,+X%5D

# One Phase Association Best Describes the Data
The data was plotted and model with linear (lilac), polynomial (blue) and one-phase association models (black).

+-------+---------+
| mg/ml |   abs   |
+-------+---------+
|  2000 | 1.07685 |
|  1500 |  0.9741 |
|  1000 |  0.8432 |
|   750 | 0.74875 |
|   500 |  0.4937 |
|   250 |  0.2928 |
|   125 |  0.1696 |
|    25 | 0.02865 |
+-------+---------+

The data and Excel equations can be found in the Excel workbook in this repository.

![dataModeling](https://raw.githubusercontent.com/har1eyk/Bradford-Assay-Protein-Quant-with-One-Phase-Assoc/master/images/modeling.bradford.data.jpg)



