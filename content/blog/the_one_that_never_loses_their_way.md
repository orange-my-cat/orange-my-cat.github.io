---
title: "The One That Never Loses Their Way"
date: 2023-03-02
tags: ["mathematics"]
---

[Eigenvalues and eigenvectors](https://en.wikipedia.org/wiki/Eigenvalues_and_eigenvectors) are often cited as crucial components in data science and machine learning, yet it is perplexing why they are not emphasized more in traditional data science curricula. Seeking answers, I pursued a second major in Mathematics and Statistics in my university.

The study dates back to [1858](https://www.jstor.org/stable/108649), when mathematician Arthur Cayley made a groundbreaking discovery with the Cayley-Hamilton theorem. This theorem states that if *```λ```* (the eigenvalue) is substituted with the original matrix, the characteristic polynomial for a matrix will remain true. Example below:

```
A = [1, 2]
    [2, 1]

which makes the characteristic polynomial be:

det(A-λI) = λ^2 - 2λ - 3

we obviously find λ = -1 and 3 when det(A-λI) = 0

replacing λ with A, 
we find that A^2 - 2A - 3I = 0
```

<br/><br/>

Finding eigenvalues and eigenvectors are quite straightforward. Eigenvalues are found by finding *```λ```* just like in the equation above while eigenvectors have to satisfy *```Av = λv```*. As in the case above: 

```
[1, 2][x] = [λx]
[2, 1][y]   [λy]

when λ = -1:

x + 2y = -x and 2x + y = -y
we find that x = -y
thus, v = [x, -x] 

when λ = 3:
x + 2y = 3x and 2x + y = 3y
we find that x = y
thus, v = [x, x]
```

<br/><br/>

But how is it so important? And what practical applications can be derived from *```λ```* and *```v```*? For starters, we need to understand what is it that we have. We can understand vectors as points in a coordinate system, while multiplying matrices with vectors transforms the vectors. In a 2D plane, we would have a vector [x, y]. In which we can multiply the vector with a 2x2 matrix to transform it. A common matrix would be a scaling matrix as shown below.

```
the scaling matrix in a 2D plane is defined as:

[k, 0]
[0, k]

where k = scale along the x-axis and y-axis
```

<br/><br/>

Knowing that, we can understand the eigenvector as the vector that only changes in scale when transformed by a matrix, while the eigenvalue is the scale which the vector changed. As in the image below, the vectors are scaled in both the x-axis and y-axis. Notice that all vectors in the image is still in its original direction but just scaled by a constant amount. This should mean that any vector can be an eigenvector for the scaling matrix right?
  
![matrix_scaling.png](/blogs/matrix_scaling.png)

```
the characteristic polynomial is defined as:

λ^2 - λk^2 + k^2 = 0

as an example, we let k = 2 to scale the image by 2 times

the characteristic polynomial is then:
λ^2 - 4λ + 4 = 0

we can derive that λ = 2

then we can calculate the eigenvectors using the eigenvalue above

[2, 0][x] = [2x]
[0, 2][y]   [2y]

we get that 2x = 2x and 2y = 2y
therefore our eigenvector would be [x, y]
```

<br/><br/>

This implies that any sets of vectors multiplied by a scaling matrix would just have every vector scaled by the same amount without any change in direction. Makes sense right? Other than the simple scaling matrix, there also exists rotation, translation, reflection, and shearing matrices, which of course is not as easy as the scaling matrix. With this, we can see that eigenvalues and eigenvectors are a big thing in computer graphics. 

In data science however, the vectors provided is not as simple as being coordinates in a plane, they may be entire rows of data or entire columns of data. Here however, we may not need to perform rotations or reflections to the data. Instead, we can use eigenvalues and eigenvectors to perform Principal Component Analysis (PCA). This allows us to significantly reduce the number of variables required for analysis. In PCA, instead of using a transformation matrix, we first need to find the eigenvalues and eigenvectors of its covariance matrix. Then we can easily transform all data points using a single matrix. To learn more about PCA, I recommend watching this [video](https://www.youtube.com/watch?v=FgakZw6K1QQ)!

![eigenvector.png](/blogs/eigenvector.png)