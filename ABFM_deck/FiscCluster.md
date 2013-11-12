---
title       : Spatial Implications of Tax and Expenditure Limitations
subtitle    : TABOR is Just One Piece...
author      : Marvin Ward Jr.
job         : Fiscal Analyst, DC Office of Revenue Analysis
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : [mathjax]            # {mathjax, quiz, bootstrap}
ext_widgets : {rCharts: ["libraries/highcharts", "libraries/nvd3", "libraries/morris"]}
mode        : selfcontained # {standalone, draft}

---

## Plan of Attack

+ Why study the local impact of TELs?
+ Does TABOR capture TEL structure in Colorado?
+ How can we explore spatial clustering?
+ How can we explore the impact of TEL intensity?
+ What have we learned?
+ What are the next steps?

--- .class #id 

## General Mechanism

1. TELs impose artificial barriers in the fiscal matching process
2. Revenue growth that lags expenditure need decreases the achievable investment in human and physical capital
3. Lower capital investment diminishes the attractiveness of a jurisdiction for businesses and, in turn, residents

To the extent that recessions facilitate 'ratcheting', the dynamic impact of recessionary years in non-trivial.  

Can TELs impact broad trends in fiscal and economic capacity?

---


## TEL Literature Landscape

Most of the empirical work attempts to study TELs across states, and as such, focuses on statewide definitions of TELs. Obviously this covers up local variation, but perhaps more interestingly, this choice in geographic scope encourages certain types of questions. 

