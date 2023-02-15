# Gamma-Radiation-Image-Enhancement-using-Matlab
matlab code for gamma radiation image enhancement 


% Read in the image
I = imread('image.jpg');

% Specify the gamma values for each color channel
gamma_r = 1.8;
gamma_g = 1.5;
gamma_b = 2.2;

% Perform gamma correction on each color channel
I_gamma(:,:,1) = imadjust(I(:,:,1), [], [], gamma_r);
I_gamma(:,:,2) = imadjust(I(:,:,2), [], [], gamma_g);
I_gamma(:,:,3) = imadjust(I(:,:,3), [], [], gamma_b);

% Perform histogram equalization on each color channel
I_heq(:,:,1) = histeq(I_gamma(:,:,1));
I_heq(:,:,2) = histeq(I_gamma(:,:,2));
I_heq(:,:,3) = histeq(I_gamma(:,:,3));

% Perform color balance adjustment on the image
I_cba = chromadapt(I_heq, grayworld(I_heq));

% Display the original and enhanced images side by side
figure;
subplot(1, 2, 1);
imshow(I);
title('Original Image');
subplot(1, 2, 2);
imshow(I_cba);
title('Enhanced Image');

