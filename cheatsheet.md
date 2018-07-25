# master template in hugo
In hugo master template name is `baseof.html` which located in `layouts/_default/baseof.html` .  

# block in master template 
{{< highlight go-html-template>}}
{{ block "main" . }}
default content here
{{ end }}
{{</ highlight >}}

# using block in other template
{{< highlight go-html-template>}}
{{ define "main" }}
	<h2>Different page</h2>
{{ end }}
{{</ highlight >}}

# Adding scss in hugo 

make file inside 	`assets/scss/style.scss` file       

Inside  html file 

{{< highlight go-html-template >}}
{{ $sass := resources.Get "scss/style.scss" }}
{{ $style := $sass | resources.ToCSS }}
<link rel="stylesheet" href="{{ $style.Permalink }}" />
{{</ highlight >}}

# Adding sourcemap and minify scss in hugo 
{{< highlight go-html-template >}}
{{ $sass := resources.Get "scss/style.scss" }}
{{ $style := $sass | resources.ToCSS (dict "outputStyle" "compressed" "enableSourceMap" true) }}
<link rel="stylesheet" href="{{ $style.Permalink }}" />
{{</ highlight >}}

# Home page path in hugo
`layouts/index.html`  

# adding static content like html css in hugo 
bootstrap location `static/css/bootstrap.min.css`

{{< highlight html>}}
<link rel='stylesheet' href='{{.Site.BaseURL}}css/bootstrap.min.css'/>
<!-- or -->
<link rel='stylesheet' href='{{"css/bootstrap.min.css" | relURL}}'/>
{{</ highlight >}}

# generating syntax highlighter for hugo 

{{< highlight bash>}}
hugo gen chromastyles --style=monokai > static/css/syntax.css
{{</ highlight >}}
Run `hugo gen chromastyles -h` for more     

# highlighting in hugo  

{{< highlight go-html-template >}}
	{{< highlight go "linenos=table,hl_lines=8 15-17,linenostart=199" >}}
	// ... code
	{{< / highlight >}}
	// or 
	{{< highlight go >}}
	// ... code
	{{< / highlight >}}
{{</ highlight >}}

# outputting rss and json 
{{< highlight php>}}
[outputs]
home = [ "HTML", "RSS", "JSON"]
{{</ highlight >}}

# how layout nested layout works 

I have set taxonomy library in `config.toml` file 
{{< highlight toml>}}
[taxonomies]
  library = "libraries"
{{</ highlight >}}

* for listing all the folder inside `content/libraries/` I wrote template inside `layouts/library/list.html`    
Here if we want to change folder name title we have to make a file `content/libraries/_index.md` file with front matter inside     
{{< highlight yaml>}}
---
title: "php essential"
date: 2018-07-24T00:29:26+06:00
weight: 1
draft: false
---
{{</ highlight >}}
* for listing all the file inside `content/libraries/php` I wrote template inside `layouts/library/php.html`   
Here `layouts/library/php.html`  is not a common layout naming format So in your file frontmatter we have to mention our layout   

{{< highlight toml>}}
+++
layout= "php"
+++
{{</ highlight >}}























