# Bot_SearchFAQ
<h1>Search Your Knowledge Base</h1>

In this recipe, we learn how to search our Knowledge base and return those results to the customer.
Knowledge article search is a popular use case for chatbots. With Apex actions and dynamic menus, we can come up with a basic solution.
The bot asks for a keyword with a <b>Question</b> element, passes the keyword to an Apex action, and then the Apex method performs a SOSL search to return a list of articles. 
If the customer wants more detail, you can merge article content in the response.

While that’s a basic design that serves as a starting point, consider the user experience.
Given the limited real estate in a chat window, a typical user interface shows only a snippet of an article. If a customer wants more, they can click a link and open the article in a browser window. 

<b>A few things to note:</b>

- The SearchFAQ() method first executes a SOSL search with filters on PublishStatus, Language and IsVisibleInPkb. If you use data categories to filter article visibility in the community, include the WITH DATA CATEGORY clause as well. The goal is that only public articles are included in the search result. The method then loops through the search results. For each article, it calls the summarizeArticleForBot() method and concatenates the summaries. The results are returned in one long text variable.

- The goal for the summarizeArticleForBot() method is to create the article title and a link to open the article.

<h3>1. Create an invocable Apex method to search articles. APEX Class Bot_SearchFAQ </h3>
<h3>2. Install LWC pack to have the hyperlink feature: <a href="https://appexchange.salesforce.com/listingDetail?listingId=a0N3A00000FoirpUAB&tab=e">Visit App Exchange</a></h3>
<h3>3. Update the permission set to enable Apex classes and Salesforce object visibility.
Knowledge has a few more access control configurations, such as view knowledge article or data category visibilities. Make sure those are set properly in the permission set too.</h3>
<h3>4. Call the action from the "Search FAQ" dialog in the bot.</h3>
- Create two Text variables: Search_Variable and Search_Result. They will be used in the “Search FAQ” dialog. Let’s have our dialog perform the following steps:

a. Clear the Search_Variable in case the customer has already been through this flow before.
In our “Search FAQ” dialog, we always want to clear the variable first so that the customer can search with a new keyword each time:

![image](https://user-images.githubusercontent.com/37139091/217377231-948e576d-3115-43d5-ae1d-e1c7f263cfc3.png)

b. Ask the customer what they want to know:

![image](https://user-images.githubusercontent.com/37139091/217371186-c9b9c8aa-2145-433e-9d39-dd28d4a2cdeb.png)

c. Call our Apex class: 

![image](https://user-images.githubusercontent.com/37139091/217371571-a83608c7-61be-4f45-a47d-377cecdb568b.png)

![image](https://user-images.githubusercontent.com/37139091/217371725-18cd04e7-a15e-4abc-83d3-440924e44ca1.png)






