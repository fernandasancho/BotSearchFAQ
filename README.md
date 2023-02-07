# Bot_SearchFAQ
<h1>Search Your Knowledge Base</h1>

In this recipe, we learn how to search our Knowledge base and return those results to the customer.
Knowledge article search is a popular use case for chatbots. With Apex actions and dynamic menus, we can come up with a basic solution.
The bot asks for a keyword with a <b>Question</b> element, passes the keyword to an Apex action, and then the Apex method performs a SOSL search to return a list of articles. 
If the customer wants more detail, you can merge article content in the response.

While that’s a basic design that serves as a starting point, consider the user experience.
Given the limited real estate in a chat window, a typical user interface shows only a snippet of an article. If a customer wants more, they can click a link and open the article in a browser window. 

<h3>1. Create an invocable Apex method to search articles. APEX Class Bot_SearchFAQ </h3>

<b>A few things to note:</b>

- The SearchFAQ() method first executes a SOSL search with filters on PublishStatus, Language and IsVisibleInPkb. If you use data categories to filter article visibility in the community, include the WITH DATA CATEGORY clause as well. The goal is that only public articles are included in the search result. The method then loops through the search results. For each article, it calls the summarizeArticleForBot() method and concatenates the summaries. The results are returned in one long text variable.

- The goal for the summarizeArticleForBot() method is to create the article title and a link to open the article.
- Install LWC pack to have the hyperlink feature: <a href="https://appexchange.salesforce.com/listingDetail?listingId=a0N3A00000FoirpUAB&tab=e">Visit App Exchange</a>
