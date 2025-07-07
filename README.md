
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>hyper+connection</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body> 
    <style>
      @import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@600;700&family=Roboto&display=swap");
      * {
        box-sizing: border-box;
      }
      body {
        margin: 0;
        padding: 0;
        font-family: "Roboto", sans-serif;
        background: #ffffff;
        color: #6b7280;
      }
      header {
        background: #ffffff;
        position: sticky;
        top: 0;
        z-index: 1000;
        border-bottom: 1px solid #e5e7eb;
        padding: 1rem 2rem;
        display: flex;
        align-items: center;
        justify-content: space-between;
      }
      header h1 {
        font-family: "Montserrat", sans-serif;
        font-weight: 700;
        font-size: 48px;
        margin: 0;
        color: #111827;
        user-select: none;
      }
      header button {
        background: transparent;
        border: none;
        color: #6b7280;
        font-weight: 600;
        font-size: 1rem;
        cursor: pointer;
        padding: 0.5rem 1rem;
        border-radius: 0.75rem;
        transition: background-color 0.2s ease;
      }
      header button:hover {
        background-color: #f3f4f6;
      }
      main {
        max-width: 1200px;
        margin: 4rem auto 6rem;
        padding: 0 2rem;
        display: flex;
        flex-direction: column;
        gap: 4rem;
      }
      /* Blog List Gallery */
      #blog-list {
        display: grid;
        grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
        gap: 2rem;
      }
      .post-card {
        background: #f9fafb;
        padding: 1rem 1rem 1.5rem 1rem;
        border-radius: 0.75rem;
        box-shadow: 0 2px 10px rgb(0 0 0 / 0.05);
        cursor: pointer;
        display: flex;
        flex-direction: column;
        transition: box-shadow 0.3s ease;
        color: #374151;
      }
      .post-card:hover,
      .post-card:focus-visible {
        box-shadow: 0 6px 15px rgb(0 0 0 / 0.1);
        outline: none;
      }
      .post-image {
        width: 100%;
        max-height: 160px;
        object-fit: cover;
        border-radius: 0.75rem;
        margin-bottom: 0.8rem;
        user-select: none;
      }
      .post-title {
        margin: 0 0 0.3rem;
        font-family: "Montserrat", sans-serif;
        font-weight: 700;
        font-size: 1.4rem;
        color: #111827;
      }
      .post-date {
        font-size: 0.85rem;
        color: #6b7280;
        margin-bottom: 0.7rem;
      }
      .post-excerpt {
        flex-grow: 1;
        font-size: 1rem;
        line-height: 1.5;
      }
      /* Full post view */
      #post-view {
        background: #f9fafb;
        padding: 2rem;
        border-radius: 0.75rem;
        box-shadow: 0 4px 20px rgb(0 0 0 / 0.1);
        color: #374151;
      }
      #post-view h2 {
        margin-top: 0;
        font-family: "Montserrat", sans-serif;
        font-weight: 700;
        font-size: 2.5rem;
        color: #111827;
      }
      #post-view .post-date {
        margin-bottom: 1rem;
        color: #6b7280;
        font-size: 0.9rem;
      }
      #post-view .post-content {
        white-space: pre-wrap;
        line-height: 1.7;
        font-size: 1.25rem;
        margin-bottom: 2rem;
      }
      #post-view .post-media {
        display: flex;
        flex-wrap: wrap;
        gap: 1.5rem;
      }
      #post-view .post-media img,
      #post-view .post-media video {
        max-width: 100%;
        max-height: 400px;
        border-radius: 0.75rem;
        box-shadow: 0 4px 12px rgb(0 0 0 / 0.1);
        cursor: zoom-in;
        object-fit: contain;
      }
      #post-view button {
        margin-top: 1.5rem;
        background: #111827;
        border: none;
        color: white;
        padding: 0.75rem 1.5rem;
        border-radius: 0.75rem;
        cursor: pointer;
        font-weight: 700;
        font-size: 1.25rem;
        transition: background-color 0.3s ease;
      }
      #post-view button:hover {
        background-color: #1f2937;
      }
      /* Admin dashboard */
      #admin-dashboard {
        display: none;
        background: #f9fafb;
        padding: 2rem;
        border-radius: 0.75rem;
        box-shadow: 0 5px 24px rgb(0 0 0 / 0.1);
      }
      #admin-dashboard h2 {
        font-family: "Montserrat", sans-serif;
        color: #111827;
        font-weight: 700;
        font-size: 2.5rem;
        margin-top: 0;
        margin-bottom: 2rem;
        text-align: center;
      }
      #admin-post-list {
        margin-bottom: 3rem;
      }
      .admin-post {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem 1.25rem;
        background: #ffffff;
        border-radius: 0.75rem;
        margin-bottom: 1.25rem;
        box-shadow: 0 3px 12px rgb(0 0 0 / 0.05);
        color: #374151;
      }
      .admin-post-title {
        font-weight: 700;
        color: #111827;
        flex: 1;
        font-size: 1.1rem;
      }
      .admin-post-date {
        margin-left: 1rem;
        font-size: 1rem;
        color: #6b7280;
        white-space: nowrap;
      }
      .admin-btns button {
        background: transparent;
        border: none;
        color: #2563eb;
        font-weight: 700;
        cursor: pointer;
        margin-left: 1rem;
        border-radius: 0.75rem;
        padding: 0.4rem 1rem;
        transition: background-color 0.3s ease;
        font-size: 1.1rem;
      }
      .admin-btns button:hover {
        background-color: #dbeafe;
      }
      .admin-btns button.delete-btn {
        color: #dc2626;
      }
      .admin-btns button.delete-btn:hover {
        background-color: #fee2e2;
      }
      form#post-form {
        border-top: 2px solid #d1d5db;
        padding-top: 2rem;
        margin-bottom: 3rem;
      }
      form#post-form label {
        display: block;
        margin-bottom: 0.5rem;
        font-weight: 600;
        color: #374151;
        font-size: 1.1rem;
      }
      form#post-form input[type="text"],
      form#post-form textarea,
      form#post-form input[type="file"] {
        width: 100%;
        padding: 0.75rem 1rem;
        border: 1px solid #d1d5db;
        border-radius: 0.75rem;
        font-size: 1rem;
        font-family: "Roboto", sans-serif;
        margin-bottom: 1.5rem;
        color: #111827;
        background: #ffffff;
      }
      form#post-form textarea {
        height: 130px;
        resize: vertical;
      }
      form#post-form input[type="file"] {
        padding: 0.5rem 0.6rem;
      }
      form#post-form .media-preview {
        margin-top: 1rem;
        display: flex;
        flex-wrap: wrap;
        gap: 1.25rem;
      }
      form#post-form .media-preview-item {
        position: relative;
        display: inline-block;
      }
      form#post-form .media-preview-item img,
      form#post-form .media-preview-item video {
        max-height: 110px;
        border-radius: 0.75rem;
        object-fit: cover;
        box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
      }
      form#post-form .media-preview-item button {
        position: absolute;
        top: -10px;
        right: -10px;
        background: #dc2626;
        border: none;
        color: white;
        border-radius: 50%;
        width: 24px;
        height: 24px;
        font-size: 16px;
        line-height: 24px;
        cursor: pointer;
        font-weight: 800;
        box-shadow: 0 0 5px rgba(0, 0, 0, 0.25);
        transition: background-color 0.3s ease;
      }
      form#post-form .media-preview-item button:hover {
        background: #b91c1c;
      }
      form#post-form button[type="submit"] {
        background: #2563eb;
        color: white;
        border: none;
        padding: 0.75rem 1.5rem;
        border-radius: 0.75rem;
        font-weight: 700;
        cursor: pointer;
        font-size: 1.15rem;
        transition: background-color 0.3s ease;
      }
      form#post-form button[type="submit"]:hover {
        background: #1e40af;
      }
      /* Password change form */
      #change-password-section {
        border-top: 2px solid #d1d5db;
        padding-top: 2rem;
        max-width: 400px;
        margin: 0 auto 2rem auto;
        background: #f3f4f6;
        border-radius: 0.75rem;
        box-shadow: 0 3px 8px rgba(0, 0, 0, 0.1);
        color: #374151;
      }
      #change-password-section h3 {
        color: #111827;
        margin: 0 0 1rem 0;
        text-align: center;
        font-family: "Montserrat", sans-serif;
        font-weight: 700;
        font-size: 1.5rem;
      }
      #change-password-section label {
        display: block;
        margin-bottom: 0.5rem;
        font-weight: 600;
        font-size: 1rem;
        color: #374151;
      }
      #change-password-section input[type="password"] {
        width: 100%;
        padding: 0.6rem 0.8rem;
        margin-bottom: 1.25rem;
        border: 1px solid #d1d5db;
        border-radius: 0.75rem;
        font-size: 1rem;
        font-family: "Roboto", sans-serif;
        color: #111827;
      }
      #change-password-section button {
        width: 100%;
        background: #2563eb;
        color: white;
        border: none;
        padding: 0.75rem 0;
        border-radius: 0.75rem;
        font-weight: 700;
        cursor: pointer;
        font-size: 1.15rem;
        transition: background-color 0.3s ease;
      }
      #change-password-section button:hover {
        background: #1e40af;
      }
      /* New back to blog home button style */
      #backToHomeBtn {
        background: #2563eb;
        color: white;
        border: none;
        padding: 0.75rem 1.5rem;
        border-radius: 0.75rem;
        cursor: pointer;
        font-weight: 700;
        font-size: 1.15rem;
        margin-bottom: 2rem;
        transition: background-color 0.3s ease;
      }
      #backToHomeBtn:hover {
        background: #1e40af;
      }
      /* Responsive */
      @media (max-width: 650px) {
        header {
          flex-direction: column;
          gap: 1rem;
        }
        #admin-dashboard .admin-post {
          flex-direction: column;
          align-items: flex-start;
          gap: 0.5rem;
        }
        .admin-post-date {
          margin-left: 0;
        }
        .admin-btns button {
          margin-left: 0;
          margin-right: 0.6rem;
        }
      }
    </style>
  </head>
  <body>
    <header>
      <h1>Hyperlink</h1>
      <button id="toggleAdminBtn" aria-label="Toggle admin login/logout">
        Admin Login
      </button>
    </header>
    <main>
      <!-- Blog Listing (Gallery mode) -->
      <section id="blog-list-section" aria-label="Blog posts">
        <div id="blog-list"></div>
      </section>
      <!-- Full Post View -->
      <section
        id="post-view-section"
        style="display: none"
        aria-label="Blog post content"
      >
        <div id="post-view">
          <h2></h2>
          <p class="post-date"></p>
          <div class="post-content"></div>
          <div class="post-media"></div>
          <button id="backToListBtn" aria-label="Back to blog list">
            Back to Blog
          </button>
        </div>
      </section>
      <!-- Admin Dashboard -->
      <section id="admin-dashboard" aria-label="Admin Dashboard">
        <button id="backToHomeBtn" aria-label="Back to blog home">
          Back to Blog Home
        </button>
        <h2>Admin Dashboard</h2>
        <div
          id="admin-post-list"
          aria-live="polite"
          aria-relevant="additions"
        ></div>
        <form
          id="post-form"
          enctype="multipart/form-data"
          aria-label="Create or Edit Blog Post"
        >
          <input type="hidden" id="post-id" />
          <label for="post-title">Title</label>
          <input
            type="text"
            id="post-title"
            required
            maxlength="100"
            autocomplete="off"
          />
          <label for="post-content">Content</label>
          <textarea
            id="post-content"
            required
            maxlength="3000"
            autocomplete="off"
          ></textarea>
          <label for="post-media"
            >Upload Images and Videos (multiple allowed)</label
          >
          <input
            type="file"
            id="post-media"
            accept="image/*,video/*"
            multiple
            aria-describedby="media-desc"
          />
          <div
            class="media-preview"
            id="media-preview"
            aria-live="polite"
            aria-relevant="additions removals"
          ></div>
          <button type="submit">Save Post</button>
        </form>
        <section
          id="change-password-section"
          aria-label="Change Admin Password"
        >
          <h3>Change Admin Password</h3>
          <label for="current-password">Current Password</label>
          <input
            type="password"
            id="current-password"
            autocomplete="current-password"
          />
          <label for="new-password">New Password</label>
          <input
            type="password"
            id="new-password"
            autocomplete="new-password"
          />
          <label for="confirm-password">Confirm New Password</label>
          <input
            type="password"
            id="confirm-password"
            autocomplete="new-password"
          />
          <button id="change-password-btn">Change Password</button>
        </section>
      </section>
    </main>
    <script>
      (() => {
        "use strict";
        const toggleAdminBtn = document.getElementById("toggleAdminBtn");
        const blogListSection = document.getElementById("blog-list-section");
        const blogList = document.getElementById("blog-list");
        const postViewSection = document.getElementById("post-view-section");
        const postView = document.getElementById("post-view");
        const postViewTitle = postView.querySelector("h2");
        const postViewDate = postView.querySelector(".post-date");
        const postViewContent = postView.querySelector(".post-content");
        const postViewMedia = postView.querySelector(".post-media");
        const backToListBtn = document.getElementById("backToListBtn");
        const adminDashboard = document.getElementById("admin-dashboard");
        const adminPostList = document.getElementById("admin-post-list");
        const postForm = document.getElementById("post-form");
        const postIdInput = document.getElementById("post-id");
        const postTitleInput = document.getElementById("post-title");
        const postContentInput = document.getElementById("post-content");
        const postMediaInput = document.getElementById("post-media");
        const mediaPreview = document.getElementById("media-preview");
        const backToHomeBtn = document.getElementById("backToHomeBtn");
        const currentPwdInput = document.getElementById("current-password");
        const newPwdInput = document.getElementById("new-password");
        const confirmPwdInput = document.getElementById("confirm-password");
        const changePwdBtn = document.getElementById("change-password-btn");
        let isAdmin = false;
        const STORAGE_KEY = "my-blog-posts";
        const ADMIN_PASSWORD_KEY = "my-blog-admin-password";
        let currentMediaArray = [];
        function initAdminPassword() {
          if (!localStorage.getItem(ADMIN_PASSWORD_KEY)) {
            localStorage.setItem(ADMIN_PASSWORD_KEY, "admin123");
          }
        }
        function getAdminPassword() {
          return localStorage.getItem(ADMIN_PASSWORD_KEY);
        }
        function setAdminPassword(newPassword) {
          localStorage.setItem(ADMIN_PASSWORD_KEY, newPassword);
        }
        function getPosts() {
          const postsJson = localStorage.getItem(STORAGE_KEY);
          if (!postsJson) return [];
          try {
            const posts = JSON.parse(postsJson);
            if (Array.isArray(posts)) return posts;
            return [];
          } catch {
            return [];
          }
        }
        function savePosts(posts) {
          localStorage.setItem(STORAGE_KEY, JSON.stringify(posts));
        }
        function formatDate(dateStr) {
          const d = new Date(dateStr);
          return d.toLocaleDateString(undefined, {
            year: "numeric",
            month: "short",
            day: "numeric",
          });
        }
        function sanitizeText(text) {
          const div = document.createElement("div");
          div.textContent = text;
          return div.innerHTML;
        }
        function getFirstImage(post) {
          if (post.media) {
            for (const m of post.media) {
              if (m.type.startsWith("image")) return m.data;
            }
          }
          return null;
        }
        function renderBlogList() {
          const posts = getPosts();
          blogList.innerHTML = "";
          if (posts.length === 0) {
            blogList.innerHTML = "<p>No posts published yet.</p>";
            return;
          }
          posts
            .sort((a, b) => new Date(b.date) - new Date(a.date))
            .forEach((post) => {
              const card = document.createElement("div");
              card.className = "post-card";
              card.tabIndex = 0;
              card.setAttribute("role", "button");
              card.setAttribute("aria-pressed", "false");
              const firstImageUrl = getFirstImage(post);
              let imgHtml = "";
              if (firstImageUrl) {
                imgHtml = `<img src="${firstImageUrl}" alt="Post thumbnail" class="post-image" loading="lazy" />`;
              }
              let excerptHtml = `<div class="post-excerpt">${sanitizeText(
                post.content
              ).substring(0, 100)}${
                post.content.length > 100 ? "..." : ""
              }</div>`;
              card.innerHTML = `
            ${imgHtml}
            <h3 class="post-title">${sanitizeText(post.title)}</h3>
            <div class="post-date">${formatDate(post.date)}</div>
            ${excerptHtml}
          `;
              card.addEventListener("click", () => openPost(post.id));
              card.addEventListener("keypress", (e) => {
                if (e.key === "Enter" || e.key === " ") {
                  e.preventDefault();
                  openPost(post.id);
                }
              });
              blogList.appendChild(card);
            });
        }   
        function openPost(id) {
          const posts = getPosts();
          const post = posts.find((p) => p.id === id);
          if (!post) return;
          postViewTitle.textContent = post.title;
          postViewDate.textContent = formatDate(post.date);
          postViewContent.textContent = post.content;
          postViewMedia.innerHTML = "";
          if (post.media && post.media.length > 0) {
            post.media.forEach((m) => {
              if (m.type.startsWith("image")) {
                const img = document.createElement("img");
                img.src = m.data;
                img.alt = post.title + " image";
                img.loading = "lazy";
                postViewMedia.appendChild(img);
              } else if (m.type.startsWith("video")) {
                const video = document.createElement("video");
                video.src = m.data;
                video.controls = true;
                video.title = post.title + " video";
                video.preload = "metadata";
                postViewMedia.appendChild(video);
              }
            });
          }
          blogListSection.style.display = "none";
          adminDashboard.style.display = "none";
          postViewSection.style.display = "block";
        }
        backToListBtn.addEventListener("click", () => {
          postViewSection.style.display = "none";
          if (isAdmin) {
            adminDashboard.style.display = "block";
          } else {
            blogListSection.style.display = "block";
          }
        });
        backToHomeBtn.addEventListener("click", () => {
          isAdmin = false;
          toggleAdminBtn.textContent = "Admin Login";
          adminDashboard.style.display = "none";
          blogListSection.style.display = "block";
          postForm.reset();
          postIdInput.value = "";
          currentMediaArray = [];
          renderMediaPreview();
          currentPwdInput.value = "";
          newPwdInput.value = "";
          confirmPwdInput.value = "";
        });
        function renderAdminPostList() {
          const posts = getPosts();
          adminPostList.innerHTML = "";
          if (posts.length === 0) {
            adminPostList.innerHTML =
              "<p>No blog posts found. Start by adding a new post below.</p>";
            return;
          }
          posts
            .sort((a, b) => new Date(b.date) - new Date(a.date))
            .forEach((post) => {
              const adminPostEl = document.createElement("div");
              adminPostEl.className = "admin-post";
              adminPostEl.innerHTML = `
            <div class="admin-post-title">${sanitizeText(post.title)}</div>
            <div class="admin-post-date">${formatDate(post.date)}</div>
            <div class="admin-btns">
              <button class="edit-btn" title="Edit Post" aria-label="Edit ${sanitizeText(
                post.title
              )}">✏️</button>
              <button class="delete-btn" title="Delete Post" aria-label="Delete ${sanitizeText(
                post.title
              )}">🗑️</button>
            </div>
          `;
              adminPostEl
                .querySelector(".edit-btn")
                .addEventListener("click", () => {
                  fillFormForEdit(post);
                });
              adminPostEl
                .querySelector(".delete-btn")
                .addEventListener("click", () => {
                  deletePost(post.id);
                });
              adminPostList.appendChild(adminPostEl);
            });
        }
        function fillFormForEdit(post) {
          postIdInput.value = post.id;
          postTitleInput.value = post.title;
          postContentInput.value = post.content;
          currentMediaArray = post.media ? [...post.media] : [];
          renderMediaPreview();
          postTitleInput.focus();
        }
        function deletePost(id) {
          if (!confirm("Are you sure you want to delete this post?")) return;
          let posts = getPosts();
          posts = posts.filter((p) => p.id !== id);
          savePosts(posts);
          renderAdminPostList();
          renderBlogList();
          postForm.reset();
          postIdInput.value = "";
          currentMediaArray = [];
          renderMediaPreview();
        }
        function renderMediaPreview() {
          mediaPreview.innerHTML = "";
          currentMediaArray.forEach((m, idx) => {
            const wrapper = document.createElement("div");
            wrapper.className = "media-preview-item";
            let mediaElem;
            if (m.type.startsWith("image")) {
              mediaElem = document.createElement("img");
              mediaElem.src = m.data;
              mediaElem.alt = "Preview Image " + (idx + 1);
              mediaElem.title = "Preview Image";
            } else if (m.type.startsWith("video")) {
              mediaElem = document.createElement("video");
              mediaElem.src = m.data;
              mediaElem.controls = false;
              mediaElem.muted = true;
              mediaElem.title = "Preview Video";
            }
            wrapper.appendChild(mediaElem);
            const removeBtn = document.createElement("button");
            removeBtn.type = "button";
            removeBtn.textContent = "×";
            removeBtn.title = "Remove this media";
            removeBtn.addEventListener("click", () => {
              currentMediaArray.splice(idx, 1);
              renderMediaPreview();
            });
            wrapper.appendChild(removeBtn);
            mediaPreview.appendChild(wrapper);
          });
        }
        function fileToBase64(file) {
          return new Promise((resolve, reject) => {
            const reader = new FileReader();
            reader.onerror = () => {
              reader.abort();
              reject(new Error("Failed to read file."));
            };
            reader.onload = () => {
              resolve({ type: file.type, data: reader.result });
            };
            reader.readAsDataURL(file);
          });
        }
        postMediaInput.addEventListener("change", async (e) => {
          const files = Array.from(e.target.files);
          if (files.length === 0) return;
          let estimatedSize = 0;
          files.forEach((f) => (estimatedSize += f.size));
          if (estimatedSize > 3 * 1024 * 1024) {
            if (
              !confirm(
                "You are uploading large files and it may affect performance or exceed storage limits. Continue?"
              )
            ) {
              postMediaInput.value = "";
              return;
            }
          }
          for (const file of files) {
            try {
              const mediaObj = await fileToBase64(file);
              currentMediaArray.push(mediaObj);
            } catch (error) {
              alert("Error reading file: " + file.name);
            }
          }
          renderMediaPreview();
          postMediaInput.value = "";
        });
        postForm.addEventListener("submit", (e) => {
          e.preventDefault();
          const title = postTitleInput.value.trim();
          const content = postContentInput.value.trim();
          if (!title || !content) {
            alert("Title and content cannot be empty.");
            return;
          }
          const posts = getPosts();
          const existingId = postIdInput.value;
          if (existingId) {
            const index = posts.findIndex((p) => p.id === existingId);
            if (index === -1) {
              alert("Post not found.");
              return;
            }
            posts[index].title = title;
            posts[index].content = content;
            posts[index].date = new Date().toISOString();
            posts[index].media = currentMediaArray;
          } else {
            const newPost = {
              id: "post_" + Date.now() + "_" + Math.floor(Math.random() * 1000),
              title,
              content,
              date: new Date().toISOString(),
              media: currentMediaArray,
            };
            posts.push(newPost);
          }
          savePosts(posts);
          renderAdminPostList();
          renderBlogList();
          postForm.reset();
          postIdInput.value = "";
          currentMediaArray = [];
          renderMediaPreview();
          alert("Post saved successfully!");
        });
        function clearPasswordChangeFields() {
          currentPwdInput.value = "";
          newPwdInput.value = "";
          confirmPwdInput.value = "";
        }
        changePwdBtn.addEventListener("click", () => {
          const currentPwd = currentPwdInput.value;
          const newPwd = newPwdInput.value;
          const confirmPwd = confirmPwdInput.value;
          if (!currentPwd || !newPwd || !confirmPwd) {
            alert("Please fill all password fields.");
            return;
          }
          if (currentPwd !== getAdminPassword()) {
            alert("Current password is incorrect.");
            return;
          }
          if (newPwd !== confirmPwd) {
            alert("New passwords do not match.");
            return;
          }
          if (newPwd.length < 4) {
            alert("New password should be at least 4 characters.");
            return;
          }
          setAdminPassword(newPwd);
          alert(
            "Password changed successfully! Please use the new password on next login."
          );
          clearPasswordChangeFields();
        });
        toggleAdminBtn.addEventListener("click", () => {
          if (!isAdmin) {
            const pwd = prompt("Enter admin password:");
            if (pwd === getAdminPassword()) {
              isAdmin = true;
              toggleAdminBtn.textContent = "Logout Admin";
              blogListSection.style.display = "none";
              postViewSection.style.display = "none";
              adminDashboard.style.display = "block";
              renderAdminPostList();
              postForm.reset();
              postIdInput.value = "";
              currentMediaArray = [];
              renderMediaPreview();
              clearPasswordChangeFields();
            } else {
              alert("Incorrect password!");
            }
          } else {
            isAdmin = false;
            toggleAdminBtn.textContent = "Admin Login";
            adminDashboard.style.display = "none";
            postViewSection.style.display = "none";
            blogListSection.style.display = "block";
            postForm.reset();
            postIdInput.value = "";
            currentMediaArray = [];
            renderMediaPreview();
            clearPasswordChangeFields();
          }
        });      
        initAdminPassword();
        renderBlogList();
      })();
    </script>
  </body>
</html>
