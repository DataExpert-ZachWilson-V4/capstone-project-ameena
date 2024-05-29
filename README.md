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

1. Number of users onboarded

FastAPI:

We can build an API that will allow our Data Scientists to analyze the data and make predictions or recomendations to the product.
