im = imread('low_lum.tif');
top = 1;
bottom = 300;
left = 300;
right = 600;
noiseAnalCrop(im,top,bottom,left,right)




function noise = noiseAnalCrop(im,top,bottom,left,right)
%Accepts RGB image and pixel coordinates of corners of region of interest
%Returns estimate of noise level, as standard deviation divided by mean luminance.





% im        648x676x3 3 channels           2628288 bytes   uint16
% uint [0 - 2^16-1] 
% we cannot computer luminance image from input TIFF file 
% final output of the noise is normalized scalre , which needs to be a double format

% conver uint16 to double ( which is [0-1] )

double_im = im2double(im);

%find the cropping region
% creat a polygone for cropping it

cropped_double_im = double_im(top:bottom,(left:right),:);

cropped_size = size(cropped_double_im);
cropped_size(1);
cropped_size(2);
%size(cropped_double_im)
% compute the standard deviation with respect to all the pixle of that region STD


%%Getting the mean with for loop
lum = zeros(cropped_size(1),cropped_size(2));
for c = 1:cropped_size(1)
    for b = 1:cropped_size(2)
        mean_temp = mean(cropped_double_im(c,b,:));
        lum(c,b) = mean_temp;
    end
end

%Getting the mean with matrix operations

lum_image = mean(cropped_double_im,3)


%lum

std_lum_region = std(lum(:));
mean_lum_region = mean(lum(:));

%lum
%size(lum)
%imshow(lum)

%std_res = std(cropped_double_im(:));

% then divide with with the mean

%mean_res = mean(cropped_double_im(:));


%x = std_lum_region/mean_lum_region
noise = std(lum_image(:))/mean(lum_image(:))


end
