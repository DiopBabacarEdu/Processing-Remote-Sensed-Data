
```python
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
% Sket to plot an elevation profile map
% From the Netcdf format
% dimensions:
%        columns = 4865 ;
%        rows = 4091 ;
% variables:
%       short altitude(rows, columns) ;
%                altitude:_FillValue = -32768s ;
%                altitude:long_name = "DEM corrected altitude" ;
%                altitude:standard_name = "altitude" ;
%               altitude:units = "m" ;
%                altitude:valid_max = 9000s ;
%               altitude:valid_min = -1000s ;
%        int latitude(rows, columns) ;
%                latitude:_FillValue = -2147483648 ;
%                latitude:long_name = "DEM corrected latitude" ;
%                latitude:scale_factor = 1.e-06 ;
%                latitude:standard_name = "latitude" ;
%                latitude:units = "degrees_north" ;
%                latitude:valid_max = 90000000 ;
%               latitude:valid_min = -90000000 ;
%        int longitude(rows, columns) ;
%                longitude:_FillValue = -2147483648 ;
%                longitude:long_name = "DEM corrected longitude" ;
%                longitude:scale_factor = 1.e-06 ;
%               longitude:standard_name = "longitude" ;
%                longitude:units = "degrees_east" ;
%                longitude:valid_max = 180000000 ;
%                longitude:valid_min = -180000000 ;
%
%// global attributes:
%                :absolute_orbit_number = 5585U ;
%                :ac_subsampling_factor = 64US ;
%                :al_subsampling_factor = 1US ;
%                :comment = " " ;
%                :contact = "EOHElp@esa.int" ;
%                :creation_time = "2017-03-14T12:45:35Z" ;
%                :institution = "SVL" ;
%                :netCDF_version = "4.2 of Jul  5 2012 17:07:43 $" ;
%                :product_name = "S3A_OL_1_EFR____20170314T104031_20170314T104331_20170314T124535_0180_015_222_2700_SVL_O_NR_002.SEN3" ;
%                :references = "S3IPF PDS 004 - i2r1 - Product Data Format Specification - OLCI, S3IPF PDS 002 - i1r6 - Product Data Format Specification - Product Structures, S3IPF DPM 002 - i2r1 - Detailed Processing Model - OLCI Level 1" ;
%                :resolution = "[ 270 294 ]" ;
%                :source = "IPF-OL-1-EO 06.06" ;
%                :start_time = "2017-03-14T10:40:31.980635Z" ;
%                :stop_time = "2017-03-14T10:43:31.945580Z" ;
%                :title = "OLCI Level 1b Product, Geo Coordinates Data Set" ;
%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
clc
clear all

ncdisp('geo_coordinates.nc','altitude');
peaksData  = ncread('geo_coordinates.nc','altitude');
surf(double(peaksData));

% From 2D to 1D array
peaksData1D = peaksData(:);

elevation_matrix = reshape(peaksData1D, length(peaksData), []);
rows = (1:4091);
imagesc(rows,peaksData1D,elevation_matrix);
xticks(rows);
colorbar;
```
