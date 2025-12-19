# Minifb


html

Copy code
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <title>Mini Facebook Clone</title>
    <style>
        body { font-family: Arial, sans-serif; margin: 20px; }
        .post { border: 1px solid #ddd; padding: 10px; margin: 10px 0; }
        .comment { margin-left: 20px; font-size: 0.9em; }
        #new-post { width: 100%; padding: 10px; }
    </style>
</head>
<body>
    <h1>Mini Red Social</h1>
    <textarea id="new-post" placeholder="Escribe una publicación..."></textarea>
    <button onclick="addPost()">Publicar</button>
    <div id="feed"></div>

    <script>
        let posts = [];

        function addPost() {
            const content = document.getElementById('new-post').value;
            if (content.trim()) {
                posts.push({ content, comments: [] });
                document.getElementById('new-post').value = '';
                renderFeed();
            }
        }

        function addComment(index) {
            const commentText = prompt('Escribe un comentario:');
            if (commentText) {
                posts[index].comments.push(commentText);
                renderFeed();
            }
        }

        function renderFeed() {
            const feed = document.getElementById('feed');
            feed.innerHTML = '';
            posts.forEach((post, i) => {
                feed.innerHTML += `
                    <div class="post">
                        <p>${post.content}</p>
                        <button onclick="addComment(${i})">Comentar</button>
                        ${post.comments.map(c => `<div class="comment">${c}</div>`).join('')}
                    </div>
                `;
            });
        }
    </script>
</body>
</html>
