# My Blog HTML Code

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>My Blog</title>
  <link rel="stylesheet" href="https://cdn.quilljs.com/1.3.6/quill.snow.css" />
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap" />
  <style>
    /* Define custom properties for colors */
    :root {
      --bg-color: #000;
      --text-color: #00BFFF;
      --accent-color: #FF0000;
    }

    /* Global Styles */
    body {
      background-color: var(--bg-color);
      color: var(--text-color);
      font-family: 'Roboto', sans-serif;
      margin: 0;
      padding-top: 60px; /* Space for fixed nav */
      display: flex;
      flex-direction: column;
      align-items: center;
    }

    header, nav, main, footer {
      width: 100%;
    }

    /* Navigation Bar */
    nav {
      background-color: var(--bg-color);
      padding: 10px 20px;
      position: fixed;
      top: 0;
      left: 0;
      z-index: 1000;
    }
    .nav-links {
      list-style: none;
      display: flex;
      justify-content: center;
      margin: 0;
      padding: 0;
    }
    .nav-links li {
      margin: 0 15px;
    }
    .nav-links a {
      text-decoration: none;
      color: var(--text-color);
      font-weight: bold;
    }

    /* Main Content Area */
    main {
      max-width: 800px;
      width: 80%;
      padding: 20px;
      margin-bottom: 20px;
      border-radius: 10px;
      box-shadow: 0 0 20px var(--text-color);
      background-color: var(--bg-color);
    }

    h1, h2 {
      text-align: center;
      margin-bottom: 20px;
      color: var(--text-color);
    }

    /* Form Inputs */
    input[type="text"], select {
      width: 100%;
      padding: 10px;
      margin-bottom: 10px;
      border: 1px solid var(--text-color);
      border-radius: 5px;
      background-color: var(--bg-color);
      color: var(--text-color);
    }
    #searchInput {
      margin-bottom: 20px;
    }

    /* Post Card Styles */
    .info-item {
      background-color: var(--bg-color);
      margin: 10px 0;
      padding: 15px;
      border-radius: 5px;
      border: 1px solid var(--text-color);
      display: flex;
      flex-wrap: wrap;
      align-items: flex-start;
    }
    .info-item img {
      max-width: 300px;
      max-height: 300px;
      margin-right: 20px;
      margin-bottom: 0;
      border-radius: 5px;
      flex-shrink: 0;
    }
    .info-item > div {
      flex: 1;
    }
    .info-item h2,
    .info-item p {
      color: var(--text-color);
      margin: 5px 0;
    }

    /* Button Styles */
    button {
      background-color: var(--accent-color);
      color: var(--bg-color);
      border: none;
      border-radius: 5px;
      cursor: pointer;
      padding: 10px 15px;
      transition: box-shadow 0.3s ease;
      margin: 5px 2px 0 0;
    }
    button:hover {
      box-shadow: 0 0 10px var(--accent-color),
                  0 0 20px var(--text-color),
                  0 0 30px var(--accent-color),
                  0 0 40px var(--text-color);
    }
    .toggle-button {
      margin: 10px 0;
    }

    /* Quill Editor Styles */
    .quill {
      height: 200px;
      background-color: var(--bg-color);
      border: 1px solid var(--text-color);
      border-radius: 5px;
      color: var(--text-color);
    }
    .quill .ql-toolbar {
      background-color: var(--bg-color);
      border: none;
      border-radius: 5px 5px 0 0;
    }
    .quill .ql-container {
      background-color: var(--bg-color);
      border: none;
      border-radius: 0 0 5px 5px;
      color: var(--text-color);
    }

    /* Modal Styles */
    .modal {
      display: none;
      position: fixed;
      z-index: 2000;
      left: 0;
      top: 0;
      width: 100%;
      height: 100%;
      overflow: auto;
      background-color: rgba(0, 0, 0, 0.4);
    }
    .modal-content {
      background-color: var(--bg-color);
      margin: 15% auto;
      padding: 20px;
      border: 1px solid var(--text-color);
      width: 80%;
      border-radius: 10px;
      text-align: center;
      color: var(--text-color);
    }
    #countdown {
      font-size: 24px;
      color: var(--accent-color);
    }

    /* Fullscreen Modal Styles */
    #fullscreenModal .modal-content {
      width: 90%;
      height: 90%;
      margin: auto;
      padding: 20px;
      position: relative;
      overflow: auto;
      background-color: var(--bg-color);
      border: 1px solid var(--text-color);
      color: var(--text-color);
    }
    #fullscreenModal img {
      max-width: 90%;
      height: auto;
      margin: 10px auto;
      display: block;
    }
    .close-button {
      position: absolute;
      top: 10px;
      right: 10px;
      background-color: var(--accent-color);
      border: none;
      color: var(--bg-color);
      padding: 5px 10px;
      cursor: pointer;
    }

    /* Footer */
    footer {
      background-color: var(--bg-color);
      padding: 20px;
      text-align: center;
    }
    footer p {
      margin: 0;
      color: var(--text-color);
    }
  </style>
