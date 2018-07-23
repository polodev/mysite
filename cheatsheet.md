# master template in hugo
In hugo master template name is `baseof.html` which located in `layouts/_default/baseof.html` .  

# block in master template 
~~~html
{{ block "main" . }}
default content here
{{ end }}
~~~

# using block in other template
~~~html
{{ define "main" }}
	<h2>Different page</h2>
{{ end }}
~~~

# Adding scss in hugo 

make file inside 	`assets/scss/style.scss` file       

inside  html file 

~~~html
{{ $sass := resources.Get "scss/style.scss" }}
{{ $style := $sass | resources.ToCSS }}
<link rel="stylesheet" href="{{ $style.Permalink }}" />
~~~
# Adding sourcemap and minify scss in hugo 
~~~html
{{ $sass := resources.Get "scss/style.scss" }}
{{ $style := $sass | resources.ToCSS (dict "outputStyle" "compressed" "enableSourceMap" true) }}
<link rel="stylesheet" href="{{ $style.Permalink }}" />
~~~

# Home page path in hugo
`layouts/index.html`  

# adding static content like html css in hugo 
bootstrap location `static/css/bootstrap.min.css`
~~~html
<link rel='stylesheet' href='{{.Site.BaseURL}}css/bootstrap.min.css'/>
~~~

# generating syntax highlighter for hugo 

~~~html
hugo gen chromastyles --style=monokai > static/css/syntax.css
~~~
Run `hugo gen chromastyles -h` for more 

highlighting in sql  

~~~
{{< highlight go "linenos=table,hl_lines=8 15-17,linenostart=199" >}}
// ... code
{{< / highlight >}}
// or 
{{< highlight go >}}
// ... code
{{< / highlight >}}
~~~





















