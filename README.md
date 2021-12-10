# Compressed Sensing by Yeji Bae and Manon Montyne #
####################################################

# Data compression

In data compression, a certain signal is represented more efficiently in terms of the sparse vector of coefficients in a generic transform basis e.g. Fourier or wavelet bases. Since most natural signals are compressible, they can be written in terms of a sparse vector s ∈ R^n and a transform basis Ψ ∈ R^(nxn): 

                                                                      x = Ψs
                                                                      
The number of non-zero elements in the vector s equals K. Therefore, we also describe s as being K-sparse.

Both images and audio signals are compressible in Fourier or wavelet bases. After taking the transform, most coefficient are close to zero and can thus be set equal to zero with a limited loss of quality. Afterwards, these few active coefficients can replace the original signal to be stored and transmitted. The original signal can then be recovered by taking the inverse transform.

# Compressed sensing

Compressed sensing on the other hand, turns the compression paradigm upside down: instead of compressing high-dimensional data by discarding most of the information, it is now possible to reconstruct a full signal from only a few measurements. The full signal can be recovered with high probability using convex algorithms. The mathematical formulation is as follows:

 - The measurements y ∈ R^p, with K < p << n are given by: y =  Cx   
 - C ∈ R^(pxn) is the measurement matrix  with a set of p linear measurements on the state of x
 - We now need to find the sparsest vector s, consistent with the measurements y
 - y = CΨs = Θs
 - This sytem of equations is and underdetermined problem and we thus have infinitely many solutions for s, however we want to find the sparsest s for which these equations hold --> ŝ = argmin ||s||₀ subject to y = CΨs
 - This optimization however is non-convex and a solution can only be found by brute-force search, therefore we will relax the optimization to a convex optimization: ŝ = argmin ||s||₁ subject to y = CΨs (here we take the l₁ norm or the Manhattan norm)

Conditions
- The matrix C must be incoherent with respect to Ψ
- The number of measurements p must be sufficiently larger on the order of: p = O(K*log(n/K)) = k₁*K*log(n/K) (k₁ depends on how incoherent C and Ψ are)
                                                                  
