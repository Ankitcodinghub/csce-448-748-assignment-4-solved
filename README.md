# csce-448-748-assignment-4-solved
**TO GET THIS SOLUTION VISIT:** [CSCE 448/748 Assignment 4 Solved](https://www.ankitcodinghub.com/product/csce-448-748-computational-photography-solved-2/)


---

📩 **If you need this solution or have special requests:** **Email:** ankitcoding@gmail.com  
📱 **WhatsApp:** +1 419 877 7882  
📄 **Get a quote instantly using this form:** [Ask Homework Questions](https://www.ankitcodinghub.com/services/ask-homework-questions/)

*We deliver fast, professional, and affordable academic help.*

---

<h2>Description</h2>



<div class="kk-star-ratings kksr-auto kksr-align-center kksr-valign-top" data-payload="{&quot;align&quot;:&quot;center&quot;,&quot;id&quot;:&quot;127234&quot;,&quot;slug&quot;:&quot;default&quot;,&quot;valign&quot;:&quot;top&quot;,&quot;ignore&quot;:&quot;&quot;,&quot;reference&quot;:&quot;auto&quot;,&quot;class&quot;:&quot;&quot;,&quot;count&quot;:&quot;1&quot;,&quot;legendonly&quot;:&quot;&quot;,&quot;readonly&quot;:&quot;&quot;,&quot;score&quot;:&quot;5&quot;,&quot;starsonly&quot;:&quot;&quot;,&quot;best&quot;:&quot;5&quot;,&quot;gap&quot;:&quot;4&quot;,&quot;greet&quot;:&quot;Rate this product&quot;,&quot;legend&quot;:&quot;5\/5 - (1 vote)&quot;,&quot;size&quot;:&quot;24&quot;,&quot;title&quot;:&quot;CSCE 448\/748 Assignment 4 Solved&quot;,&quot;width&quot;:&quot;138&quot;,&quot;_legend&quot;:&quot;{score}\/{best} - ({count} {votes})&quot;,&quot;font_factor&quot;:&quot;1.25&quot;}">

<div class="kksr-stars">

<div class="kksr-stars-inactive">
            <div class="kksr-star" data-star="1" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="2" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="3" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="4" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" data-star="5" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>

<div class="kksr-stars-active" style="width: 138px;">
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
            <div class="kksr-star" style="padding-right: 4px">


<div class="kksr-icon" style="width: 24px; height: 24px;"></div>
        </div>
    </div>
</div>


<div class="kksr-legend" style="font-size: 19.2px;">
            5/5 - (1 vote)    </div>
    </div>
Programming Assignment 4

1 Goal

The goal of this project is to perform gradient domain image blending. Basically, given a source image and a mask, our goal is to seamlessy blend the masked areas of the source image into a target photograph.

2 Starter Code

Starter code (in Python) along with the images can be downloaded from here. Note that, expected results for a few images are included in the “Results” folder.

3 Main Task

Here, you are required to implement gradient domain image blending, described in Perez, et al.’s paper. Your implementation should run properly on all the examples (which means you need to handle the boundary conditions – see Sec. 3.3), however, you will only be able to produce high-quality results on images 1 to 5 (images 6 and 7 require Poisson blending with mixing gradients – see Extra Credit). To get the full point, you need to create one composite of your own. You can use the GetMask function to obtain a mask on your images.

The implementation of gradiant domain blending is not complicated, but it is easy to make a mistake. Below we provide a detailed description of the process for a simple 1D case and then extend it to 2D.

3.1 Simple 1D Example

Note: the following guide is for MATLAB, but there are similar functions in python as well. You can find equivalent functions by seraching “Similar function to MATLAB X in Python”.

Here, we are going to discuss a simple 1D case to get you started with implementing the 2D case.

3.1.1 Hole-Filling

Let’s start with a simple case where instead of copying in new gradients we only want to fill in a missing region of an image and keep the gradients as smooth (close to zero) as possible. To simplify things further, let’s start with a one dimensional signal instead of a two dimensional image.

Here is our signal t (see Fig. 1) and a mask M specifying which “pixels” are missing.

t = [5 4 0 0 0 0 2 4]; M = [0 0 1 1 1 1 0 0];

M = logical(M); % converting the mask from double to binary

We can formulate our objective as a least squares problem. Given the intensity values of t, we want to solve for new intensity values v under the mask M such that:

v = argmin X (vi − vj)2, with vi = ti for all i ∈ ∼ M. (1)

v

&lt;i,j&gt;∈M

Here, i is a coordinate (1d or 2d) for each pixel under mask M. Each j is a neighbor of i. The summation guides the gradient (the local pixel differences) in all directions to be close to 0. Minimizing this equation could be called a Poisson fill.

Figure 1: On the left, we show the target signal t. The goal is to fill in the samples 3 to 6 smoothly using the Poisson equation. On the right, we show the filled in result tsmoothed.

For this example let’s define neighborhood to be the pixel to your left. The optimal pixel values can be obtained by setting the derivative of the above equation equal to zero. This gives us two equations at each pixel as follows:

for all i ∈ M, vi − vi−1 = 0 and vi+1− vi = 0, (2)

where vj = tj for all j ∈∼ M. This produces the following system of equations:

v(1) – t(2) = 0; %left border v(2) – v(1) = 0; v(3) – v(2) = 0; v(4) – v(3) = 0; t(7) – v(4) = 0; %right border

Note that the coordinates do not directly correspond between v and t. For example, v(1), the first unknown pixel, sits on top of t(3). You could formulate it differently if you choose. Plugging in known values of t we get:

v(1) – 4 = 0; v(2) – v(1) = 0; v(3) – v(2) = 0; v(4) – v(3) = 0; 2 – v(4) = 0;

Now let’s convert this to matrix form and have Matlab solve it for us

A = [ 1 0 0 0; …

-1 1 0 0; …

0 -1 1 0; …

0 0 -1 1; …

0 0 0 -1];

b = [4; 0; 0; 0; -2];

v = A; % “help mldivide” describes the ’’ operator.

t_smoothed = zeros(size(t)); t_smoothed(˜M) = t(˜M); t_smoothed( M) = v;

As it turns out, in the 1d case, the Poisson fill is simply a linear interpolation between the boundary values. But in 2d the Poisson fill exhibits more complexity.

3.1.2 Blending Source

Now instead of just doing a fill, let’s try to seamlessly blend content from one 1d signal into another. We’ll fill the missing values in t using the corresponding values in s (see Fig. 2):

s = [8 6 7 2 4 5 7 8];

Now our objective changes. Instead of trying to minimize the gradients, we want the gradients to match another set of gradients (those in s). Therefore, our set of equations changes as follows:

v(1) – t(2) = s(3) – s(2); v(2) – v(1) = s(4) – s(3); v(3) – v(2) = s(5) – s(4); v(4) – v(3) = s(6) – s(5); t(7) – v(4) = s(7) – s(6);

After plugging in known values from t and s this becomes:

v(1) – 4 = 1; v(2) – v(1) = -5; v(3) – v(2) = 2; v(4) – v(3) = 1; 2 – v(4) = 2;

Finally, in matrix form for MATLAB

A = [ 1 0 0 0; …

-1 1 0 0; …

0 -1 1 0; …

0 0 -1 1; …

0 0 0 -1];

b = [5; -5; 2; 1; 0];

v = A;

t_and_s_blended = zeros(size(t)); t_and_s_blended(˜M) = t(˜M); t_and_s_blended( M) = v;

Notice that in our quest to preserve gradients without regard for intensity we might have gone too far. Our signal now has negative values. The same thing can happen in the image domain, so you’ll want to watch for that and at the very least clamp values back to the valid range.

Figure 2: On the left, we show the source signal s. The goal is to blend this source signal with the target from Fig. 1. On the right, we show the blended result tandsblended.

3.2 Extension to 2D

When working with images, the basic idea is the same as above, except that each pixel has at least two neighbors (left and top) and possibly four neighbors. Either formulation will work. For example, in a 2d image using a 4-connected neighborhood, our equations above imply that for a single pixel in v, at coordinate (i,j) which is fully under the mask you would have the following equations:

v(i,j) – v(i-1, j) = s(i,j) – s(i-1, j); v(i,j) – v(i+1, j) = s(i,j) – s(i+1, j); v(i,j) – v(i, j-1) = s(i,j) – s(i, j-1); v(i,j) – v(i, j+1) = s(i,j) – s(i, j+1);

4*v(i,j) – v(i-1, j) – v(i+1, j) – v(i, j-1) – v(i, j+1) =

4*s(i,j) – s(i-1, j) – s(i+1, j) – s(i, j-1) – s(i, j+1);

where everything on the right hand side is known. This formulation is similar to equation 8 in Perez, et al.’s´ paper. You can read the paper, especially the “Discrete Poisson Solver”, if you want more guidance.

3.3 Hints

• For color images, process each color channel independently (hint: matrix A will not change, so don’t go through the computational expense of rebuilding it for each color channel).

• The linear system of equations (and thus the matrix A) becomes enormous. But A is also very sparse because each equation only relates a pixel to some number of its immediate neighbors.

• You will need to keep track of the relationship between coordinates in matrix A and image coordinates. You might need a dedicated data structure to keep track of the mapping between rows and columns of A and pixels in s and t.

• Not every pixel has left, right, top, and bottom neighbors. Handling these boundary conditions might get slightly messy. You can start by assuming that all masked pixels have 4 neighbors (this is true for the majority of cases), but your code should properly handle the boundary conditions (image 7).

• Your algorithm can be made significantly faster by finding all the A matrix values and coordinates ahead of time and then constructing the sparse matrix in one operation. This should speed up blending from minutes to seconds.

4 Extra Credit

Mixing Gradients – Mixing Gradients to allow transparent images or images with holes. Instead of trying to adhere to the gradients of the source image, at each masked pixel use the largest gradient available in either the source or target. You can test your implementation on images 6 and 7. Note that mixing gradients is different from average gradients. You won’t receive any points for implementing average gradients.

5 Write Up

Include all the results in your report. For each result, you should show the input images, as well as the naive blending along with your blended result. Describe how you implemented the assignment. Discuss any problem you faced when implementing the assignment or any decisions you had to make.

6 Graduate Credit

Graduate students have to do the extra credit.

7 Deliverables

Your entire project should be in a folder called “firstnamelastname”. This folder should be zipped up and submitted through e-campus. Inside the folder, you should have the followings:

• A folder named “Code” containing all the codes for this assignment. Please include a README file to explain what each file does if you add any other files to the starter code.

• A report in the pdf format. Make sure you write your name on top of the report. Also make sure the pdf file is under 5 MB.

Make sure you exclude all the results and original images from your submission.

8 Checklist

Make sure you can check all the items below before submitting your assignment. You will lose 5 points for each item that cannot be checked.

The folder is named properly (“firstnamelastname”). Note between first and last name. The folder structure should be exactly as follows

“firstname lastname.zip”

– “firstname lastname”

∗ “Code”

∗ Report.pdf

Inside the root folder, there is a folder called “Code” that contains your source code. Also make sure the report is in the root folder.

The folders “Images” and “Results” are not included (you only submit your codes and a report).

Name written on top of the report.

The report is in pdf format and the file is under 5 MB.

9 Ruberic

Total credit: [100 points]

[55 points] – Implement Poisson blending

[15 points] – Implement the approach efficiently using sparse matrix

[10 points] – Handle the boundary condition

[10 points] – Include one example of your own

[10 points] – Write up

Extra credit: [15 points]

[15 points] – Mixing gradients

10 Acknowlegements

The project is derived from James Hays Computational Photography course with permission.