+ What is the impact of TELs on revenue volatility ([St. Clair 2012](http://papers.ssrn.com/sol3/papers.cfm?abstract_id=2151690))? 
+ Do TELs constrain property taxes ([Dye & McGuire 1997](http://www.sciencedirect.com/science/article/pii/S0047272797000479))? 
+ Do TELs constrain growth in employment and wages ([Poterba & Rueben 1995](http://www.jstor.org/discover/10.2307/2117953?uid=3739256&uid=2&uid=4&sid=21102688756161))?
+ Does the impact of TELs on property revenue change during recessions (Mullins & Mikesell 2013)?

Evaluating the impact of TELs with a local lens begs the question, *are some jurisdictions affected differently than others*? While St. Clair did utilize local government data, the purpose was to show a general effect.  [Mullins (2004)](http://onlinelibrary.wiley.com/doi/10.1111/j.0275-1100.2004.00350.x/abstract?deniedAccessCustomisedMessage=&userIsAuthenticated=false), by contrast, is an important example of evaluating the *differential* impact of TELs as a function of socioeconomic starting conditions.

This study seeks to extend this approach by incorporating spatial and temporal dependency.

---

![DC Mean AGI](/home/choct155/dissertation/Presentations/ABFM_deck/iit2011_by_census_block_map_scaled.png)

---

## TABOR *And Company*

While the Taxpayer's Bill of Rights (TABOR) gets the lion's share of attention in Colorado, it is but one component of a set of four overlapping policies.  In order of enactment:

1. **General Statewide Limit on Property Tax Revenue (SLPTR):**  Local property tax revenues may not increase by more than 5.5% in a given year (the limit was 7% before 1988)
2. **Gallagher Amendment (GA):** Assessment rates for residential property are set statewide, calculated to keep historical ratios of residential and non-residential property tax revenue consistent (with some minor space for modification)
3. **Taxpayer Bill of Rights (TABOR):** Limits annual growth in revenues to inflation plus a measure of growth (new construction for local governments and enrollment for school districts)
4. **Amendment 23 (A23):** Mandates minimum increases in school funding and removes a portion of revenue from the TABOR base

Yes, the interactions create modeling difficulties, but they also happen to provide *temporal variation* in the restrictiveness of the TEL structure.

---

## And De-Brucing is ...?

Local governments reserve the right to waive the requirements of both TABOR and the SLPTR.  Over the 1993-2011 period, 48 counties chose to exempt themselves from one or both restrictions.  This has provided *cross-sectional variation*.

![TEL Intensity](/home/choct155/dissertation/Presentations/ABFM_deck/TEL_intensity_2009.png)

---

## Local Indicators of Spatial Autocorrelation

Spatial clustering is an indication of shared economic bases and fiscal linkages (both active cooperation and spillovers).  Revenue per capita can serve as a fiscal capacity indicator used to evaluate the extent of said fiscal linkages.

### Local Moran's $I_i$

<div>
$$I_i=\frac{\sum_j z_i w_{i,j} z_j}{\sum_i z_i^2}=\frac{\sum_j (y_i-\bar y)w_{i,j}(y_j-\bar y)}{\sum_i(y_i-\bar y)^2}$$
</div>

### Getis & Ord's $G_i$

<div>
$$G_i(d)=\frac{\sum_j w_{i,j} (d) y_j - W_i \bar y(i)}{s(i)\{[(n-1) S_{1i} - W_i^2]/(n-2)\}^{(1/2)}},j \neq i$$
</div>

--- 

![Moran](/home/choct155/dissertation/Presentations/ABFM_deck/moranIPlot.png)

---

![Getis and Ord](/home/choct155/dissertation/Presentations/ABFM_deck/goGPlot.png)

---

## Clustering Dynamic Evolves Over Time

![Cluster Kernel G_i](/home/choct155/dissertation/Presentations/ABFM_deck/cluster_var_by_w_kern_g.png)

+ Variation is substantially higher in $G_i$, which indicates relative consistency in clustering activity, with larger variation in the magnitude of clustering values. This could mean simultaneous revenue capacity transitions occur in multiple counties within given neighborhoods.

---

## Additional Clustering Observations

+ Variation is generally more substantial in the higher values for both statistics. For Moran's $I_i$, this indicates varying intensity of spatial association amongst similar values. For $G_i$ this indicates low revenue capacity counties are more tightly coupled than high revenue capacity counties.



+ Central tendency generally leans right of zero for $I_i$, while leaning left of zero for $G_i$ This suggests a tendency towards the existence of spatial clustering, but this clustering occurs more often among low revenue capacity jurisdictions.

---

## Econometric Exploration

__Ordinary Least Squares__  - OLS will serve as a non-spatial pooled estimate

   $$y=X\beta+\epsilon$$

**Spatial Error Model** - Error term in this model seeks to mitigate spatial dependency across counties

   $$y=\gamma Wy + X\beta-\gamma WX\beta + \epsilon$$

**Spatial Lag Model** - Model explicitly incorporates the weighted average of neighborhood values

   <div>
   $$y = \rho Wy + X\beta + \epsilon$$
   </div>

**Fixed Effect Spatial Lag Model** - Model both incorporates the weighted average of neighborhood values and the value of the observation in the preceding time period

   $$y=\lambda (I_T \otimes W_N)y + (\iota_T \otimes I_N)\mu + X\beta + \epsilon$$ 
   

---

## What Are We Modeling?

At this stage, the skeletal specification being assessed is, in general, the following:

$y = f($TEL Intensity, Relative Per Capita Industrial Output, Gross State Product$)$

For most of the models, $y$ is Per Capita Revenue, but the clustering values calculated from the 10 combinations of 5 weight matrices and the two LISAs ($G_i$ and $I_i$) are modeled when weight matrices do not enter the right side of the equation.

TEL intensity is (somewhat clumsily) modeled as an ordinal score, with each TEL policy adding to said score.

In general, the variation explained was fairly limited, but TEL intensity rejected the null consistently at a high level of confidence.

---

## Highlights

1. When estimating the impact of TEL intensity on clustering values, clear effects ($p$ < .05) were only seen with $G_i$ dependents.  The effects were in the ballpark of a -0.1$\sigma$.

2. The negative impact of of TEL intensity on per capita revenue grew by approximately 25% when spatial impacts were introduced, and fell by an order of magnitude when temporal effects were subsequently added (~ -.3$\sigma$ to -.03$\sigma$).

3. The impact of TEL intensity (in repeated cross-sections) grew more negative with time.  This effect was consistent both across weight matrix choice in both SEM and SLM, as well as the number of lags modeled in SLM.

---

![TEL Impact on Per Capita Revenue](/home/choct155/dissertation/Presentations/ABFM_deck/TEL_pcrev_impact_scaled.png)

---

## UPDATE:

Initial TEL Intensity Score masks cross-sectional variation stemming from economic differences between counties.  The new intensity measure has two components:

1. TEL constraint is modeled as the lesser between the TABOR and Statewide Property Tax Revenue limits

2. Gallagher Amendment is modeled as the ratio between two broad classes of property: residential/non-residential

The latter enters the model directly, but the former is used to model capacity that remains unaccessible due to the constraints.  Both *flow* and *stock* measures were generated.

$y = f($TEL Intensity, Property Classification Ratio, Demand for Housing, Demand for Residence$)$

---


## Next Steps

1. Compare "revenue" capacity dynamic to economic capacity dynamic to parse out source endowments from the output of public choice.

2. A limitation of the approaches used here is the modeling of all counties en masse.  In reality, the socioeconomic starting conditions of each differ, and it is possible to parse out regimes for parameter estimation.  Regime in this case would be defined by revenue capacity quintile.

3. Taking this one step further, it seems reasonable to suspect that TELs play a role in the probability of transitioning from one regime to next.  Spatially aware Markov chain methods are available to test this hypothesis.

4. While it is plausible that revenue composition converges with TEL intensity, the multivariate nature of revenue portfolios complicates direct comparison.  Principal component analysis or the author's preliminary thoughts on $f($Kendall's $\tau$, Euclidean Distance$)$ may serve to reduce dimesionality enough for systematic comparison.

Pick me apart (but you have to tell me about it): [https://github.com/choct155/TEL/blob/master/ipynb/ABFM_TEL_Script.html](https://github.com/choct155/TEL/blob/master/ipynb/ABFM_TEL_Script.html) 





---

# APPENDIX

---

## TEL Intensity vs. State Unemployment Rate


<div id='chart3' class='rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawchart3()
    });
    function drawchart3(){  
      var opts = {
 "dom": "chart3",
"width":    800,
"height":    400,
"x": "st_unempr",
"y": "est",
"group": "model",
"type": "scatterChart",
"color": "pval",
"id": "chart3" 
},
        data = [
 {
 "X": 3,
"est": 900.92,
"pval": 0.94357,
"var": "intensity_stock",
"pr2":   0.17,
"model": "slm_econ",
"year": 1995,
"st_unempr":      4 
},
{
 "X": 5,
"est": -325.48,
"pval": 0.72417,
"var": "intensity_stock",
"pr2": 0.67497,
"model": "slm_rev",
"year": 1995,
"st_unempr":      4 
},
{
 "X": 3,
"est": -16311,
"pval": 0.12457,
"var": "intensity_stock",
"pr2": 0.23243,
"model": "slm_econ",
"year": 1996,
"st_unempr":    4.2 
},
{
 "X": 5,
"est": -856.87,
"pval": 0.33235,
"var": "intensity_stock",
"pr2": 0.64409,
"model": "slm_rev",
"year": 1996,
"st_unempr":    4.2 
},
{
 "X": 3,
"est": -3375.4,
"pval": 0.57063,
"var": "intensity_stock",
"pr2": 0.19542,
"model": "slm_econ",
"year": 1997,
"st_unempr":    3.4 
},
{
 "X": 5,
"est": -906.56,
"pval": 0.033803,
"var": "intensity_stock",
"pr2": 0.66289,
"model": "slm_rev",
"year": 1997,
"st_unempr":    3.4 
},
{
 "X": 3,
"est": -2141.6,
"pval": 0.69665,
"var": "intensity_stock",
"pr2": 0.19425,
"model": "slm_econ",
"year": 1998,
"st_unempr":    3.5 
},
{
 "X": 5,
"est": -924.72,
"pval": 0.015042,
"var": "intensity_stock",
"pr2": 0.6909,
"model": "slm_rev",
"year": 1998,
"st_unempr":    3.5 
},
{
 "X": 3,
"est": 1918.6,
"pval": 0.68892,
"var": "intensity_stock",
"pr2": 0.18782,
"model": "slm_econ",
"year": 1999,
"st_unempr":      3 
},
{
 "X": 5,
"est": -839.43,
"pval": 0.021854,
"var": "intensity_stock",
"pr2": 0.65417,
"model": "slm_rev",
"year": 1999,
"st_unempr":      3 
},
{
 "X": 3,
"est":   3528,
"pval": 0.48363,
"var": "intensity_stock",
"pr2": 0.19215,
"model": "slm_econ",
"year": 2000,
"st_unempr":    2.7 
},
{
 "X": 5,
"est": -954.81,
"pval": 0.0083257,
"var": "intensity_stock",
"pr2": 0.63644,
"model": "slm_rev",
"year": 2000,
"st_unempr":    2.7 
},
{
 "X": 3,
"est": 5246.6,
"pval": 0.15229,
"var": "intensity_stock",
"pr2": 0.23345,
"model": "slm_econ",
"year": 2001,
"st_unempr":    3.8 
},
{
 "X": 5,
"est": -620.94,
"pval": 0.01903,
"var": "intensity_stock",
"pr2": 0.63242,
"model": "slm_rev",
"year": 2001,
"st_unempr":    3.8 
},
{
 "X": 3,
"est": 5049.6,
"pval": 0.14154,
"var": "intensity_stock",
"pr2": 0.27315,
"model": "slm_econ",
"year": 2002,
"st_unempr":    5.7 
},
{
 "X": 5,
"est": -511.86,
"pval": 0.13363,
"var": "intensity_stock",
"pr2": 0.57683,
"model": "slm_rev",
"year": 2002,
"st_unempr":    5.7 
},
{
 "X": 3,
"est": 4017.3,
"pval": 0.24561,
"var": "intensity_stock",
"pr2": 0.21134,
"model": "slm_econ",
"year": 2003,
"st_unempr":    6.1 
},
{
 "X": 5,
"est": -264.33,
"pval": 0.3622,
"var": "intensity_stock",
"pr2": 0.63121,
"model": "slm_rev",
"year": 2003,
"st_unempr":    6.1 
},
{
 "X": 3,
"est": 2888.5,
"pval": 0.31798,
"var": "intensity_stock",
"pr2": 0.22323,
"model": "slm_econ",
"year": 2004,
"st_unempr":    5.6 
},
{
 "X": 5,
"est": -354.92,
"pval": 0.10533,
"var": "intensity_stock",
"pr2": 0.6598,
"model": "slm_rev",
"year": 2004,
"st_unempr":    5.6 
},
{
 "X": 3,
"est": 2798.3,
"pval": 0.29328,
"var": "intensity_stock",
"pr2": 0.22917,
"model": "slm_econ",
"year": 2005,
"st_unempr":    5.1 
},
{
 "X": 5,
"est": -491.56,
"pval": 0.01807,
"var": "intensity_stock",
"pr2": 0.64581,
"model": "slm_rev",
"year": 2005,
"st_unempr":    5.1 
},
{
 "X": 3,
"est": 2238.9,
"pval": 0.36639,
"var": "intensity_stock",
"pr2": 0.24621,
"model": "slm_econ",
"year": 2006,
"st_unempr":    4.3 
},
{
 "X": 5,
"est": -294.69,
"pval": 0.14563,
"var": "intensity_stock",
"pr2": 0.63609,
"model": "slm_rev",
"year": 2006,
"st_unempr":    4.3 
},
{
 "X": 3,
"est": 2331.9,
"pval":  0.292,
"var": "intensity_stock",
"pr2": 0.29031,
"model": "slm_econ",
"year": 2007,
"st_unempr":    3.8 
},
{
 "X": 5,
"est": -320.79,
"pval": 0.13602,
"var": "intensity_stock",
"pr2": 0.60932,
"model": "slm_rev",
"year": 2007,
"st_unempr":    3.8 
},
{
 "X": 3,
"est": 1547.1,
"pval": 0.47965,
"var": "intensity_stock",
"pr2": 0.33333,
"model": "slm_econ",
"year": 2008,
"st_unempr":    4.8 
},
{
 "X": 5,
"est": -478.56,
"pval": 0.034579,
"var": "intensity_stock",
"pr2": 0.57629,
"model": "slm_rev",
"year": 2008,
"st_unempr":    4.8 
},
{
 "X": 3,
"est": 1085.6,
"pval": 0.49092,
"var": "intensity_stock",
"pr2": 0.39135,
"model": "slm_econ",
"year": 2009,
"st_unempr":    8.1 
},
{
 "X": 5,
"est": -260.93,
"pval": 0.20278,
"var": "intensity_stock",
"pr2": 0.56223,
"model": "slm_rev",
"year": 2009,
"st_unempr":    8.1 
} 
]
  
      var data = d3.nest()
        .key(function(d){
          return opts.group === undefined ? 'main' : d[opts.group]
        })
        .entries(data)
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .x(function(d) { return d[opts.x] })
          .y(function(d) { return d[opts.y] })
          .width(opts.width)
          .height(opts.height)
         
        
          
        

        
        
        
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>


---

## TEL Intensity Impact by Year


<div id = 'Chart4' class = 'rChart nvd3'></div>
<script type='text/javascript'>
 $(document).ready(function(){
      drawChart4()
    });
    function drawChart4(){  
      var opts = {
 "dom": "Chart4",
"width":    800,
"height":    400,
"x": "year",
"y": "est",
"group": "model",
"type": "multiBarChart",
"title": "TEL Intensity Estimates Over Time",
"id": "Chart4" 
},
        data = [
 {
 "X": 3,
"est": 900.9224267005,
"pval": 0.9435668199872,
"var": "intensity_stock",
"pr2": 0.1699975703233,
"model": "slm_econ",
"year": 1995,
"st_unempr":              4 
},
{
 "X": 5,
"est": -325.4793235475,
"pval": 0.7241664038076,
"var": "intensity_stock",
"pr2": 0.6749691162565,
"model": "slm_rev",
"year": 1995,
"st_unempr":              4 
},
{
 "X": 3,
"est": -16310.52720344,
"pval": 0.1245665493891,
"var": "intensity_stock",
"pr2": 0.2324343000739,
"model": "slm_econ",
"year": 1996,
"st_unempr":            4.2 
},
{
 "X": 5,
"est": -856.8721132819,
"pval": 0.3323542475805,
"var": "intensity_stock",
"pr2": 0.6440884156585,
"model": "slm_rev",
"year": 1996,
"st_unempr":            4.2 
},
{
 "X": 3,
"est": -3375.376503958,
"pval": 0.5706255325022,
"var": "intensity_stock",
"pr2": 0.1954207582433,
"model": "slm_econ",
"year": 1997,
"st_unempr":            3.4 
},
{
 "X": 5,
"est": -906.5639540528,
"pval": 0.03380346928501,
"var": "intensity_stock",
"pr2": 0.6628938534316,
"model": "slm_rev",
"year": 1997,
"st_unempr":            3.4 
},
{
 "X": 3,
"est": -2141.55755095,
"pval": 0.6966523062812,
"var": "intensity_stock",
"pr2": 0.1942473057187,
"model": "slm_econ",
"year": 1998,
"st_unempr":            3.5 
},
{
 "X": 5,
"est": -924.7229725652,
"pval": 0.01504197653569,
"var": "intensity_stock",
"pr2": 0.690898666411,
"model": "slm_rev",
"year": 1998,
"st_unempr":            3.5 
},
{
 "X": 3,
"est": 1918.626165524,
"pval": 0.6889239774547,
"var": "intensity_stock",
"pr2": 0.1878225689603,
"model": "slm_econ",
"year": 1999,
"st_unempr":              3 
},
{
 "X": 5,
"est": -839.4286852002,
"pval": 0.0218543674185,
"var": "intensity_stock",
"pr2": 0.6541685771778,
"model": "slm_rev",
"year": 1999,
"st_unempr":              3 
},
{
 "X": 3,
"est": 3527.993507737,
"pval": 0.4836276516606,
"var": "intensity_stock",
"pr2": 0.1921461255538,
"model": "slm_econ",
"year": 2000,
"st_unempr":            2.7 
},
{
 "X": 5,
"est": -954.8141019661,
"pval": 0.008325711285281,
"var": "intensity_stock",
"pr2": 0.6364411313175,
"model": "slm_rev",
"year": 2000,
"st_unempr":            2.7 
},
{
 "X": 3,
"est": 5246.644817456,
"pval": 0.1522870498335,
"var": "intensity_stock",
"pr2": 0.2334451122447,
"model": "slm_econ",
"year": 2001,
"st_unempr":            3.8 
},
{
 "X": 5,
"est": -620.9372099317,
"pval": 0.01903018343737,
"var": "intensity_stock",
"pr2": 0.6324180311784,
"model": "slm_rev",
"year": 2001,
"st_unempr":            3.8 
},
{
 "X": 3,
"est": 5049.600815087,
"pval": 0.1415358089654,
"var": "intensity_stock",
"pr2": 0.2731454967024,
"model": "slm_econ",
"year": 2002,
"st_unempr":            5.7 
},
{
 "X": 5,
"est": -511.8640631656,
"pval": 0.1336297531493,
"var": "intensity_stock",
"pr2": 0.5768327783229,
"model": "slm_rev",
"year": 2002,
"st_unempr":            5.7 
},
{
 "X": 3,
"est": 4017.259505092,
"pval": 0.2456098781218,
"var": "intensity_stock",
"pr2": 0.2113402815172,
"model": "slm_econ",
"year": 2003,
"st_unempr":            6.1 
},
{
 "X": 5,
"est": -264.3327986584,
"pval": 0.3622042596347,
"var": "intensity_stock",
"pr2": 0.631206324094,
"model": "slm_rev",
"year": 2003,
"st_unempr":            6.1 
},
{
 "X": 3,
"est": 2888.504166501,
"pval": 0.3179797721316,
"var": "intensity_stock",
"pr2": 0.2232339799281,
"model": "slm_econ",
"year": 2004,
"st_unempr":            5.6 
},
{
 "X": 5,
"est": -354.921267122,
"pval": 0.1053261778269,
"var": "intensity_stock",
"pr2": 0.6597991069278,
"model": "slm_rev",
"year": 2004,
"st_unempr":            5.6 
},
{
 "X": 3,
"est": 2798.267141041,
"pval": 0.2932796502226,
"var": "intensity_stock",
"pr2": 0.2291679561841,
"model": "slm_econ",
"year": 2005,
"st_unempr":            5.1 
},
{
 "X": 5,
"est": -491.5594094288,
"pval": 0.0180704928484,
"var": "intensity_stock",
"pr2": 0.6458144794074,
"model": "slm_rev",
"year": 2005,
"st_unempr":            5.1 
},
{
 "X": 3,
"est": 2238.947189299,
"pval": 0.3663904838086,
"var": "intensity_stock",
"pr2": 0.2462121922066,
"model": "slm_econ",
"year": 2006,
"st_unempr":            4.3 
},
{
 "X": 5,
"est": -294.6946291591,
"pval": 0.1456341388135,
"var": "intensity_stock",
"pr2": 0.6360878542497,
"model": "slm_rev",
"year": 2006,
"st_unempr":            4.3 
},
{
 "X": 3,
"est": 2331.862427098,
"pval": 0.2920015155372,
"var": "intensity_stock",
"pr2": 0.2903080824307,
"model": "slm_econ",
"year": 2007,
"st_unempr":            3.8 
},
{
 "X": 5,
"est": -320.788377513,
"pval": 0.1360185949161,
"var": "intensity_stock",
"pr2": 0.609323116984,
"model": "slm_rev",
"year": 2007,
"st_unempr":            3.8 
},
{
 "X": 3,
"est": 1547.112855529,
"pval": 0.4796537780313,
"var": "intensity_stock",
"pr2": 0.3333339530103,
"model": "slm_econ",
"year": 2008,
"st_unempr":            4.8 
},
{
 "X": 5,
"est": -478.5627639267,
"pval": 0.03457945489043,
"var": "intensity_stock",
"pr2": 0.5762887315287,
"model": "slm_rev",
"year": 2008,
"st_unempr":            4.8 
},
{
 "X": 3,
"est": 1085.613147137,
"pval": 0.4909187152187,
"var": "intensity_stock",
"pr2": 0.3913514008093,
"model": "slm_econ",
"year": 2009,
"st_unempr":            8.1 
},
{
 "X": 5,
"est": -260.9264165802,
"pval": 0.2027842231436,
"var": "intensity_stock",
"pr2": 0.5622299198557,
"model": "slm_rev",
"year": 2009,
"st_unempr":            8.1 
} 
]
  
      if(!(opts.type==="pieChart" || opts.type==="sparklinePlus")) {
        var data = d3.nest()
          .key(function(d){
            //return opts.group === undefined ? 'main' : d[opts.group]
            //instead of main would think a better default is opts.x
            return opts.group === undefined ? opts.y : d[opts.group];
          })
          .entries(data);
      }
      
      if (opts.disabled != undefined){
        data.map(function(d, i){
          d.disabled = opts.disabled[i]
        })
      }
      
      nv.addGraph(function() {
        var chart = nv.models[opts.type]()
          .x(function(d) { return d[opts.x] })
          .y(function(d) { return d[opts.y] })
          .width(opts.width)
          .height(opts.height)
         
        
          
        

        
        
        
      
       d3.select("#" + opts.id)
        .append('svg')
        .datum(data)
        .transition().duration(500)
        .call(chart);

       nv.utils.windowResize(chart.update);
       return chart;
      });
    };
</script>