</head>
<body>
  <header>
    <!-- Navigation Bar -->
    <nav>
      <ul class="nav-links">
        <li><a href="#home">Home</a></li>
        <li><a href="#archive">Archive</a></li>
      </ul>
    </nav>
  </header>

  <main id="home">
    <h1>My Blog</h1>
    <input type="text" id="searchInput" placeholder="Search posts..." oninput="searchPosts()" aria-label="Search Posts">
    <button class="toggle-button" id="toggleButton" aria-label="Switch view">Switch to Preview</button>
    <section class="editor" id="editor">
      <input type="text" id="titleInput" placeholder="Enter title" aria-label="Post Title">
      <input type="text" id="descriptionInput" placeholder="Enter description" aria-label="Post Description">
      <select id="categoryInput" aria-label="Post Category">
        <option value="">Select Category</option>
        <option value="Technology">Technology</option>
        <option value="Lifestyle">Lifestyle</option>
        <option value="Travel">Travel</option>
      </select>
      <div id="editorContainer" class="quill"></div>
      <input type="file" id="imageInput" accept="image/*" aria-label="Upload Image">
      <button id="addButton" aria-label="Add Post">Add Post</button>
    </section>
    <section class="preview" id="preview" style="display: none;">
      <h2>Preview</h2>
      <div id="previewContainer"></div>
    </section>
    <section id="infoContainer"></section>
  </main>

  <footer>
    <p>&copy; 2025 My Blog. All rights reserved.</p>
  </footer>

  <!-- Modal for Initial Choice -->
  <div id="modal" class="modal" role="dialog" aria-modal="true">
    <div class="modal-content">
      <p>Do you want to create a blog post or preview existing posts?</p>
      <button id="createButton" aria-label="Create Blog Post">Create Blog Post</button>
      <button id="previewButton" aria-label="Preview Posts">Preview Posts</button>
      <p id="countdown">30</p>
    </div>
  </div>

  <!-- Fullscreen Modal for Blog Post View -->
  <div id="fullscreenModal" class="modal" role="dialog" aria-modal="true">
    <div class="modal-content">
      <button id="closeFullscreen" class="close-button" aria-label="Close Fullscreen">Close</button>
      <div id="fullscreenContent"></div>
      <button id="fullscreenEdit" class="toggle-button" aria-label="Edit Post">Edit</button>
    </div>
  </div>

  <script src="https://cdn.quilljs.com/1.3.6/quill.js"></script>
  <script>
    document.addEventListener('DOMContentLoaded', () => {
      // Element references
      const infoContainer = document.getElementById('infoContainer');
      const titleInput = document.getElementById('titleInput');
      const descriptionInput = document.getElementById('descriptionInput');
      const categoryInput = document.getElementById('categoryInput');
      const imageInput = document.getElementById('imageInput');
      const addButton = document.getElementById('addButton');
      const editor = document.getElementById('editor');
      const preview = document.getElementById('preview');
      const previewContainer = document.getElementById('previewContainer');
      const toggleButton = document.getElementById('toggleButton');
      const modal = document.getElementById('modal');
      const createButton = document.getElementById('createButton');
      const previewButton = document.getElementById('previewButton');
      const countdownDisplay = document.getElementById('countdown');
      const searchInput = document.getElementById('searchInput');
      const fullscreenModal = document.getElementById('fullscreenModal');
      const fullscreenContent = document.getElementById('fullscreenContent');
      const closeFullscreen = document.getElementById('closeFullscreen');
      const fullscreenEdit = document.getElementById('fullscreenEdit');

      // Variable to track current post in fullscreen view
      let currentPostElement = null;

      // Initialize Quill editor
      const quill = new Quill('#editorContainer', {
        theme: 'snow',
        modules: {
          toolbar: [
            [{ header: [1, 2, false] }],
            ['bold', 'italic', 'underline'],
            ['image', 'code-block'],
            ['clean']
          ]
        }
      });

      // Load stored posts from localStorage
      function loadPosts() {
        const storedPosts = localStorage.getItem('info');
        if (storedPosts) {
          infoContainer.innerHTML = storedPosts;
          attachPostEventListeners();
        }
      }

      // Save posts to localStorage
      function savePosts() {
        localStorage.setItem('info', infoContainer.innerHTML);
      }

      // Reattach event listeners to posts after loading from storage
      function attachPostEventListeners() {
        const posts = infoContainer.getElementsByClassName('info-item');
        Array.from(posts).forEach(post => {
          const openBtn = post.querySelector('.open-btn');
          const editBtn = post.querySelector('.edit-btn');
          const deleteBtn = post.querySelector('.delete-btn');
          if (openBtn) openBtn.addEventListener('click', () => openFullScreen(post));
          if (editBtn) editBtn.addEventListener('click', () => loadPostForEdit(post));
          if (deleteBtn) deleteBtn.addEventListener('click', () => {
            post.remove();
            savePosts();
          });
        });
      }

      // Function to create and add a new post
      function addNewPost() {
        const newTitle = titleInput.value.trim();
        const newDescription = descriptionInput.value.trim();
        const newCategory = categoryInput.value;
        const newContent = quill.root.innerHTML.trim();
        const newImageFile = imageInput.files[0];

        // Require a title and content before proceeding
        if (!newTitle || !newContent) return;

        // Create post container
        const postDiv = document.createElement('div');
        postDiv.className = 'info-item';

        // Create inner content container
        const contentDiv = document.createElement('div');

        // Title
        const titleEl = document.createElement('h2');
        titleEl.textContent = newTitle;
        contentDiv.appendChild(titleEl);

        // Description
        const descEl = document.createElement('p');
        descEl.textContent = newDescription;
        contentDiv.appendChild(descEl);

        // Category
        const categoryEl = document.createElement('p');
        categoryEl.textContent = `Category: ${newCategory}`;
        contentDiv.appendChild(categoryEl);

        // Date
        const dateEl = document.createElement('p');
        dateEl.textContent = new Date().toLocaleString();
        contentDiv.appendChild(dateEl);

        // Post content
        const postContentEl = document.createElement('div');
        postContentEl.innerHTML = newContent;
        contentDiv.appendChild(postContentEl);

        // Buttons for actions
        const openButton = document.createElement('button');
        openButton.textContent = 'Open';
        openButton.className = 'open-btn';
        openButton.addEventListener('click', () => openFullScreen(postDiv));
        contentDiv.appendChild(openButton);

        const editButton = document.createElement('button');
        editButton.textContent = 'Edit';
        editButton.className = 'edit-btn';
        editButton.addEventListener('click', () => loadPostForEdit(postDiv));
        contentDiv.appendChild(editButton);

        const deleteButton = document.createElement('button');
        deleteButton.textContent = 'Delete';
        deleteButton.className = 'delete-btn';
        deleteButton.addEventListener('click', () => {
          postDiv.remove();
          savePosts();
        });
        contentDiv.appendChild(deleteButton);

        // If an image was uploaded, create and insert an image element
        if (newImageFile) {
          const imgEl = document.createElement('img');
          imgEl.alt = 'Post image';
          const reader = new FileReader();
          reader.onload = (e) => {
            imgEl.src = e.target.result;
            postDiv.insertBefore(imgEl, contentDiv);
            postDiv.appendChild(contentDiv);
            savePosts();
          };
          reader.readAsDataURL(newImageFile);
        } else {
          postDiv.appendChild(contentDiv);
          savePosts();
        }

        // Append the new post and clear the form
        infoContainer.appendChild(postDiv);
        titleInput.value = '';
        descriptionInput.value = '';
        categoryInput.value = '';
        quill.setContents([]);
        imageInput.value = '';
      }

      // Event listener for the Add Post button
      addButton.addEventListener('click', addNewPost);

      // Load a post into the editor for editing
      function loadPostForEdit(postElement) {
        const title = postElement.querySelector('h2').textContent;
        const description = postElement.querySelector('p').textContent;
        const categoryText = postElement.querySelector('p:nth-of-type(2)').textContent;
        const contentHTML = postElement.querySelector('div').innerHTML;
        titleInput.value = title;
        descriptionInput.value = description;
        categoryInput.value = categoryText.replace('Category: ', '');
        quill.root.innerHTML = contentHTML;
        postElement.remove();
        savePosts();
        editor.style.display = 'block';
        preview.style.display = 'none';
      }

      // Display a post in the fullscreen modal
      function openFullScreen(postElement) {
        currentPostElement = postElement;
        fullscreenContent.innerHTML = postElement.innerHTML;
        fullscreenModal.style.display = 'block';
      }

      // Search functionality by title or category
      window.searchPosts = () => {
        const searchTerm = searchInput.value.toLowerCase();
        const posts = infoContainer.getElementsByClassName('info-item');
        Array.from(posts).forEach(post => {
          const title = post.querySelector('h2').textContent.toLowerCase();
          const category = post.querySelector('p:nth-of-type(2)').textContent.toLowerCase();
          post.style.display = (title.includes(searchTerm) || category.includes(searchTerm)) ? 'flex' : 'none';
        });
      };

      // Toggle between editor and preview modes
      toggleButton.addEventListener('click', () => {
        if (editor.style.display === 'none') {
          editor.style.display = 'block';
          preview.style.display = 'none';
          toggleButton.textContent = 'Switch to Preview';
        } else {
          editor.style.display = 'none';
          preview.style.display = 'block';
          toggleButton.textContent = 'Switch to Editor';
          updatePreview();
        }
      });

      // Update the preview section by cloning posts
      function updatePreview() {
        previewContainer.innerHTML = '';
        Array.from(infoContainer.children).forEach(post => {
          previewContainer.appendChild(post.cloneNode(true));
        });
      }

      // Fullscreen modal close functionality
      closeFullscreen.addEventListener('click', () => {
        fullscreenModal.style.display = 'none';
      });

      // Fullscreen modal edit functionality
      fullscreenEdit.addEventListener('click', () => {
        if (currentPostElement) {
          loadPostForEdit(currentPostElement);
          fullscreenModal.style.display = 'none';
        }
      });

      // Modal countdown and initial choice handling
      modal.style.display = 'block';
      let countdown = 30;
      const countdownInterval = setInterval(() => {
        countdownDisplay.textContent = countdown;
        if (--countdown < 0) {
          clearInterval(countdownInterval);
          createButton.click();
        }
      }, 1000);

      createButton.addEventListener('click', () => {
        modal.style.display = 'none';
        editor.style.display = 'block';
        preview.style.display = 'none';
        toggleButton.style.display = 'block';
        clearInterval(countdownInterval);
      });

      previewButton.addEventListener('click', () => {
        modal.style.display = 'none';
        editor.style.display = 'none';
        preview.style.display = 'block';
        toggleButton.style.display = 'none';
        updatePreview();
        clearInterval(countdownInterval);
      });

      // Load posts on startup
      loadPosts();
    });
  </script>
</body>
</html>
```

## Explanation of Key Improvements

- **Semantic Structure:**  
  Uses `<header>`, `<main>`, and `<footer>` to enhance readability and accessibility.

- **CSS Custom Properties:**  
  Colors are defined as variables for easier theming and maintenance.

- **Accessibility Enhancements:**  
  ARIA attributes and alt texts are added for screen readers and improved usability.

- **JavaScript Modularization:**  
  Functions like `loadPosts()`, `savePosts()`, and `addNewPost()` improve the organization and readability of the code.
