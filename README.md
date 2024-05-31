[![Review Assignment Due Date](https://classroom.github.com/assets/deadline-readme-button-24ddc0f5d75046c5622901739e7c5dd533143b0c8e959d652212380cedb1ea36.svg)](https://classroom.github.com/a/1lXY_Wlg)

# TechGist 
 
A social platform where you get summary of all the technical reading you want to do from your subscriptions , articles , linkedin , books , youtube transcripts, audio and pod cast ( audio to text convertion) 

Problem at Hand:

Currently, we face the challenge of logging into multiple platforms to satisfy our technical appetite. Storing and managing these articles across different sources is cumbersome and inefficient. This fragmented approach results in wasted time and missed valuable insights.

Proposed Solution:

To address this issue, we propose the development of a comprehensive social platform designed to streamline the process of accessing and managing technical content. Our platform will offer the following features:

1. Automated Content Aggregation: Users can configure their settings to automatically fetch and summarize content from preferred authors on LinkedIn, Medium, Substack, and other blogging platforms. By simply entering their LinkedIn details and selecting the bloggers they want to follow, the platform will provide a concise gist of the latest posts from these authors.
   
2. Centralized Article Management: The platform will also enable users to store links to their favorite articles in one convenient location. This central repository will make it easy to organize, access, and revisit valuable content without the need to navigate through multiple websites.

   
Benefits:

* Time Efficiency: Users will no longer need to log into multiple accounts and manually search for updates. The platform will deliver all relevant content summaries directly to them.
* Enhanced Organization: With a centralized storage system, users can keep all their preferred articles and links neatly organized, improving their ability to reference and utilize this information.
* Personalized Experience: The ability to follow specific authors and configure settings ensures that users receive content tailored to their interests and needs.
We believe this solution will significantly enhance the way technical professionals access and manage their reading material, leading to better knowledge retention and more efficient use of time.
We look forward to discussing this proposal further and exploring how we can bring this vision to life.

Conceptual Data Model :


Creating a conceptual data model involves defining the high-level entities, their attributes, and relationships that will be used in the system. Here's a conceptual data model for the proposed social platform for aggregating and summarizing technical content:


<pre>

+--------------------+                   +-------------------+
|        User        |                   |       Author      |
+--------------------+                   +-------------------+
| UserID (PK)        |                   | AuthorID (PK)     |
| Name               |                   | Name              |
| Email              |                   | ProfileURL        |
| Password           |                   | Platform          |
| LinkedInProfile    |                   +-------------------+
| MediumProfile      |                            |
| SubstackProfile    |                            |
| OtherProfiles      |                            |
+--------------------+                            |
       |                                         |
       | 1                                       | M
       |                                         |
+---------------------------+           +--------------------------+
|   UserFavoriteAuthors     |           |         Article          |
+---------------------------+           +--------------------------+
| FavoriteID (PK)           |           | ArticleID (PK)           |
| UserID (FK)               |-----------| AuthorID (FK)            |
| AuthorID (FK)             |           | Title                    |
| DateAdded                 |           | Content                  |
+---------------------------+           | Summary                  |
       |                                 | PublishDate              |
       | 1                               | URL                      |
       |                                 +--------------------------+
       |
       |
       | 1
       |
       |
       | M
+---------------------------+
|   UserFavoriteArticles    |
+---------------------------+
| FavoriteID (PK)           |
| UserID (FK)               |
| ArticleID (FK)            |
| DateAdded                 |
+---------------------------+
       |
       | 1
       |
       | M
+---------------------------+
| UserPlatformSettings      |
+---------------------------+
| SettingsID (PK)           |
| UserID (FK)               |
| PlatformID (FK)           |
| ProfileURL                |
| FollowAuthors (List)      |
+---------------------------+
       |
       | 1
       |
       | M
+---------------------------+
|       UserTimeline        |
+---------------------------+
| TimelineID (PK)           |
| UserID (FK)               |
| ActivityType              |
| ActivityDate              |
| ActivityDetails           |
+---------------------------+

</pre>

Entities and Relationships
1. User
    * Attributes:
        * UserID (Primary Key)
        * Name
        * Email
        * Password
        * LinkedInProfile
        * MediumProfile
        * SubstackProfile
        * OtherProfiles
2. Author
    * Attributes:
        * AuthorID (Primary Key)
        * Name
        * ProfileURL
        * Platform (LinkedIn, Medium, Substack, etc.)
3. Article
    * Attributes:
        * ArticleID (Primary Key)
        * Title
        * Content
        * Summary
        * PublishDate
        * URL
        * AuthorID (Foreign Key)
          
4. UserFavoriteAuthors
   
    * Attributes:
        * FavoriteID (Primary Key)
        * UserID (Foreign Key)
        * AuthorID (Foreign Key)
        * DateAdded
          
5. UserFavoriteArticles
   
    * Attributes:
        * FavoriteID (Primary Key)
        * UserID (Foreign Key)
        * ArticleID (Foreign Key)
        * DateAdded
          
6. UserPlatformSettings
    * Attributes:
        * SettingsID (Primary Key)
        * UserID (Foreign Key)
        * PlatformID (Foreign Key)
        * ProfileURL
        * FollowAuthors (List of AuthorIDs)
     
7. UserTimeline

Attributes:
TimelineID (Primary Key)
UserID (Foreign Key)
ActivityType (e.g., 'Followed Author', 'Read Article', 'Saved Article')
ActivityDate
ActivityDetails
          
Relationships

* User has many UserFavorite
* User has many UserPlatformSettings
* UserFavorite links User and Article
* Article is written by Author
* Article belongs to Platform
* UserPlatformSettings links User and Platform

Analytics dashboard :

1. Active Users: The number of users actively using the TechGist service within a specific time frame, typically measured monthly (MAU - Monthly Active Users).
2. Saved Items: The total number of articles, videos, and other content saved by users.
3. Engagement Metrics: This includes metrics like the average time spent reading or watching saved content, the frequency of item saves, and the number of items read or viewed per user.
4. Retention Rates: The percentage of users who continue to use TechGist over time, indicating user loyalty and satisfaction.
5. New User Acquisition: The rate at which new users are signing up for TechGist, often measured through marketing efforts, referral programs, and other user acquisition strategies.
6. Customer Satisfaction and NPS (Net Promoter Score): Measures of how satisfied users are with TechGist and how likely they are to recommend it to others (Cascade Strategy) (Oberlo) .
7. Revenue Metrics: For TechGist’s premium services, this includes metrics such as subscription rates, revenue from premium users, and overall revenue growth.
8. Content Categorization Efficiency: Metrics that track how effectively TechGist’s algorithms categorize and recommend content to users, enhancing the user experience.
9. User Demographics: Data on the age, location, and interests of TechGist’s user base to tailor content and marketing strategies more effectively.
10. Churn Rate: The percentage of users who stop using TechGist over a given period, providing insights into user retention challenges (Whale) .


Tracking these metrics helps Pocket continuously improve its service, ensuring it meets user needs and stays competitive in the market.


If time permits then would love to build an API using FASTAPI

This API will allow our Data Scientists to analyze the data and make predictions or recomendations to the product.
