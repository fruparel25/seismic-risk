Socioeconomic exposure model was developed by Nath et al. (2015) utilizing population distribution and land-use land-cover (LULC) classification. Figure 1 depicts the framework adopted to develop seismic exposure of the city. 

&nbsp;&nbsp;&nbsp;&nbsp;![Picture 1](https://github.com/user-attachments/assets/940e5919-7b17-47f1-ba14-5f1ecb6aa92b)






&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Figure 1. Seismic Exposure Flow Diagram.

Street Intersection Density: 

The amount of bends/turns on the road is directly correlated with the number of intersection points shown by SID, which is street intersection points for the city. High-income areas have highways with fewer bends and street intersection sites, whereas lower-income areas have more uneven roadways. The greater the number of street intersection points implies higher risk and vice versa.

Figure 2(a) displays the ward data for Nagpur. On the streets extracted for the extent of Nagpur through Geoinformatics world as shown in Figure 2(b), the line intersection algorithm is applied. In order to prevent duplicate intersection locations, adjacent road segments must be combined as shown in Figure 2(c) using the dissolve technique from QGIS's vector geometry toolbox. Figure 2(d) shows the intersection points for Gandhibagh region (low income area). Street intersection density for Nagpur city is categorized in a grid size (100m X 100m) as shown in Figure 11(a).

<img width="797" alt="Screenshot 2025-02-02 at 12 45 51 PM" src="https://github.com/user-attachments/assets/943b72b7-fbe0-4dc4-adcf-ae1e0e8c080a" />

Built-up Density:

It should be emphasized that a hazard is meaningless in and of itself until it affects vulnerable infrastructure. The Mapflows.ai API, which is a deep learning model was used to extract the Nagpur city plan area as shown Figure 3(a). Over 1.5 million buildings were identified in all capturing 393.5 km2 of rooftops (Figure 3(a)) using high resolution satellite images with a processing time of 800 minutes. Classification of built-up density is taken in grid (100m x 100m) as shown in Figure 11(b). Figure 3(b) shows the magnified view of building footprints at Shivaji Nagar, Nagpur.

<img width="783" alt="Screenshot 2025-02-02 at 12 49 22 PM" src="https://github.com/user-attachments/assets/7ae4738e-3824-410d-8c15-cce32caa9179" />



