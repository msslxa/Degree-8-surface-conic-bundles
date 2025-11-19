**Conic Bundles Maple Worksheets**

Overview

This repository contains four Maple worksheets (.mw) that construct and analyze conic bundles over P^1 for four multidegree types. Each worksheet:

Builds the six coefficient polynomials sigma_{i,j}(t) on the affine chart t = x0/x1 with the prescribed degrees.

(When required) Imposes linear relations among coefficients to cut out loci used in the constructions.

Diagonalizes the ternary quadratic form in variables (y0, y1, y2) using an explicit change of variables. Internally, the code permutes variables so that alpha0 = sigma_{2,2}; this matches the diagonalization routine implemented in the helper procedure DiagonalForm.

Converts the diagonalized form A(t) z0^2 + B(t) z1^2 + C(t) z2^2 to a Brauer-model conic
a(t) x^2 + b(t) y^2 - z^2 = 0
by setting a(t) = -A/C and b(t) = -B/C.

Factors numerators and denominators of a(t) and b(t) over the current Maple base field and prints:

a(t) and b(t)

factor(numer(a)), factor(denom(a))

factor(numer(b)), factor(denom(b))

the diagonal coefficients A(t), B(t), C(t)

the invariants Delta12 = 4alpha0alpha3 - alpha1^2 and delta_Q (the standard ternary quadratic discriminant used by the script).

Files 

conic_844000.mw (Type (8,4,4,0,0,0) on T_{8,0,0})

Degrees:
sigma00 in degree 8
sigma01, sigma02 in degree 4
sigma11, sigma12, sigma22 constants

Produces a(t), b(t), factorizations, and diagonal data.

Includes optional specializations relevant to unirationality/minimality tests; edit the constraint block to activate.

conic_643210.mw (Type (6,4,3,2,1,0) on T_{3,1,0})

Degrees:
sigma00 in degree 6
sigma01 in degree 4
sigma02 in degree 3
sigma11 in degree 2
sigma12 in degree 1
sigma22 constant

Produces a(t), b(t), factorizations, and diagonal data.

conic_433222.mw (Type (4,3,3,2,2,2) on T_{4,2,2})

Degrees:
sigma00 in degree 4
sigma01, sigma02 in degree 3
sigma11, sigma12, sigma22 in degree 2

Imposes constraints:
a0 = 0, a1 = 0, a3 = 0, a4 = 0,
and b0c3 - c0b3 = 0.
Generic branch assumes b0 != 0 and sets c3 = (c0*b3)/b0. If you want the alternative branches (e.g., b0 = 0), edit the constraint block accordingly.

Produces a(t), b(t), factorizations, and diagonal data.

conic_442420.mw (Type (4,4,2,4,2,0) on T_{2,2,0})

Degrees:
sigma00, sigma01, sigma11 in degree 4
sigma02, sigma12 in degree 2
sigma22 constant

Imposes constraints:
a3 = 0, a4 = 0, c2 = 0.

Produces a(t), b(t), factorizations, and diagonal data.


What the scripts print

Brauer model: a(t) x^2 + b(t) y^2 - z^2 = 0

Factorizations:
numerator(a), denominator(a), numerator(b), denominator(b)

Diagonal data:
A(t), B(t), C(t), Delta12, delta_Q


How to run

Option 1: Open each .mw in Maple and execute all.

Option 2: From Maple command line or your Maple environment, open and run the worksheet. (Exact shell invocation for .mw depends on your Maple setup; typically you double-click and execute within the GUI.)


Parameter specialization

Coefficients are symbolic by default. To specialize, edit the assignment block or use eval on the printed expressions inside Maple. For example:
eval(a_t, {a0=1, a2=0, b1=2, f0=3});
eval(b_t, { ... });


Important assumptions

Characteristic not equal to 2.

The working chart t = x0/x1 is valid (x1 != 0).

The diagonalization formula uses:
alpha0 = sigma22, alpha1 = sigma12, alpha2 = sigma02,
alpha3 = sigma11, alpha4 = sigma01, alpha5 = sigma00.

The routine expects Delta12 = 4alpha0alpha3 - alpha1^2 to be nonzero on the region you are analyzing; if you specialize parameters and this vanishes, the diagonalization degenerates.


Notes on constraints with divisions

Whenever a constraint like b0c3 - c0b3 = 0 is enforced as c3 = (c0*b3)/b0, the worksheet assumes b0 != 0 for that branch. If you need the b0 = 0 branch, edit the constraint block (for example, enforce c0 = 0 when b3 != 0, or drop the constraint if both b0 and b3 are zero so the identity holds automatically).


**Verification script (Magma):** the file `(8,4,4,0,0,0)_Cremonas.txt` symbolically reproduces the Cremona sequence:
1) builds X₈ ⊂ ℙ³ with a 6-fold line and forms the plane octic C = X₈ ∩ (z₁−z₂=0),
2) applies two standard quadratic Cremonas and a final explicit quadratic map,
3) confirms that the image is a smooth conic, hence that C is rational.

**Verification script (Magma):** the file `Cohomology_Normal_Bundle.txt`: computes the cohomology groups of the normal bundle of a smooth conic bundle with degree 8 discriminant for each one of the four types.
