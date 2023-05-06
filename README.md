Download Link: https://assignmentchef.com/product/solved-ee5176-assignment-3-high-dynamic-rangehdr-imaging
<br>
<h1></h1>

<h2>HDR Imaging</h2>

The purpose of this assignment is to explore high dynamic range (HDR) imaging. HDR imaging is one of the multi-imaging techniques which recovers high dynamic range image from the multiple images of a scene taken from same vantage point. Here multiple photographs of the scene are taken with different amounts of exposure. This algorithm uses these differently exposed photographs to recover the response function of the imaging process, up to factor of scale. With the known response function, the algorithm can fuse the multiple photographs into a single, high dynamic range image whose pixel values are proportional to the true radiance values in the scene. This radiance values of the image are to be tonemapped to shown it on a display. For this you will use an exposure stack collected from camera (Nikon D3300). For reference, both exposure stacks are captured with fixed aperture and ISO, and with shutter speeds equal to , where k ∈ {1<em>,…..,</em>16} is the index in an image’s file name.

Figure 1: From left to right: Two Low Dynamic Range(LDR) exposures, and an HDR composite tonemapped using the photographic tonemapping.

<h2>1          Camera Response Function(CRF) Estimation</h2>

The rendered(jpg) images obtained from the camera have non-linear response with respect to scene radiance. So before you can merge them into an HDR image, you first need to estimate the camera response function in order to undo this non-linearity. You will do this using the method by Debevec and Malik [1], you can find this in section 2.1 which explains the method. Pseudo code for the same has been given at the end of the paper. Plot the function ‘g’ mentioned in the section 2.1 and report the same.

<h2>2          Constructing the HDR Radiance Map</h2>

Given a set of k(16) LDR linear images corresponding to different exposures <em>t<sub>k</sub></em>, we can merge them into an HDR image. HDR image is obtained as the weighted sum of LDF images. These weights are used to place more emphasis on well-exposed pixels, and less emphasis on under-exposed or over-exposed ones from each LDR image. Implement it following the steps given in section 2.2 of Debevec and Malik [1]. Then, store the resulting HDR images as .EXR files, which is an open source high dynamic range file format. To do this you can use existing python or MATLAB library. Include this file in your submission.

<h2>3       Photographic tonemapping</h2>

Now that you have an HDR image, you need to tonemap it so that you can display them. You can use the following tonemapping algorithm. Given pixel values <em>I<sub>ij,HDR </sub></em>of a linear HDR image, photographic tonemapping is performed as

(1)

<em>I</em>˜<em>white </em>= <em>B </em>· max(<em>I</em>˜<em>ij,HDR</em>)        (2) <em>i,j</em>

(3)

(4)

The parameter K is the key, and determines how bright or dark the resulting tonemapped rendition is. The parameter B is the burn, and can be used to suppress the contrast of the result. Finally, N is the number of pixels, and <em> </em>is a small constant to avoid the singularity of the logarithm function at 0. Apply it by tonemapping each color channel separately in the same way. Experiment with different key and burn values. Some reasonable starting values for the parameters are K = 0.15 and B = 0.95, but to get good tonemaps you will need to explore different values.

<ul>

 <li>Set <em>I</em><sup>˜</sup><em><sub>white </sub></em>= ∞ and vary the K around the given value and report the best 3 visually appealing tonemapped HDR results with corresponding K value.</li>

 <li>Very both K and B around the given values and report the best 3 visually appealing tonemapped HDR results with corresponding K and B values.</li>

 <li>Have you observed the difference between the above two results? If yes, state your conclusions with valid reasons.</li>

</ul>

<h2>References</h2>

[1] Paul E Debevec and Jitendra Malik, “Recovering high dynamic range radiance maps from photographs,” in <em>ACM SIGGRAPH 2008 </em>