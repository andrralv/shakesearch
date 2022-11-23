### Design

I followed mostly a front-end approach, but I did make some changes to the `main.go` file to handle the casing. The app can be found at `https://shakesearch-andrralv.herokuapp.com/`

When I first saw the raw ShakeSearch application and went ahead to try it, I noticed that the data returned from the network tab contained whitespace so that each piece of text is structured like a poem or a verse, but the application did not present it like that. Due to this, I envisioned the search not as a horizontal component (original) but as a full-body page that renders these verses vertically. 

I honestly decided to have a little fun with the app styling, I used the Google font called 'Medieval' and used a green color palette that made me think of the XVth century. It also makes the website look a bit dated like a Geocities circa 2006 where a ShakeSearch website would be a more typical common app (I liked that).

I did not want to include advanced libraries like react or any node modules for this type of app, I wanted to see how far I could get with vanillaJS. I did include https://www.npmjs.com/package/typo-js though.

### Changes

Here's a list of changes I added to the app, in order of implementation priority:

- HTML restructuring. I did change a couple elements: used a `<ul>` instead of a `<table>`. Some elements were wrapped inside a `<p>` element (not great for ally), so I changed that to a `<div>`, etc.
- Changed input type to search to add native behavior such as clearing the search.
- CSS styling. Similarly, I did not want to include any SASS or styled components, and went for regular CSS. Ordered from parent to smaller DOM tags.
- Fixed the case-sensitive search. `hamlet`, `Hamlet`, and `HAMLET` return the same results (the ordering changes: the casing used in the search takes priority).
- Included suggestions: Searching `Hmlet` returns no results, but the app will suggest to change the search to `Hamlet`. Similar to Google. (Used typoJS for this).
- URL params: The search is now shareable. URL params get updated with every search, which means you can paste `https://shakesearch-andrralv.herokuapp.com/?search=Hamlet` in the browser and get the results right away.
- Added an index number to each result verse.

### Possible Improvements and Brainstorming

- While the search now handles different types of casing. More unusual cases like `haMleT` don't work. I left it out of scope.
- `typo` does a good job at trying to complete the word when the user misses a character or misspells a word. But it's not as great as something like Google autocomplete. So a full fuzzy search algorithm with multiple words is not implemented (out of scope).
- While the app should render fine in mobile devices, responsiveness was left out of scope.
- I had this weird idea about connecting OpenAI and using the search input + keywords from a verse to render an Open AI image as an illustration next to each verse. But unfortunately the complexity of handling multiple images would make the app slow down a lot while waiting for the request.
- I think it'd be cool for the user to be able to click and save their favorite verses. This would mean either creating a session or storing the favorites in a Cookie (out of scope).