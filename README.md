# ACLU Child Separation Project
### About: 

For this project, I implemented data analysis using R. I used the libraries readr and dplyr which helped me to build the project. I analyze the data of ACLU to gain a better undstanding and insight of the situation at the border regarding the family separtation policy enacted in 2018.
 
### Note:

I used the .csv file provided by the American Civil Liberties Union (ACLU) which provided the data related to the immigrant children separated from their families at the border of Mexico.

ACLU has noted concerns about the comprehensiveness and accuracy of the government's data. Despite this, working with the data available can still yield valuable insights. 

### Results

**Original Data**

<img width="638" alt="Screen Shot 2021-09-23 at 4 44 59 PM" src="https://user-images.githubusercontent.com/89553126/134590606-fe7f6c90-77f9-4a2e-ac6d-3dcd1776e0de.png">

First, I cleand up the data. The data had repeating information. In order to make things easier to analyze, I took out *addr* column from the data.
 
 <img width="141" alt="Screen Shot 2021-09-23 at 4 45 19 PM" src="https://user-images.githubusercontent.com/89553126/134590657-29e2d516-4855-4c7f-b7cb-3826e3404f91.png">
 
Afterwards, I renamed the columns to make them easier to understand.

<img width="635" alt="Screen Shot 2021-09-23 at 4 46 35 PM" src="https://user-images.githubusercontent.com/89553126/134590680-7d744b59-d92b-4ede-92f8-ec534740c3dd.png">

<img width="635" alt="Screen Shot 2021-09-23 at 4 46 49 PM" src="https://user-images.githubusercontent.com/89553126/134590721-9b787377-98be-427a-bea7-115fc54b402f.png">
 
Now I am interesed in getting an understanding of how far some of the children have been moved from the United States-Mexico border. Since the latitude represents how far north and south a location is, I decided to measure how far each detention center is from the border in terms of latitude change. 

I know that the southernmost point of the border lies at a latitude of **25.83**. Therefore, I created a variable called *border_latitude* with the value **25.83** that I will use to find the *lat_change_border* which I will add to our existing data.

<img width="427" alt="Screen Shot 2021-09-23 at 4 51 20 PM" src="https://user-images.githubusercontent.com/89553126/134590751-51770248-598d-4f71-bb1a-7f5355c8e697.png">
 
<img width="813" alt="Screen Shot 2021-09-23 at 4 51 33 PM" src="https://user-images.githubusercontent.com/89553126/134590768-0d1f097e-1d6b-4bcd-81bd-41b21e36f433.png">


Now I can arrange the borders from furthest to closest so in this case, greater than 15° latitude change from the border.

<img width="250" alt="Screen Shot 2021-09-23 at 4 52 48 PM" src="https://user-images.githubusercontent.com/89553126/134590802-c82cf7e5-3ed8-4395-911f-09e4d1b47ff5.png">

<img width="813" alt="Screen Shot 2021-09-23 at 4 53 06 PM" src="https://user-images.githubusercontent.com/89553126/134590826-b9c3c8c5-2a93-4efb-b371-5bd889a5ceda.png">

As well as place the latitude change in descending order.

<img width="268" alt="Screen Shot 2021-09-23 at 4 54 23 PM" src="https://user-images.githubusercontent.com/89553126/134590868-d17d9667-77ed-4674-9477-253a3bb7cfcb.png">

<img width="824" alt="Screen Shot 2021-09-23 at 4 54 36 PM" src="https://user-images.githubusercontent.com/89553126/134590886-3dcd40ba-fe52-463d-9142-dce023303c57.png">
 
As someone who wants to stay informed, I want to also identify the detention centers that hold the largest number of children.

<img width="254" alt="Screen Shot 2021-09-23 at 5 01 02 PM" src="https://user-images.githubusercontent.com/89553126/134590908-16456ac8-7d62-4378-901f-c2d017ce4aa5.png">

<img width="816" alt="Screen Shot 2021-09-23 at 5 01 11 PM" src="https://user-images.githubusercontent.com/89553126/134590941-9184078f-40ab-4d10-8397-87ad4abcea3d.png">
 
According to the data, children have been separated from their parents to detention centers located in many different states. I am interested in the state I have visited before, Texas. I will use the variable *chosen_state* and filter the data to just see that set.

After this I will order the rows of *chosen_state_separations* by *number_children* in descending order.

<img width="289" alt="Screen Shot 2021-09-23 at 5 06 51 PM" src="https://user-images.githubusercontent.com/89553126/134591026-fe208164-0f33-488a-abc8-e1f113aa1e43.png">

<img width="814" alt="Screen Shot 2021-09-23 at 5 06 58 PM" src="https://user-images.githubusercontent.com/89553126/134591039-9974f3c6-4789-4f02-b2eb-cae37f0cdb09.png">
 
You may have known about the separation policy that existed at the US-Mexico border in 2018 before, or you may have just learned about it today. Either way, you have seen that working with data and performing an analysis is not just a manipulation of numbers in a program. It’s an opportunity to understand our world, and bring to light the stories and lives of the people living in it.
 
