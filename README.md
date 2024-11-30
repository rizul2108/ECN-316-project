### **Removal of Haze for Underwater Images based on Contrast & Improvement of Color using the Fusion Method**

### **Introduction:**

The underwater environment presents unique challenges for image capture due to factors such as light absorption and scattering. These lead to images with poor visibility, reduced color contrast, and sharpness. This project introduces an effective image enhancement technique using a single image approach without requiring specialized hardware. The technique relies on blending two images derived from color-corrected and white-balanced versions of the original image, utilizing multi-scale fusion to enhance the final output. The enhanced images show improved global contrast, better exposedness of dark regions, and sharpness in edges, making them ideal for various applications such as underwater inspection, marine biology, and archeological documentation.

Traditional enhancement methods such as gamma correction and histogram equalization struggle to restore underwater images effectively due to the combination of additive and multiplicative processes that cause image degradation. This project addresses these challenges using a fusion-based approach that blends a contrast-enhanced and a white-balanced image, leveraging multi-scale fusion to produce high-quality enhanced outputs.

**Methodology:**

The implemented method involves a two-step approach:

1. **White-Balancing:**
   - White-balancing is applied to correct the color cast caused by selective absorption in water. Red wavelengths are absorbed first, followed by green and blue. This results in an image dominated by bluish and greenish tones.
   - The algorithm compensates for this by enhancing the red channel using a proportional addition of green, ensuring a balanced and natural color distribution.
2. **Fusion-Based Enhancement:**
   - Two images are derived from the white-balanced version:
     1. **Gamma-Corrected Image**: Enhances global contrast.
     2. **Sharpened Image**: Uses unsharp masking to highlight edges.
   - These two images are fused using a multi-scale fusion technique that merges them based on their weight maps. Three weight maps are used:
     1. **Laplacian Contrast Weight Map**: Measures edge sharpness.
     2. **Saliency Weight Map**: Highlights prominent objects. We didn't implement it as it required ML knowledge in it.
     3. **Saturation Weight Map**: Enhances color regions.
3. The final output is a fusion of the two images, ensuring high contrast, sharp edges, and balanced colors.

### **Algorithm:**

The algorithm can be divided into four significant steps:

1. **Input Preparation:**
   - Capture an underwater image and apply white balancing to obtain a color-corrected version.
2. **Preprocessing:**
   - Apply gamma correction and unsharp masking to derive two processed versions.
3. **Weight Map Calculation:**
   - Compute weight maps for each input image's contrast, saliency, and saturation.
4. **Multi-scale Fusion:**
   - Use Gaussian and Laplacian pyramids to blend the images according to their weight maps. Reconstruct the final enhanced image by summing the pyramid levels.

### **References:**

1. C. O. Ancuti et al., "Color Balance and Fusion for Underwater Image Enhancement," _IEEE Transactions on Image Processing_, vol. 27, no. 1, pp. 379-393, 2018\.
2. J. Y. Chiang and Y. C. Chen, "Underwater Image Enhancement by Wavelength Compensation and Dehazing," _IEEE Transactions on Image Processing_, vol. 21, no. 4, pp. 1756-1769, 2012\.
