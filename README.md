# ACLU Child Separation Project
### About: 

For this project, I implemented data analysis using R. I used the libraries readr and dplyr which helped me to build the project. I analyze the data of ACLU to gain a better undstanding and insight of the situation at the border regarding the family separtation policy enacted in 2018.
 
### Note:

I used the .csv file provided by the American Civil Liberties Union (ACLU) which provided the data related to the immigrant children separated from their families at the border of Mexico.

ACLU has noted concerns about the comprehensiveness and accuracy of the government's data. Despite this, working with the data available can still yield valuable insights. 

### Results:

**Original Data**

<img width="638" alt="Screen Shot 2021-09-23 at 4 44 59 PM" src="https://user-images.githubusercontent.com/89553126/134590606-fe7f6c90-77f9-4a2e-ac6d-3dcd1776e0de.png">

First, I cleand up the data. The data had repeating information. In order to make things easier to analyze, I took out *addr* column from the data.
 
```R
# select columns
aclu <- aclu %>%
select(-addr)
```
 
Afterwards, I renamed the columns to make them easier to understand.

```R
# rename columns
aclu <- aclu %>%
rename(city = program_city, state = program_state, number_children = n, longitude = lon, latitude = lat)
names(aclu)
```

<img width="635" alt="Screen Shot 2021-09-23 at 4 46 49 PM" src="https://user-images.githubusercontent.com/89553126/134590721-9b787377-98be-427a-bea7-115fc54b402f.png">
 
Now I am interesed in getting an understanding of how far some of the children have been moved from the United States-Mexico border. Since the latitude represents how far north and south a location is, I decided to measure how far each detention center is from the border in terms of latitude change. 

I know that the southernmost point of the border lies at a latitude of **25.83**. Therefore, I created a variable called *border_latitude* with the value **25.83** that I will use to find the *lat_change_border* which I will add to our existing data.

```R
# add column
border_latitude <- 25.83
aclu <- aclu %>%
mutate(lat_change_border = latitude - border_latitude)
head(aclu)
```
 
<img width="813" alt="Screen Shot 2021-09-23 at 4 51 33 PM" src="https://user-images.githubusercontent.com/89553126/134590768-0d1f097e-1d6b-4bcd-81bd-41b21e36f433.png">

Now I can arrange the borders from furthest to closest so in this case, greater than 15° latitude change from the border.

```R
# latitude change
 further_away <- aclu %>%
 filter(lat_change_border > 15)
head(further_away)
```

<img width="813" alt="Screen Shot 2021-09-23 at 4 53 06 PM" src="https://user-images.githubusercontent.com/89553126/134590826-b9c3c8c5-2a93-4efb-b371-5bd889a5ceda.png">

As well as place the latitude change in descending order.

```R
# number of children
further_away <- further_away %>%
arrange(desc(lat_change_border))
head(further_away)
```

<img width="824" alt="Screen Shot 2021-09-23 at 4 54 36 PM" src="https://user-images.githubusercontent.com/89553126/134590886-3dcd40ba-fe52-463d-9142-dce023303c57.png">
 
As someone who wants to stay informed, I want to also identify the detention centers that hold the largest number of children.

```R
# state analysis
ordered_by_children <- aclu %>%
arrange(desc(number_children))
head(ordered_by_children)
```

<img width="816" alt="Screen Shot 2021-09-23 at 5 01 11 PM" src="https://user-images.githubusercontent.com/89553126/134590941-9184078f-40ab-4d10-8397-87ad4abcea3d.png">
 
According to the data, children have been separated from their parents to detention centers located in many different states. I am interested in the state I have visited before, Texas. I will use the variable *chosen_state* and filter the data to just see that set.

After this I will order the rows of *chosen_state_separations* by *number_children* in descending order.

```R
# specific state
chosen_state <- 'TX'
chosen_state_separations <- aclu %>%
filter(state == chosen_state) %>%
arrange(desc(number_children))
 
head(chosen_state_separations)
```

<img width="814" alt="Screen Shot 2021-09-23 at 5 06 58 PM" src="https://user-images.githubusercontent.com/89553126/134591039-9974f3c6-4789-4f02-b2eb-cae37f0cdb09.png">
 
You may have known about the separation policy that existed at the US-Mexico border in 2018 before, or you may have just learned about it today. Either way, you have seen that working with data and performing an analysis is not just a manipulation of numbers in a program. It’s an opportunity to understand our world, and bring to light the stories and lives of the people living in it.
 
