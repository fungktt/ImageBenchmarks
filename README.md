## Benchmarking Images.jl (Julia), OpenCV (Python), and scikit-image (Python)

Here, I will be calculating the mean of all of the following features in these 3 packages. <br/>
For benchmarking in Julia, I used [BenchmarkTools.jl](https://github.com/JuliaCI/BenchmarkTools.jl) and the marcro <code>@benchmark</code>. <br/>
For benchmarking in Python, I used the [timeit function](https://docs.python.org/2/library/timeit.html) to calculate the execution time. <br/>
The timeit function is called according to the number of samples BenchmarkTools takes automatically. <br/>

<br/>

| Feature                             | Images.jl  | OpenCV     | scikit-image |
|-------------------------------------|------------|------------|--------------|
| Loading an image                    | 395.282 ms | 64.078 ms  | 108.628 ms   |
| Displaying an image                 | 355.328 ms | 8.862 ms   | 369.267 ms   |
| Saving an image                     | 706.732 ms | 100.882 ms | 5.827 ms     |
| Displaying image size               | 51.257 ns  | 189.199 ns | 198.249 ns   |
| Applying Laplacian filtering        | 80.182 ms  | 13.625 ms  | 95.63 ms     |
| Applying Gaussian filtering         | 529.559 ms | 1.054 ms   | 132.463 ms   |
| Arbitrary resizing                  | 30.540 ms  | 0.408 ms   | 176.474 ms   |
| Image rotation                      | 284.137 ms | 3.91 ms    | 275.552 ms   |
| Filling an image black              | 90.772 ns  | 12.128 ms  | 12.28 ms     |
| Grayscaling                         | 20.687 ms  | 0.405 ms   | 22.007 ms    |
| Converting to an HSV representation | 59.745 ms  | 1.041 ms   | 434.09 ms    |
| Getting a grayscale histogram       | 226.654 ms | 1.582 ms   | 30.512 ms    |
| Getting a histogram equalised image | 438.124 ms | 1.071 ms   | 251.342 ms   |
| Getting a gamma corrected image     | 594.044 ms | 2.308 ms   | 187.379 ms   |

<br/>

From the results above, we can conclude that OpenCV is the fastest package in general out of the 3 benchmarked here. Many of the features were computed under 15 ms by OpenCV, whereas many by scikit-image were between 100-300 ms.
But interestingly, Images.jl is overall the slowest package of the 3, especially the fact that it takes a very long time to load, display, save, Guassian-filter and gamma-correct images.
Therefore, we can fairly say that there is some room for improvement in Images.jl.

As for why OpenCV is very fast compared to the others, it may be because OpenCV is heavily-funded and well established for a long time and written naively in C++. This can be seen in the difference between OpenCV and scikit-image, which uses Python and its PyPlot libraries.

Below are the 3 files that I created for each package, containing the code. Thanks for reading!
