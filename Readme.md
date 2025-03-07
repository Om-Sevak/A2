# Resume Hosting with a Static Site Generator and Forge

## Statement of Purpose

This README explains, step by step, how to create, deploy, and maintain a professional online resume using a static site generator and a version control forge. It is intended for technical communication beginners—such as students or new professionals—with a basic understanding of Markdown and Git. The document is structured following the ABC format (Abstract, Body, Conclusion) as recommended in Chapter 8 of *Technical Communication: A Practical Approach* by William S. Pfeiffer. By following these instructions, you will learn how to convert your Markdown resume into a static website and deploy it on GitHub Pages using ghp-import. This guide also incorporates key recommendations from Andrew Etter on using lightweight markup languages to simplify technical documentation.

---

## Prerequisites

Before you begin, ensure you have the following resources:

- **Git:**  
  A distributed version control system for tracking project changes.  
  [Download Git](https://git-scm.com/)

- **Markdown Editor:**  
  An editor with Markdown support and live preview, such as Visual Studio Code, Typora, or StackEdit.

- **Static Site Generator:**  
  A tool to convert Markdown into a static website. Options include:  
  - **Pelican (Python-based):** [Pelican](https://www.getpelican.com/)  
  - **Jekyll (Ruby-based):** [Jekyll](https://jekyllrb.com/)  
  - **Hugo (Go-based):** [Hugo](https://gohugo.io/)

- **Forge Account:**  
  A platform for hosting your repository and website; GitHub is recommended.  
  [Sign up on GitHub](https://github.com/)

- **Python (if using Pelican):**  
  [Download Python](https://www.python.org/)

*According to Chapter 8’s guidelines, using Markdown helps you focus on content, while a static site generator automates the conversion of that content into a professional webpage.*

---

## Instructions

*The instructions below follow the ABC format, with each step designed as a single, clear action for both process explanations (for understanding) and instructions (for doing).*

### A. Project Setup

1. **Create Your Resume File:**
   - Write your professional resume in Markdown. Create a file named `resume.md` with clear sections (e.g., "Professional Experience," "Education," "Skills").
   - *Example:*
     ```markdown
     # John Doe

     ## Professional Experience
     - **Software Developer, XYZ Inc.** – Developed scalable web applications.
     - **Intern, ABC Corp.** – Assisted in testing and documentation.

     ## Education
     - Bachelor of Science in Computer Science, University of Manitoba

     ## Skills
     - **Languages:** Python, JavaScript, C++
     - **Tools:** Git, Docker, Linux
     ```

2. **Set Up Your Project Directory:**
   - Create a new folder called `resume-site`.
   - Inside the folder, create a subfolder named `content` and place your `resume.md` file there.
   - *Note:* Organizing your files in this manner keeps your content separate from configuration files.

3. **Initialize a Git Repository:**
   - Open your terminal, navigate to the `resume-site` folder, and run:
     ```sh
     git init
     ```
   - *Result:* A Git repository is created to track your project changes.

4. **Add and Commit Files:**
   - Run:
     ```sh
     git add .
     git commit -m "Initial commit: Added resume content"
     ```
   - *Instruction:* Each step here is atomic, following Pfeiffer’s guideline for clear, step-by-step instructions.

### B. Generating the Static Website

5. **Select a Static Site Generator:**
   - Choose between Pelican, Jekyll, or Hugo. For example, if you are comfortable with Python, choose Pelican.
   - *Tip:* Your choice depends on your familiarity with the tool, but all effectively convert Markdown to HTML.
   - *Reference:* Etter recommends using lightweight markup for simplicity.

6. **Configure the Static Site Generator (Using Pelican as an Example):**
   - Run the Pelican quickstart by executing:
     ```sh
     pelican-quickstart
     ```
   - Answer the prompts:
     - Specify the project folder.
     - Set the title (e.g., “John Doe Resume”).
     - Choose the language, default folder for content (`content`), etc.
   - *Guideline:* This interactive process sets up your configuration, following an ABC format where the Abstract outlines purpose and the Body provides detailed steps.

7. **Generate the Website:**
   - Run:
     ```sh
     pelican content
     ```
   - *Result:* Your Markdown resume is converted to HTML files stored in the `output` folder.
   - *Note:* Grouping of steps ensures clarity and logical flow, as recommended in Chapter 8.

8. **Preview Locally:**
   - Serve your site locally by running:
     ```sh
     pelican --listen
     ```
   - Open your browser and go to [http://127.0.0.1:8000](http://127.0.0.1:8000) to view your site.
   - *Verification:* This step confirms that your process explanation leads to a clear, working output.

### C. Deploying Online

9. **Create a Remote Repository:**
   - Log in to GitHub and create a new repository named `resume-site` using the GitHub interface.
   - *Action:* Follow GitHub’s prompts to set up the repository.

10. **Push Your Local Repository:**
    - Link your local repository to the remote repository and push your files by running:
      ```sh
      git remote add origin https://github.com/your-username/resume-site.git
      git branch -M main
      git push -u origin main
      ```
    - *Result:* Your project is now safely version-controlled on GitHub.

11. **Deploy Using ghp-import:**
    - Install ghp-import (if not already installed):
      ```sh
      python -m pip install ghp-import
      ```
    - Generate your static site in publishconf.py:
      ```sh
      pelican content -s publishconf.py
      ```
    - Import the generated output into a new branch (typically `gh-pages`):
      ```sh
      ghp-import output -b gh-pages
      ```
    - Push the `gh-pages` branch to GitHub:
      ```sh
      git push origin gh-pages
      ```
    - *Outcome:* Your static site is now deployed on GitHub Pages and is accessible at a URL such as `https://your-username.github.io/resume-site/`.

12. **Select the "gh-pages" Branch in GitHub Settings:**

    - In your GitHub repository, go to Settings > Pages.
    - Under “Source,” select the gh-pages branch (instead of the default master/main).
    - Save your changes.
    - Result: Your site is served from the gh-pages branch and is accessible at a URL like https://your-username.github.io/resume-site/.
    
13. **Verify the Deployment:**
    - Open your browser and navigate to the GitHub Pages URL to ensure that your resume is displayed correctly.
    - *Guideline:* This step confirms that the deployment instructions yield a verifiable result.

---

## Further Resources/Readings

For additional background and further reading on the topics covered in this README, consider the following resources:

- [Markdown Guide](https://www.markdownguide.org/) – A comprehensive tutorial on Markdown.
- [GitHub Pages Documentation](https://docs.github.com/en/pages) – Official instructions for deploying websites using GitHub Pages.
- [Pelican Documentation](https://www.getpelican.com/) – Detailed guidance on setting up and using the Pelican static site generator.
- [Jekyll Tutorial](https://jekyllrb.com/docs/) – An introductory guide to converting Markdown into a website with Jekyll.

*These resources offer additional perspectives on the tools and processes discussed, reinforcing the instructional guidelines referenced from Pfeiffer’s work.*

---

## FAQ

**Q: Why is Markdown preferred over raw HTML for technical documentation?**  
**A:** Markdown is simpler and more readable, allowing you to focus on content without getting bogged down in complex HTML syntax. This approach promotes clarity and maintainability, in line with Etter’s recommendations.

**Q: I updated my Markdown resume, but the changes are not showing on my live website. What should I do?**  
**A:** Ensure that you have committed and pushed your changes to the correct branch on GitHub. Then, regenerate your static site by running `pelican content` and deploy the updated output using `ghp-import` with the `gh-pages` branch. Finally, clear your browser cache to see the latest version.

---

## Credits

- **Project Developer:** Om Sevavk
- **Peer Review Contributors:** Meshvi Patel, Adwait Pujari
- **Third-Party Tools and Resources:**  
  - Static site themes and templates from [Pelican Themes](https://github.com/getpelican/pelican-themes)  
  - Guidance from GitHub Pages documentation and online Markdown tutorials
- **Instructional References:**  
  - *Technical Communication: A Practical Approach* by William S. Pfeiffer and Kaye Adkins (Chapter 8: Process Explanations and Instructions)  
  - Andrew Etter’s recommendations on using lightweight markup languages for efficient technical documentation

