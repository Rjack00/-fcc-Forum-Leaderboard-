# **Forum Posts Fetcher**

This project fetches and displays the latest posts from the freeCodeCamp forum, providing an interactive table with essential details such as post titles, categories, view counts, and timestamps.  

## **Features**
- **Fetch Latest Posts:** Retrieves the most recent topics from the freeCodeCamp forum.
- **Dynamic Categories:** Links posts to their respective categories with clickable category labels.
- **User Avatars:** Displays user avatars alongside their posts.
- **Time Stamps:** Converts timestamps into a human-readable "time ago" format.
- **Formatted View Counts:** Converts large numbers into concise formats like "1k."

---

## **How It Works**

### **Main Components**
1. **Data Fetching:**
   - Fetches data from the forum's JSON feed at:
     ```plaintext
     https://cdn.freecodecamp.org/curriculum/forum-latest/latest.json
     ```
   - Displays the fetched posts in a table on the webpage.

2. **Dynamic Rendering:**
   - Builds the table with:
     - Post titles linking to the original forum thread.
     - User avatars.
     - Categories dynamically mapped to their respective URLs and CSS classes.
     - Timestamps in a relative "time ago" format.
     - View counts formatted as compact strings.

3. **Reusable Functions:**
   - `forumCategory(id)`: Maps category IDs to category names and URLs.
   - `timeAgo(time)`: Converts timestamps into a "time ago" format.
   - `viewCount(views)`: Formats large view counts (e.g., 1200 → 1k).
   - `avatars(posters, users)`: Generates avatar image tags for users.

---

## **Setup and Usage**

### **Prerequisites**
- A modern web browser with JavaScript enabled.
- Basic HTML and JavaScript knowledge for customization.

### **How to Use**
1. **HTML Structure:**
   - Ensure there is a table element with an ID of `posts-container` in your HTML:
     ```html
     <table id="posts-container"></table>
     ```

2. **JavaScript Integration:**
   - Include the script in your webpage:
     ```html
     <script src="path-to-your-script.js"></script>
     ```

3. **Run the Script:**
   - When the page loads, the script fetches and renders the latest forum posts.

---

## **Code Explanation**

### **Key Functions**
- **`fetchData()`**
  - Asynchronously fetches data from the forum JSON feed and passes it to the rendering function.
  
- **`showLatestPosts(data)`**
  - Takes the fetched data and renders a table with the latest posts.

- **`avatars(posters, users)`**
  - Generates user avatar images by replacing the `{size}` placeholder in the avatar URL template.

### **Category Mapping**
The script maps category IDs to their names and styles using the `allCategories` object:
```javascript
const allCategories = {
  299: { category: "Career Advice", className: "career" },
  // Other categories...
};
```

If a category ID is missing, it defaults to "General."

---

## **Customization**

1. **Add New Categories:**
   - Update the `allCategories` object with additional IDs, names, and CSS class names.

2. **Change Avatar Size:**
   - Modify the `replace` function in the `avatars` method:
     ```javascript
     const avatar = user.avatar_template.replace(/{size}/, desiredSize);
     ```

3. **Styling:**
   - Add custom CSS for different category classes or avatar containers.

---

## **Known Limitations**
- The forum's JSON feed might not always provide the latest data in real time.
- Missing category IDs default to "General."

---

## **Further Development**
- Implement a search bar for filtering posts.
- Paginate results to handle a larger number of topics.
