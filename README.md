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

## Usage
Run `python3 <path to script>/ssg.py [options] --languages= --translations-dir= --templates= --templates-dir= --output-dir=`

Run `python3 <path to script>/ssg.py -h` or `python3 <path to script>/ssg.py --help` to display the help message.

### Arguments
- `-h`, `--help` : displays the help message.
- (*)`--languages` : Comma-separated languages to generate the files for (e.g. 'en,fr').
- (*)`--translations-dir` : Path to the directory containing the JSON files.
- (*)`--templates` : Comma-separated names of the templates to geenrate the files for (e.g. 'index,about').
- (*)`--templates-dir` : Path to the directory containing the HTML files.
- (*)`--output-dir` : Path to the directory into which the folders and files will be created or updated.

/!\ Arguments marked with (*) are mandatory.

### Exemple
Current directory is:
```
directory/
- assets/
  - ssg.py
  - templates/
    - index.html
    - other-page.html
  - translations/
    - en.json
    - fr.json
```

Running `python3 ./assets/ssg.py --languages='en,fr' --translations-dir='./assets/translations/' --templates='index,other-page' --templates-dir='./assets/templates/' --output-dir='./output'` will give you this:
```
directory/
- assets/ (same as before)
- output/
  - en/
    - index.html
    - other-page.html
  - fr/
    - index.html
    - other-page.html
```

## Copyright and licensing
This work has no copyright and is free of any license.
