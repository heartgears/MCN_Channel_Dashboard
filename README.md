# MCN_Channel_Dashboard
Analyze numerous MCN partner channels in one dashboard.

## Background
MCNs, or multi-channel networks, are groups of YouTube channels that partner with music rightsholders to upload and promote music. Popular MCNs include the District (and its SONY Music joint venture FYEO), COLORS, and NATIONS, which have all partnered with the major US record labels (Sony Music, Universal Music, and Warner Music). These networks can range from several to hundreds of partner channels, with these partner channels contributing millions of subscribers and billions of streams to their respective MCNs and rightsholders.

For this project, I converted an internal list of Sony Music's MCN partner channels into a dashboard to better interact with and understand our MCN networks.

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
The channel list was directly imported into a Google co-lab Python notebook via Google Sheets. The four aforementioned columns above (Genres, Moods, Languages and Top Markets) were manipulated into four separate data frames by splitting. This data was then converted into separate data frames using pd.melt, resulting in each Channel ID receiving at least one row of data. For example, a channel with multiple genres listed would receive a row in the data frame for each genre. 

![Genre_df_Redacted.jpg](https://github.com/heartgears/MCN_Channel_Dashboard/blob/main/Genre_df_Redacted.jpg)

A separate data frame was created for the rest of the channel list data, minus the abovementioned columns. This data frame was then merged with these other data frames on a left join to create a new dataset for the best dashboard viewing.

## 3. Dashboard
The final data frame was then re-uploaded to the same Google Sheet for Google's Looker Data studio to create a dashboard with multiple views. Due to the confidentiality of the data, the final dashboard is not linked here, and some data has been redacted.

### 3a. MCN Partner View

<img src="https://github.com/heartgears/MCN_Channel_Dashboard/blob/main/3a_MCN_Overview.jpg" width=50% height=50%>

The first page of the dashboard is primarily for identifying target channels within certain genre, language, and mood spaces. A user can, for example, filter for Spanish-language Pop channels with over 100,000 subscribers. The data returned will show all channels meeting this criteria and sort them by the channels with the most Sony content uploads. This allows teams to fine-tune their MCN outreach strategies and better understand the level of support they could expect to receive on certain musical products.

### 3b. Channel Drilldowns

![3b_Channel_Drilldown.jpg](https://github.com/heartgears/MCN_Channel_Dashboard/blob/main/3b_Channel_Drilldown.jpg)

The second page of the dashboard provides insight into certain channels' data. Users can see the size of a channel, how frequently it uploads, and Sony's market share by number of uploads. They can additionally filter by similar criteria found on page one.

### 3c. Interaction Tracker

![3c_Interactions.jpg](https://github.com/heartgears/MCN_Channel_Dashboard/blob/main/3c_Interactions.jpg)

The third and final page explores the interaction tracker data provided by District & FYEO. In addition to seeing the raw interaction tracker data, users can filter for their label or territory's content only, in addition to artist and song performance data. The charts on the right show trends in their support broken out by tier of artist, as well as seeing the Top 10 songs and channel supporters of particular content.



