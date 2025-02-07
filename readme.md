## How to Create a New Article

1. **File Naming and Location**
   - **Directory:** All posts should be placed in the `_posts` directory.
   - **Filename Format:** Name your file using the date and a short title (for example, `YYYY-MM-DD-your-post-title.md`).
     - **Example:** `2025-03-15-introducing-new-feature.md`

2. **Adding YAML Front Matter**
   At the top of your Markdown file, include a YAML block (delimited by `---`) that specifies metadata about your post. This typically includes:
   - **layout:** Specify the layout (e.g., `post`).
   - **title:** The title of your article.
   - **date:** The publication date and time in the format `YYYY-MM-DD HH:MM:SS ±TTTT`.
   - **categories:** A list of categories (e.g., `[Category1, Category2]`).
   - **author:** Your name.

   **Example:**
   ```yaml
   ---
   layout: post
   title: "Introducing a New Feature"
   date:   2025-03-15 10:00:00 +0000
   categories: [Feature, Update]
   author: "Your Name"
   ---
   ```

3. **Writing Your Content**
   - Write the article content in Markdown after the YAML front matter.
   - Use headings, images, links, and other Markdown features as needed.
   - Save your file in the `_posts` directory.

---

## Managing Assets (Images, Videos, etc.)

1. **Asset Storage Location**
   - **Fixed Pages:** When creating fixed pages (e.g., About, Contact, or other standalone pages), store your assets directly under the `assets` directory (or within organized subdirectories like `assets/images` or `assets/videos`).
   - **Blog Posts:** For blog posts, it is recommended to create a dedicated subdirectory under `assets` using the post’s file name.
     - **Example:** For a post named `2025-03-15-introducing-new-feature.md`, create a subdirectory:
       ```
       assets/2025-03-15-introducing-new-feature/
       ```
       Then, place all images and other media related to that post inside this folder.

2. **Referencing Assets in Your Posts**
   - Use relative URLs in your Markdown or HTML to reference assets.
   - **Example in Markdown:**
     ```markdown
     ![Descriptive Alt Text](/assets/2025-03-15-introducing-new-feature/feature-image.jpg)
     ```
   - **Example in HTML:**
     ```html
     <img src="/assets/2025-03-15-introducing-new-feature/feature-image.jpg" alt="Descriptive Alt Text" width="600">
     ```
   - Starting the path with a forward slash (`/`) indicates that the asset is located relative to the site’s root directory.

---

## Previewing Your Article Locally

To allow contributors to preview articles on their local machines (even if the post’s date is set in the future), follow these steps:

1. **Navigate to Your Project Directory**
   Open your terminal and change to the root directory of the Jekyll project.

2. **Run the Local Server**
   Use the following command to start the Jekyll server with future-dated posts enabled:
   ```bash
   bundle exec jekyll serve --future true
   ```
   - The `--future true` flag ensures that posts with publication dates in the future are rendered. This is especially useful if you are scheduling posts.

3. **View in Your Browser**
   - Once the server is running, open your browser and go to [http://localhost:4000](http://localhost:4000).
   - Check that your new article appears as expected and review any formatting or content issues.

4. **Restart After Changes**
   - If you update any configuration settings (e.g., in `_config.yml`), stop the server and re-run the `bundle exec jekyll serve --future true` command for changes to take effect.

---

## Additional Tips

- **Using the Provided Example:**
  You can refer to the example post (`_posts/2025-01-24-bokeh-scatter-plot-performance-test.md`) for guidance on how to structure your own posts.

