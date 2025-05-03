
# how to implement tinymce (description generator) in laravel from npm 

```bash
npm install tinymce
```



![Logo](https://camo.githubusercontent.com/409f2cec2b7e7c7410ea4a2e15c64d2252deaeb27c8cc7a80e1190ad342b6b33/68747470733a2f2f7777772e74696e792e636c6f75642f73746f726167652f6769746875622d726561646d652d696d616765732f74696e796d63652d656469746f722d36782e706e67)


# implementation

open file ``resources/js/app.js`` and paste this code

```bash 
import 'tinymce/tinymce';
import 'tinymce/skins/ui/oxide/skin.min.css';
import 'tinymce/skins/content/default/content.min.css';
import 'tinymce/icons/default/icons';
import 'tinymce/themes/silver/theme';
import 'tinymce/models/dom/model';
import 'tinymce/plugins/code';
import 'tinymce/plugins/table';
import 'tinymce/plugins/lists';

// TinyMCE initialize karne ke liye
window.addEventListener('DOMContentLoaded', () => {
    tinymce.init({
        selector: 'textarea#myeditorinstance', // Aapka textarea ID
        plugins: 'code table lists', // Plugins jo aap use karna chahte hain
        toolbar: 'undo redo | blocks | bold italic | alignleft aligncenter alignright | indent outdent | bullist numlist | code | table', // Toolbar options
        skin: false, // Custom skin disable karne ke liye (optional)
        content_css: false // Custom content CSS disable karne ke liye (optional)
    });
});
```
then run cmds

```bash
npm run build
```
```bash
npm run dev
```

# And finally use this

```bash
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>TinyMCE in Laravel 10</title>
    @vite(['resources/js/app.js', 'resources/css/app.css'])
</head>
<body>
    <h1>TinyMCE Editor</h1>
    <form method="POST" action="/save-content">
        @csrf
        <textarea id="myeditorinstance" name="content"></textarea>
        <button type="submit">Save</button>
    </form>
</body>
</html>
```
