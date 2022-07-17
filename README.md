# html_copy_code_to_clipboard
 
[Source](https://www.roboleary.net/2022/01/13/copy-code-to-clipboard-blog.html)

```html
<!DOCTYPE html>
<html>

    <head>
        <link rel="stylesheet" type="text/css"
            href="https://cdnjs.cloudflare.com/ajax/libs/prism/1.22.0/themes/prism-tomorrow.min.css" />
        <style>
            *,
            *:before,
            *:after {
                box-sizing: border-box;
            }

            pre[class*="language-"] {
                position: relative;
                overflow: auto;
                margin: 5px 0;
                padding: 1.75rem 0 1.75rem 1rem;
                border-radius: 10px;
            }

            button {
                position: absolute;
                top: 5px;
                right: 5px;

                font-size: .9rem;
                padding: .15rem;
                background-color: #828282;
                color: 1e1e1e;
                border: ridge 1px #7b7b7c;
                border-radius: 5px;
                text-shadow: #c4c4c4 0 0 2px;
            }

            button:hover {
                cursor: pointer;
                background-color: #bcbabb;
            }

            main {
                display: grid;
                max-width: 600px;
                margin: 20px auto;
            }


            h1 {
                font-size: 1.3rem;
            }
        </style>
    </head>

    <body>

        <main>
            <pre><code class="language-css">...</code></pre>
            <pre><code class="language-html">&lt;...&gt;</code></pre>
            <pre><code class="language-javascript">...</code></pre>
        </main>
        
        <script>
            const copyButtonLabel = "Copy Code";

            // you can use a class selector instead if you, or the syntax highlighting library adds one to the 'pre'. 
            let blocks = document.querySelectorAll("pre");

            blocks.forEach((block) => {
                // only add button if browser supports Clipboard API
                if (navigator.clipboard) {
                    let button = document.createElement("button");
                    button.innerText = copyButtonLabel;
                    button.addEventListener("click", copyCode);
                    block.appendChild(button);
                }
            });

            async function copyCode(event) {
                const button = event.srcElement;
                const pre = button.parentElement;
                let code = pre.querySelector("code");
                let text = code.innerText;
                await navigator.clipboard.writeText(text);

                button.innerText = "Code Copied";

                setTimeout(() => {
                    button.innerText = copyButtonLabel;
                }, 1000)
            }
        </script>
        <script src="https://cdnjs.cloudflare.com/ajax/libs/prism/1.26.0/prism.min.js"></script>
    </body>

</html>
```

---

```
Copyright 2022 M. Fadli Zein
```