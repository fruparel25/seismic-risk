Socioeconomic exposure model was developed by Nath et al. (2015) utilizing population distribution and land-use land-cover (LULC) classification. Figure 1 depicts the framework adopted to develop seismic exposure of the city. 

&nbsp;&nbsp;&nbsp;&nbsp;![Picture 1](https://github.com/user-attachments/assets/940e5919-7b17-47f1-ba14-5f1ecb6aa92b)






&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Figure 1. Seismic Exposure Flow Diagram.

1. Street Intersection Density: 

The amount of bends/turns on the road is directly correlated with the number of intersection points shown by SID, which is street intersection points for the city. High-income areas have highways with fewer bends and street intersection sites, whereas lower-income areas have more uneven roadways. The greater the number of street intersection points implies higher risk and vice versa.

Figure 2(a) displays the ward data for Nagpur. On the streets extracted for the extent of Nagpur through Geoinformatics world as shown in Figure 2(b), the line intersection algorithm is applied. In order to prevent duplicate intersection locations, adjacent road segments must be combined as shown in Figure 2(c) using the dissolve technique from QGIS's vector geometry toolbox. Figure 2(d) shows the intersection points for Gandhibagh region (low income area). Street intersection density for Nagpur city is categorized in a grid size (100m X 100m) as shown in Figure 11(a).

<img width="797" alt="Screenshot 2025-02-02 at 12 45 51 PM" src="https://github.com/user-attachments/assets/943b72b7-fbe0-4dc4-adcf-ae1e0e8c080a" />

2. Built-up Density:

It should be emphasized that a hazard is meaningless in and of itself until it affects vulnerable infrastructure. The Mapflows.ai API, which is a deep learning model was used to extract the Nagpur city plan area as shown Figure 3(a). Over 1.5 million buildings were identified in all capturing 393.5 km2 of rooftops (Figure 3(a)) using high resolution satellite images with a processing time of 800 minutes. Classification of built-up density is taken in grid (100m x 100m) as shown in Figure 11(b). Figure 3(b) shows the magnified view of building footprints at Shivaji Nagar, Nagpur.

<img width="783" alt="Screenshot 2025-02-02 at 12 49 22 PM" src="https://github.com/user-attachments/assets/7ae4738e-3824-410d-8c15-cce32caa9179" />

3. Population Density:
  
Demography is an aspect of science that examines population increase, which is crucial for predicting the likelihood of earthquakes. Areas with a higher density of people are typically more vulnerable during intense earth tremors. The population density per square kilometer at the ward level was calculated using data from the 2011 Indian census. As shown in Figure 11(c), the ward data was compiled into a consistent grid of 100m using QGIS' "join attribute by nearest" plugin.

4. Building Age:

From the LULC categorization of the Landsat satellite dataset for the years 1993, 2002, 2016, and 2022, the building age is captured using USGS Earth Explorer as shown in Figure 4. For classification supervised machine-learning technique is used with the maximum likelihood model. Landsat datasets of 30m spatial resolution are used. To map the pixels (built-up changes) to the grid (100m X 100m), join attribute by nearest is used. Because of the age of the building, areas highlighted in red as shown in Figure 11(d) are considered to be at high risk.

<img width="722" alt="Screenshot 2025-02-02 at 12 53 13 PM" src="https://github.com/user-attachments/assets/5be0e26a-b648-4811-bc66-5d7dfe345052" />

5. Tree Density:

Low-income neighborhoods lack green spaces due to irregularly shaped and densely populated housing, whereas well developed areas contain gardens and extensive green spaces. The normalized difference vegetation index (NDVI) is calculated using Equation 1. Near-infrared (NIR) light is reflected by healthy green vegetation, while red light (RED) is absorbed. As shown in Figure 6(a), the NDVI calculation uses the Landsat 8 bands, with values ranging from -1 to +1, magnified view shown in Figure 6(b). Values greater than 0.2 are classified as green areas and the density of points is classified and mapped to the grid (Figure 11(e)).

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;"NDVI= "  (NIR-RED)/(NIR+RED)

<img width="766" alt="Screenshot 2025-02-02 at 12 55 56 PM" src="https://github.com/user-attachments/assets/3e60e7d6-2df5-4267-8c03-53da7d1d6b31" />

6. Important Structures:
   
Public spaces including hospitals, restaurants, movie theatres, and tourist attractions represent a substantial risk of earthquake victims causing casualty or getting injured. As seen in Figure 7(a), the quick OSM plugin is able to identify these locations using Google Maps. In Nagpur city, areas like Ramdespeth (Figure 7(b)) and Dhantoli are known for large number of hospitals and good medical facilities. All of the points are combined and categorized as indicated in Figure 11(f).

<img width="753" alt="Screenshot 2025-02-02 at 12 56 08 PM" src="https://github.com/user-attachments/assets/7a6e1608-c26d-4f9c-ac8e-ef133b0e9076" />

Extraction of Feature Importance:

For predictive modelling, feature importance rates the relevance of each individual feature. To assess feature importance, machine learning models like decision trees, random forests, and neural networks as well as statistical techniques like the analytical hierarchy process are used. Six columns (features) and 24616 rows (100m grids) make up our dataset.

1. Random Forest (RF) classifier: 

In Random Forest, the "forest" is a group of decision trees, each of which contributes to the final prediction. The classification is done by combining the predictions of all of the decision trees in the forest, each of which is trained on a random subset of the training data.

The set of six features (Street intersection density, Built-up density, Population Density, Building age, Tree density and important structure) serves as the input to the RF classifier. In order to evaluate each combination described rather than choosing samples at random, Grid-SearchCV is used for hyper-parameter (user-defined parameters that affect training and behavior of the model) training. Table 1 contains hyper-parameter information.

<img width="867" alt="Screenshot 2025-02-02 at 1 03 09 PM" src="https://github.com/user-attachments/assets/d18add30-c0d6-4259-b92c-df229cfe1bae" />


Gini impurity is employed to measure feature importance to categorize, assess, and track feature reduction with 74% testing accuracy. Figure 9(a) shows comparison of the predicted and actual labels for seismic risk zones. Feature importance through RF classifier is shown in Table 3 and are processed further to predict exposure for seismic risk (Figure 11(h)).

2. Neural Networks (NN):
  
These networks are the computational models that excel at learning and recognizing intricate patterns and relationships in data. They are trained using a method known as backpropagation and are made up of interconnected artificial neurons arranged in layers. They use training data to develop and enhance their accuracy. Gradient adjustments and automated learning rate adjustments improve training.

Here, the convergence speed is increased by using Nesterov accelerated gradients. The model in Table 2 has been tested with an accuracy of 72.95% after 250 training epochs.A square matrix representing rows with actual/true class and columns with predicted is shown in Figure 9(b). To create the exposure maps for seismic risk (Figure 11(i)), SHAP (Shapley Additive exPlanations) values are used to categorize importance as stated in Table 3.

<img width="851" alt="Screenshot 2025-02-02 at 1 03 29 PM" src="https://github.com/user-attachments/assets/5e04779f-0dec-4493-ac74-1d843fe376b6" />

3. Analytical Hierarchy Process (AHP):
  
By following AHP, which was introduced by Saaty (1980), feature importance is determined. This is a multi-criteria analysis method that assigns appropriate weights to the levels that have been built. This method enables the user to compare two criteria at once by providing a score value ranging from 1 to 9 with their appropriate priority from equal to extreme importance. Hence, there will be nC2 comparisons made where n is the number of parameters. Hence, 6C2 i.e., 15 comparisons made are shown in Figure 10. 

<img width="825" alt="Screenshot 2025-02-02 at 1 04 23 PM" src="https://github.com/user-attachments/assets/76557ba2-e0e0-4e72-a965-6d0f642a66af" />


Comparison of feature Importance through RF, NN and AHP

In maps (Figure 11 (h) and Figure 11 (i)), 1 indicates no risk, 2 as very low risk, 3 as low risk, 4 as moderate risk and 5 as high risk. NN states that no-risk, very low-risk, and moderate- risk zones are classified with good results (above 52 %) as compared to low-risk, and high-risk (low as 1.25%) zones. RF classifier concludes that no-risk, very low-risk, and moderate-risk zones were identified with results (above 62%). 
Higher AHP rankings (shown in Figure. 11 (g)) indicate older structures, higher population densities, higher street intersection densities, lower tree densities, and more important structures.


<img width="833" alt="Screenshot 2025-02-02 at 1 05 07 PM" src="https://github.com/user-attachments/assets/829f8177-7078-4587-b76b-bef57d6ca09e" />

<img width="867" alt="Screenshot 2025-02-02 at 1 07 05 PM" src="https://github.com/user-attachments/assets/d2212370-570b-4cd2-96a3-fda1756bbb54" />

<img width="839" alt="Screenshot 2025-02-02 at 1 07 19 PM" src="https://github.com/user-attachments/assets/8e68eca0-d8b9-4629-8f66-ce24d8f2288a" />


