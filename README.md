# MCN_Channel_Dashboard
Analyze a number of MCN partner channels in one dashboard.

## Background
MCNs or multi-channel networks are groups of YouTube channels that partner with music rightsholders to upload and promote music. Popular MCNs include the District (and it's SONY Music joint venture FYEO), COLORS, and NATIONS, which have all partnered with the major US record labels (Sony Music, Universal Music, and Warner Music). These networks can range from several to hundreds of partner channels, with these partner channels contributing millions of subscribers and billions of streams to their respective MCNs and rightsholders.

For this project, I converted an internal list of Sony Music's MCN partner channels into a dashboard to better interact with and understand the value and impact of our MCN support.

## Requirements and Technology
* Python & Pandas
* Google Sheets
* Google Co-lab
* Google Looker Data Studio

## 1. Dataset
The initial channel list consisted of data pulled from Tubular reporting and direct reports from MCN partner channels. The list of columns and their datatype can be seen below.

![Channel_List_Redacted.jpg](https://github.com/heartgears/MCN_Channel_Dashboard/blob/main/Channel_List_Redacted.jpg)
![Channel_List_Redacted.jpg](https://github.com/heartgears/MCN_Channel_Dashboard/blob/main/Columns_List.png)

Some columns – in particular genres, moods, languages, and top markets - included multiple values in each cell, separated by commas. These multiple-value cells and columns made filtering data tedious and non-intuitive. The dashboard aims to solve this particular problem, as well as the overwhelming number of channels and rows in a spreadsheet format into something cleaner and more interactive for label teams to use for guiding their MCN strategy.

## 2. Data Preparation and Manipulation
The channel list was directly imported into a Google co-lab Python notebook via Google Sheets. The four aforementioned columns above (Genres, Moods, Languages and Top Markets) were used to create four separate data frames. In Google Sheets, a separate sheet was used to split these columns on commas, resulting in a sheet like the below:

These sheets were then converted into separate data frames and melted using pd.melt, resulting in each Channel ID receiving at least one row of data. For example, if a channel had multiple genres listed, it would receive a row in the data frame for each genre. 

A separate data frame was created for the rest of the channel list data, minus the aforementioned columns above. This data frame was then merged one at a time with each of these other data frames with a left join. The final step of data preperation was to apply a mask for the numeric data columns (YouTube Views, Subscribers, etc), so that the dashboard could sum the results for a channel and return the correct subscriber count. I.e., if this step was not performed, a channel could have three genres and 100 subscribers and the dashboard would return the subscribers as a metric sum of 300. Additionally, with this step taken, if multiple channels are selected, the sum function returns the correct result.

## 3. Dashboard
The final data frame was then re-uploaded to the same Google Sheet for Google's Looker Data studio to create a dashboard. The final dashboard can be seen below.

Due to the confidentiality of the data, the final dashboard is not linked here. 
