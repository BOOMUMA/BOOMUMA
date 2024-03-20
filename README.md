## Introduction
  Listening to music is often seen as entertainment, but it is also commonly regarded as beneficial for mental and emotional well-being. Listening to music can help people relax and aid in sleep, while upbeat music can provide motivation. Music is even considered a therapeutic tool for psychological treatment. Report suggests that music can help combat depression, anxiety, and a range of other mental health issues[1]. 
  However, everyone's musical preferences are greatly different, everyone have their own tastes. Do all types of music have a positive impact on their audience's mental health? Could there be music genres that even have negative effects? What kind of music listening frequency (i.e. how long music should be listened to every day) is effective for mental health? This data analysis aims to explore these questions.

## Data review
  I have found a dataset on Kaggle consisting of survey results collected by individuals through Google Form, which includes responses from 736 participants of different age groups and music genre preferences. It comprises 33 variables, including the severity of four common mental health issues (anxiety, depression, insomnia, OCD) and the frequency of listening to specific music genres. Interpretation of some of the variables are followings:
  
 Hours per day: Number of hours the respondent listens to music per day.
 
 While working: Does the respondent listen to music while studying/working?
 
 Fav genre: Respondent's favorite or top genre.
 
 Music effects: Does music improve/worsen respondent's mental health conditions?
 
 Anxiety, Depression, Insomnia, and OCD: Self-reported mental health problem, on a scale of 0-10,
- 0 means I do not experience this.
- 10 means I experience this regularly, constantly/or to an extreme.

## Data preprocessing
  The dataset consists of 33 rows and 736 columns. Among the 33 rows, there are 7 columns with float data type and 26 columns with object data type. The variables "Hours per day" with a maximum value of "24" and "BPM" with a maximum value of "999999999.0" indicate the presence of outliers in these two variables. Null values are also present throughout the dataset. The presence of outliers and null values can significantly impact my analysis results. Therefore, I had to remove null values and outliers by using the Pandas DataFrame methods. Additionally, I excluded two unnecessary columns, 'Timestamp' and 'Permissions,' and generated a new CSV file for further data analysis.

  To explore the relationship between the frequency of listening to different music genres and other variables, I converted the variables related to frequency from object type to numerical data. I replaced the categories "Never, Rarely, Sometimes, Very frequently" with numerical values "1, 2, 3, 4" to represent their representative frequencies for future processing, allowing for easier analysis.

## Data visualization & Key findings
  I would like to investigate the connection between people's favorite music genres and their views on four mental health issues. One effective method for this exploration is correlation analysis, which is a mathematical tool used to measure the strength and direction of the relationship between two continuous numerical variables. The Pearson correlation coefficient is the most commonly used measure of correlation, ranging from -1 to 1. The formula for calculating the Pearson correlation coefficient is as follows[2]:
![Pearson_correlation_coefficient](https://github.com/BOOMUMA/BOOMUMA/blob/main/Correlation%20coefficient.png)

  A positive coefficient indicates a positive linear relationship between two variables, suggesting that as one variable increases, the other variable also tends to increase. Conversely, a negative coefficient indicates a negative linear relationship, meaning that as one variable increases, the other variable tends to decrease. A coefficient of 0 signifies no linear relationship between the two variables. The size of the coefficient can be interpreted as follows:
[![interpret_r.png](https://github.com/BOOMUMA/BOOMUMA/blob/main/interpret_r.png)](https://github.com/BOOMUMA/BOOMUMA/blob/main/interpret_r.png)


  However, the variable "Fav genre" is categorical data (object type) rather than numerical. Fortunately, the dataset includes information about the frequency of listening to each music genre, which provides a powerful description of individual music preferences. During the data preprocessing stage, I transformed this variable from categorical to numerical type. Therefore, I directly selected all the numerical data from the dataset to generate a correlation matrix heatmap and I marked coefficients exceeding 0.5 or below -0.5 on the heatmap.

  The heatmap reveals a strong positive correlation coefficient of 0.78 between the frequency of listening to Hip-hop music and the frequency of listening to Rap music. This indicates that individuals who listen to Hip-hop frequently are likely to have a high frequency of listening to Rap music as well. Additionally, there is a moderate positive correlation between the frequency of listening to Hip-hop music and the frequency of listening to R&B music, with a coefficient of 0.53. Similarly, there is a moderate positive correlation between the frequency of listening to R&B music and the frequency of listening to Rap music, with a coefficient of 0.51.

  Furthermore, the correlation coefficient between Anxiety and Depression is 0.52, indicating a moderate positive correlation. This suggests a significant overlap between these two mental health issues in individuals. Individuals with a high score in anxiety are likely to also have a high score in depression.

  The age of the survey respondents in the dataset ranges from 10 to 89 years old, with the majority falling within the 10-40 age range. This distribution is reasonable because the survey questionnaire was distributed through Google Forms, targeting digital users. Therefore, it is expected that most respondents would be concentrated in the younger age groups.
  
  According to the dataset, 63.8% of the respondents use Spotify as their streaming service, while 8.8% of the respondents do not use any similar platforms. Let's generate the age distribution of users across different streaming service platforms. Except for Pandora, which has 50% of its users concentrated in the 30-60 age range, with a median age between 50 and 60, the users of other streaming service platforms have a median age between 20 and 30. Among the respondents, Spotify and Apple Music users are the youngest, with 50% of their users being around 20 years old. There are a few respondents in the 70-80 age range, which appear as outliers in the box plot. Some of them use Spotify, while others do not use any streaming service.

  Now let's explore the differences in music genre preferences among different age groups. Fans of Rock, Classical, and Pop music span across various age ranges, attracting different age groups. Genres like Kpop and Rap, which are popular among younger individuals, tend to have a concentrated fan base in the 10-30 age range.

  From the distribution bar chart of favorite genre, we can observe that Rock, Pop, and Metal belong to mainstream popular music, while Latin and Gospel fall into the niche music category.

 Approximately 76% of the respondents believe that music has a positive impact on their mental health. They feel that listening to music improves their mental health conditions, which confirms the statement I mentioned in the introduction that music can help combat mental health issues.
  
  Looking at the stacked bar chart of Favorite genre and Music effects, a majority of individuals thought listening to music was beneficial for improving their mental health conditions. However, individuals who reported a decline in mental health condition are fans of Rock, Video game music, Pop, Rap, and Classical music, with a significant concentration among respondents who favor Rock and Video game music. It's worth noting that among those who selected Video game music as their favorite genre, around 45% believe that music has no effect on their mental health, and nearly 12% think it has a negative impact.

 Listeners of Latin music have the highest average scores in Anxiety. Lofi music has the highest average scores in Depression, Insomnia, and OCD. (But since the number of respondents who chose Latin or Lofi as their favorite music genres is relatively small, it may not be representative.)
Fans of Hip-hop music also show higher-than-average scores in Depression and OCD.

 Does the frequency of daily music listening affect the effectiveness of music in improving mental health issues? There may be a certain relationship. In the box plot of "Hours per day" and "Music effects" it can be observed that respondents who believe music has a positive effect on their mental health have a median frequency of around 3 hours of daily music listening, which is approximately 1 hour more than those who reported "No effect" or "Even worsen."

 However, when observing the line charts of "Hours per day" and the four mental health scores, especially Anxiety and OCD, as the daily music listening frequency increases, the scores of mental health issues also tend to increase. Among those who listen to music for an average of 8 hours or more per day, they exhibit extremely high scores across all four mental health issues.

 By comparing the variable "While working" with the four mental health scores, I was surprised that individuals who listen to music while working tend to have more severe mental health conditions compared to those who do not listen to music while working.

## Conclusion
 Music has an overall positive impact on improving mental health issues and can be considered a therapeutic tool suitable for most individuals. However, among all music genres, Video game music shows the weakest effect in improving mental health problems and even has the highest likelihood of exacerbating them. There is no strong correlation between music genre preferences and mental health issues. Each genre's audience exhibits different performances in various mental health problems. However, I discovered that people who enjoy one music genre may also enjoy another genre (e.g., Hiphop and Rap, Hiphop and R&B, Rap and R&B), indicating a possible crossover between these pairs of genres' audiences.
 
 Regarding the frequency of listening to music and its impact on mental health issues, the frequency of daily music listening plays a significant role. Higher frequency has a greater effect on improving mental health problems. Additionally, there were some unexpected findings. Individuals with more severe mental health problems tend to rely more on listening to music. This is evident in their longer daily music listening times and the fact that they also listen to music while working.


[1]https://www.ncbi.nlm.nih.gov/pmc/articles/PMC8566759/

[2]https://en.wikipedia.org/wiki/Pearson_correlation_coefficient

[3]https://www.ncbi.nlm.nih.gov/pmc/articles/PMC3576830/
