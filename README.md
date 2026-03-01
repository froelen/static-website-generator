# froelen's Static Website Generator

## What is an SSG?
An SSG is a tool that can **automatically** generate webpages based on templates and various options.

Mine is oriented towards **multilingual** websites.

It creates the different pages from a language and a template list, under the different `<language>/` directories.

## How does it work?
When using the tool, you must specify the languages and templates that will be used, their respective directories, and the "root" (output) directory.

The language files are of the JSON format, using the following structure:
```JSON
{
  "index":{
    "variableName":"Whatever content you want.",
    "variable2":"It can include HTML tags <em>like so<em>."
  },
  "other-page":{
    "variableName":"Variables can have the same name if they're under different templates."
  }
}
```

The variables are set in the HTML file with a double pair of curly brackets. E.g., in `index.html`:
```HTML
<html>
  <head>...</head>
  <body>
    <p>{{variableName}}</p>
    <p>{{variable2}}</p>
  </body>
</html>
```

## Copyright and licensing
This work has no copyright and is free of any license.
