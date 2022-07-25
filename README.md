## Backgroud and Inspiration to project

This projects is a datacamp inspired project. A competition that I could not find a way to submit.
However, my inspiration to this project is from the need to practise clustering algorithm
and eventually build a dash application that runs locally and adjust certain kind of plots
and numbers based on the number of clusters.

### The background
You work for a medical device manufacturer in Switzerland. Your company manufactures 
orthopedic devices and sells them worldwide. 
The company sells directly to individual doctors who use 
them on rehabilitation and physical therapy patients.

Historically, the sales and customer support departments have grouped doctors by geography. 
However, the region is not a good predictor of the number of
purchases a doctor will make or their support needs.

Your team wants to use a data-centric approach to segmenting 
doctors to improve marketing, customer service, and product planning.

## 💾 The data

The company stores the information you need in the following four tables. Some of the fields are anonymized to comply with privacy regulations.

#### Doctors contains information on doctors. Each row represents one doctor.
- "DoctorID" - is a unique identifier for each doctor.
- "Region" - the current geographical region of the doctor.
- "Category" - the type of doctor, either 'Specialist' or 'General Practitioner.'
- "Rank" - is an internal ranking system. It is an ordered variable: The highest level is Ambassadors, followed by Titanium Plus, Titanium, Platinum Plus, Platinum, Gold Plus, Gold, Silver Plus, and the lowest level is Silver.
- "Incidence rate"  and "R rate" - relate to the amount of re-work each doctor generates.
- "Satisfaction" - measures doctors' satisfaction with the company.
- "Experience" - relates to the doctor's experience with the company.
- "Purchases" - purchases over the last year.

#### Orders contains details on orders. Each row represents one order; a doctor can place multiple orders.
- "DoctorID" - doctor id (matches the other tables).
- "OrderID" - order identifier.
- "OrderNum" - order number.
- "Conditions A through J" - map the different settings of the devices in each order. Each order goes to an individual patient.

#### Complaints collects information on doctor complaints.
- "DoctorID" - doctor id (matches the other tables).
- "Complaint Type" - the company's classification of the complaints.
- "Qty" - number of complaints per complaint type per doctor.

#### Instructions has information on whether the doctor includes special instructions on their orders.
- "DoctorID" - doctor id (matches the other tables).
- "Instructions" - 'Yes' when the doctor includes special instructions, 'No' when they do not.

The dataset can be found and downloaded from the data folder in this repo.

## Kprototype algorithm notebook

> The Kprototype algorithm notebook contains the EDA performed on the datasets
and the key insights obtained are as followw

- The histogram distribution of doctors purchases revealed to us that the most single
purchase occurred at around 4 - 6 purchases at once. And, although we expected that as the number of doctors increased in 
particular region, the average number of devices ordered would increase, but 
the barplot that showed the comparism did not display anything of such.

- When we compare the quanitity of devices purchased to the number of complaints made, we see that we have
seemingly a normal distribution where the maximum number of complaints received come from the median average number
of purchaes made.

> When we eventually go ahead to use the Kprototype algorithm which is relevant for both categorical and numerical 
features, we settled with using 4 clusters as a hyperparameter settings because of explicability and clarity of
each clusters. The clusters going from 0 to 3 have the following characteristics:

**Cluster 0**: They have most of their mean purchases around 10+ but their ambassador ranking personnel have a mean purchase of close to 30. However this particular cluster have the highest complaints among all other clusters, which is significantly higher than all other clusters. The ranking do no begin at silver, it rather begins at gold and goes all the way to Ambassaor, skipping Titanium plus.

**Cluster 1**: Although the scatterplot is hard to interpret, we do see that that Cluster 1 distributed accross difference experience range. However, above experience of 1, not many kind of clusters are found there and the cluster well dominates the field. The average purchase is below 10. It contains all ranks with the silver rank up to the gold rank clusterred around the same number of purchase, less than 10 and the higher ranks clustered around region of 10 or greater but less than 20.

**Cluster 2**: They have an average purchase greater than 40, with only titanium rank and ambassador rank present in the cluster. The titanium rank have their average purchases greater than 30 and the average purchases of their ambassadors greater than 40 and close to 50.

**Cluster 3**: It contains only three rank, Platinium Plus, Titanium and Ambassadors with average purchase of 30. However, they are spectacular for their high incidence rate among all other clusters. By looking at the scatterplot also, we discover that most of the clusters are above 20 and are the highest incidence rate in all of the data points in the scatterplot.

**Cluster 4**: Cluster 4 looks a lot like cluster 1 with very little difference. The difference is that cluster 4 has Titanium plus in the lower price region clustring with the likes of silver, dilver plus and lower ranks.


## Dash Application notebook

> This notebook contains the code that was used to develop a interactive dash application that generates plots for cluster classification
based on the number of hyperparameter given via the slider.

> This application includes a slider for changing the number of sliders and a radio button for switching between including 
the internal ranking features or not including the internal ranking system. Based on the input via the slider and radio button, 
the error metric is generated and some important plots for defining the number of clusters formed is automatically plotted.

Yours' Sincerely
deelight-del