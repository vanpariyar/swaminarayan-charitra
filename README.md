# Swaminarayan Charitra 🙏

This project is a community-driven collection of Charitras (Divine Activities) of Lord Swaminarayan. It aims to organize and share these spiritual stories in **Gujarati, Hindi, and English** for devotees worldwide.

The website is built using [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

**View Live Site:** [https://vanpariyar.in/swaminarayan-charitra/](https://vanpariyar.in/swaminarayan-charitra/)

---

## 🚀 Local Development

Follow these steps to set up the project on your machine.

### Prerequisites
- [Node.js](https://nodejs.org/) (Recommended: Latest LTS)
- [NPM](https://www.npmjs.com/) (Installed automatically with Node.js)

### Setup & Run
1.  **Clone the repository:**
    ```bash
    git clone https://github.com/vanpariyar/swaminarayan-charitra.git
    cd swaminarayan-charitra
    ```

2.  **Install dependencies:**
    This installs the Hugo binary locally using `hugo-bin`.
    ```bash
    npm install
    ```

3.  **Start the development server:**
    Run the following command to preview the site at `http://localhost:1313/`.
    ```bash
    npm start
    ```

4.  **Build for production:**
    ```bash
    npm run build
    ```

---

## ✍️ How to Contribute

We welcome contributions from everyone! Whether you want to add a new Charitra, fix a typo, or improve the design.

### Adding a New Charitra
1.  **Create a new post:**
    Use the following command to create a new Charitra file with the correct template:
    ```bash
    npx hugo new charitra/YYYY-MM-DD-your-charitra-name.md
    ```
2.  **Edit the file:**
    Navigate to `content/charitra/` and open your new file.
3.  **Fill in the content:**
    -   Update the `title`, `author`, `tags`, `categories`, etc., in the front matter.
    -   Add the story in Gujarati, Hindi, and English (as available).
    -   Use the `<!--more-->` tag to separate the summary from the full content.
4.  **Preview locally:** Run `npm start` and check if everything looks good.
5.  **Submit your changes:** Push your branch and create a Pull Request.

---

## 📁 Project Structure

-   `content/charitra/`: All spiritual stories (Markdown files).
-   `archetypes/charitra.md`: The template used for new Charitra posts.
-   `static/`: Images, icons, and other static assets.
-   `layouts/`: Custom HTML overrides for the theme.
-   `config.yml`: Main configuration for the site and theme.
-   `themes/hugo-PaperMod`: The core theme files.

---

## 🛠 Tech Stack
-   **Static Site Generator:** Hugo (Latest)
-   **Theme:** PaperMod
-   **Deployment:** GitHub Pages (via GitHub Actions)

---

## 🙏 Credits
-   **Authors:** Bharat Desai, Dhaval Desai, Hitendra Kalariya, Ronak Vanpariya
-   **Community Contributors:** Thank you to everyone who has contributed Charitras!

`If you want to contribute or have suggestions, feel free to reach out via GitHub Issues or contact us directly at ronak@vanpariyar.in`
