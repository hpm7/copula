# Correlation in GBD coding challenge

Input: GBD outputs from CODEm (fatal), DisMod (non-fatal), or even just get_draws

Output: Same exact columns as inputs, but jointly correlated

Inpspiration: It's common knowledge that everything modelled in GBD does not specify any correlation structures, for e.g., we would expect a pretty high correlation between IHD and Diabetes, or for a given cause, we might expect to see correlation across adjacent age groups. Therefore, when we aggregate deaths across causes to a global level, we find the uncertainty intervals to be super small.

The purpose of this project is to be able to come up with a function which will take in marginal distributions and a (matrix of) correlation values, and output the same number of columns that went in, but the joint distribution of the marginals will be correlated. In terms of IHME application, aggregating a joint distribution will give wider uncertainty intervals (for e.g., if high draws are correlated with other high draws, and v.v. for low draws, you can expect the upper and lower intervals to be expansive).

How do we do that: Sklar's Theorem says that there always exists a function such that, for any two marginal distributions, the joint distribution can have a given correlation structure, such that the marginals in the joint are unchanged. 

A much smaller scaled version of this has been used and published by IHME last year, and therefore I think we have a great standing foot to work off of (see master branch).


## Challenges: 
-	large number of rows (scalibility and tractability computationally)
-   high dimensionality in categories (specifiying and being able to choose correlation across ages/sexes/causes)
-	keeping a dimension unchanged (induce correlation across ages and sexes, but keep the temporal correlation untouched)
-- (wrapper function around the already existing one, which will collapse non-sorts into a single dim, and to-sorts into another)

-	coming up with a prior correlation matrix
-- (an option: using older GBD results to be passed)

-	the impossible combinations (if we are dealing with four marginal distributions, and we have two pairs with perfect correlation, then it's impossible to ... )


## Progress:

1)	Getting comfy with the function by using example draws right now. 
2)	Creating a prepping data function to take get_draws and prep for the copulating function.

3)	Unit tests. 
4)	Stacking of dimensions. Most challenging. (7 modified business days) 
5)	Supplying correlation matrix. Build in a default AR(1) matrix if correlation not supplied. 
6)	Porting to different language. 


## Timeline:














