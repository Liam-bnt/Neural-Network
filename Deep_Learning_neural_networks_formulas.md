

## Neural Network – Formulas Summary
Liam Beaudet-Nallet
## October 2026
In this document, "." corresponds to the matrix product while "x" corresponds to multiplication.
1  For 1 neuron
## Definitions
Let m be the number of examples and 10 the number of features.
## X =
## ⎡
## ⎢
## ⎢
## ⎢
## ⎢
## ⎣
x
## (1)
## 1
x
## (1)
## 2
···  x
## (1)
## 10
x
## (2)
## 1
x
## (2)
## 2
···  x
## (2)
## 10
## .
## .
## .
## .
## .
## .
## .
## .
## .
## .
## .
## .
x
## (m)
## 1
x
## (m)
## 2
···  x
## (m)
## 10
## ⎤
## ⎥
## ⎥
## ⎥
## ⎥
## ⎦
## ∈R
m×10
## W =
## ⎡
## ⎢
## ⎢
## ⎢
## ⎣
w
## 1
w
## 2
## .
## .
## .
w
## 10
## ⎤
## ⎥
## ⎥
## ⎥
## ⎦
## ∈R
## 10×1
b∈R
## Model
Z = X · W + b
## A =
## 1
1 + e
## −Z
Cost function
## L =−
## 1
m
m
## ∑︂
i=1
y× log(A) + (1− y)× log(1− A)
Gradient descent
## W
n+1
## = W
n
− α
## ∂L
## ∂W
## (︃
## ∂L
## ∂W
## =
## 1
m
## X
## T
· (A− y)
## )︃
b
n+1
= b
n
− α
## ∂L
## ∂b
## (︃
## ∂L
## ∂b
## =
## 1
m
## ∑︂
(A− y)
## )︃
## 2  Neural Network
## Notation
## • W
## [l]
ij
: weight of layer l, for neuron i of that layer, connected to input j.
- b
## [l]
i
: bias of neuron i in layer l.
## 1

- z
## [l]
i
: linear output (pre-activation) of neuron i in layer l.
- a
## [l]
i
: activation (output) of neuron i in layer l.
## • Z
## [l]
## , A
## [l]
## , W
## [l]
, b
## [l]
: matrices/vectors gathering these quantities for the whole layer l.
Two conventions forZ
## [1]
The number m of training examples can be placed either on the rows or on the columns of the
matrices. Both conventions are equivalent: one is obtained from the other by transposition. Starting
from the row version Z = X·W +b, we transpose the matrix product and the bias to get the transpose
of Z:
(X · W + b)
## T
## = W
## T
## · X
## T
+ b
## T
## .
The weight matrix of the row version is therefore the transpose of the one in the column version,
and b goes from a row vector to a column vector. The column version has the advantage of making
the computation easier to visualize row by row: each row of W
## [1]
holds the weights of one neuron,
so each row of Z
## [1]
is the output of one neuron for all examples, as if the data flowed through the
neurons laid out in a column.
Convention 1: examples on the rows (shown here with 2 neurons)
## Z
## [1]
## =
## ⎡
## ⎢
## ⎢
## ⎢
## ⎢
## ⎣
x
## (1)
## 1
x
## (1)
## 2
x
## (2)
## 1
x
## (2)
## 2
## .
## .
## .
## .
## .
## .
x
## (m)
## 1
x
## (m)
## 2
## ⎤
## ⎥
## ⎥
## ⎥
## ⎥
## ⎦
## ⏞
## ⏟⏟⏞
## X∈R
m×2
## ·
## [︄
w
## [1]
## 11
w
## [1]
## 21
w
## [1]
## 12
w
## [1]
## 22
## ]︄
## ⏞
## ⏟⏟⏞
## W
## [1]
## ∈R
## 2×2
## +
## [︂
b
## [1]
## 1
b
## [1]
## 2
## ]︂
## ⏞
## ⏟⏟⏞
b
## [1]
## ∈R
## 1×2
## =
## ⎡
## ⎢
## ⎢
## ⎢
## ⎢
## ⎣
z
## [1](1)
## 1
z
## [1](1)
## 2
z
## [1](2)
## 1
z
## [1](2)
## 2
## .
## .
## .
## .
## .
## .
z
## [1](m)
## 1
z
## [1](m)
## 2
## ⎤
## ⎥
## ⎥
## ⎥
## ⎥
## ⎦
## ⏞
## ⏟⏟⏞
## Z
## [1]
## ∈R
m×2
Convention 2: examples on the columns (shown here with 3 neurons, and the one used in the
rest of this section)
## Z
## [1]
## =
## ⎡
## ⎢
## ⎣
w
## [1]
## 11
w
## [1]
## 12
w
## [1]
## 21
w
## [1]
## 22
w
## [1]
## 31
w
## [1]
## 32
## ⎤
## ⎥
## ⎦
## ⏞
## ⏟⏟⏞
## W
## [1]
## ∈R
## 3×2
## ·
## [︄
x
## (1)
## 1
x
## (2)
## 1
···  x
## (m)
## 1
x
## (1)
## 2
x
## (2)
## 2
···  x
## (m)
## 2
## ]︄
## ⏞
## ⏟⏟⏞
## X∈R
## 2×m
## +
## ⎡
## ⎢
## ⎣
b
## [1]
## 1
b
## [1]
## 2
b
## [1]
## 3
## ⎤
## ⎥
## ⎦
## ⏞
## ⏟⏟⏞
b
## [1]
## ∈R
## 3×1
## =
## ⎡
## ⎢
## ⎣
z
## [1](1)
## 1
z
## [1](2)
## 1
···  z
## [1](m)
## 1
z
## [1](1)
## 2
z
## [1](2)
## 2
···  z
## [1](m)
## 2
z
## [1](1)
## 3
z
## [1](2)
## 3
···  z
## [1](m)
## 3
## ⎤
## ⎥
## ⎦
## ⏞
## ⏟⏟⏞
## Z
## [1]
## ∈R
## 3×m
Forward propagation
## Z
## [1]
## = W
## [1]
· X + b
## [1]
## A
## [1]
## =
## 1
1 + e
## −Z
## [1]
## Z
## [2]
## = W
## [2]
## · A
## [1]
+ b
## [2]
## A
## [2]
## =
## 1
1 + e
## −Z
## [2]
Cost function
## L =−
## 1
m
## ∑︂
y× log(A
## [2]
) + (1− y)× log(1− A
## [2]
## )
## 2

Gradients for backpropagation
## ∂L
## ∂W
## [2]
## =
## ∂L
## ∂A
## [2]
## ×
## ∂A
## [2]
## ∂Z
## [2]
## ×
## ∂Z
## [2]
## ∂W
## [2]
## ∂L
## ∂b
## [2]
## =
## ∂L
## ∂A
## [2]
## ×
## ∂A
## [2]
## ∂Z
## [2]
## ×
## ∂Z
## [2]
## ∂b
## [2]
## ∂L
## ∂W
## [1]
## =
## ∂L
## ∂A
## [2]
## ×
## ∂A
## [2]
## ∂Z
## [2]
## ×
## ∂Z
## [2]
## ∂A
## [1]
## ×
## ∂A
## [1]
## ∂Z
## [1]
## ×
## ∂Z
## [1]
## ∂W
## [1]
## ∂L
## ∂b
## [1]
## =
## ∂L
## ∂A
## [2]
## ×
## ∂A
## [2]
## ∂Z
## [2]
## ×
## ∂Z
## [2]
## ∂A
## [1]
## ×
## ∂A
## [1]
## ∂Z
## [1]
## ×
## ∂Z
## [1]
## ∂b
## [1]
Simplified gradients
We set
dZ
## 2
## =
## ∂L
## ∂A
## [2]
## ×
## ∂A
## [2]
## ∂Z
## [2]
dZ
## 1
= dZ
## 2
## ×
## ∂Z
## [2]
## ∂A
## [1]
## ×
## ∂A
## [1]
## ∂Z
## [1]
so that the gradients become
## ∂L
## ∂W
## [2]
= dZ
## 2
## ×
## ∂Z
## [2]
## ∂W
## [2]
## ∂L
## ∂b
## [2]
= dZ
## 2
## ×
## ∂Z
## [2]
## ∂b
## [2]
## ∂L
## ∂W
## [1]
= dZ
## 1
## ×
## ∂Z
## [1]
## ∂W
## [1]
## ∂L
## ∂b
## [1]
= dZ
## 1
## ×
## ∂Z
## [1]
## ∂b
## [1]
That gives
dZ
## 2
## = A
## [2]
− y
dZ
## 1
## = W
## [2]T
· dZ
## 2
## × A
## [1]
## (︂
## 1− A
## [1]
## )︂
## ∂L
## ∂W
## [2]
## =
## 1
m
dZ
## 2
## · A
## [1]T
## ∂L
## ∂b
## [2]
## =
## 1
m
## ∑︂
axis 1
dZ
## 2
## ∂L
## ∂W
## [1]
## =
## 1
m
dZ
## 1
## · X
## T
## ∂L
## ∂b
## [1]
## =
## 1
m
## ∑︂
axis 1
dZ
## 1
## 3

## 3  Concepts
## Broadcasting
Definition. Broadcasting is the mechanism that allows an operation (addition, multiplication, . . . )
between arrays of different shapes, by automatically “stretching” the smaller array so that both
shapes match, without actually copying the data.
Rule. Compare the shapes of the two arrays starting from the last dimension and moving left.
Two dimensions are compatible if:
- they are equal, or
- one of them is equal to 1. If so, then the dimension is stretched to match the other.
If a dimension is missing, it is treated as 1.  If a pair of dimensions is neither equal nor 1, the
operation fails.
Example. In Z = X·W +b, the product X·W has shape (m, 1) and b is a scalar: b is broadcast
and added to each of the m rows.
## Over-fitting
Definition. Overfitting occurs when a model fits the training data too closely (including its noise),
so that the training error is very low but the error on new, unseen data is high: the model does not
generalize.
Solution. Reduce the model’s ability to memorize the training set:
- get more training data;
- add regularization (L2 penalty on the weights, dropout);
- use early stopping, monitoring the error on a validation set;
- simplify the model (fewer layers or neurons).
## 4