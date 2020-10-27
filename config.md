<!-- RSS settings -->
<!--
@def website_title = "Fredrik Ekre"
@def website_descr = "Example website using Franklin"
@def website_url   = "http://localhost:8000/"
-->
+++
# Exclude everything that is not explicitly in include
_include = ["_assets/", "_css/", "_libs/", "_layout/", "index.html", "404.md", "posts/", "about/"]
_exclude = if get(ENV, "FRANKLIN_OPTIMIZE", nothing) == "true"
        # ["_libs/highlight/highlight.pack.js"]
        String[]
    else
        String[]
    end
ignore = [setdiff([isfile(x) ? x : x * "/" for x in readdir()], _include); _exclude]
+++



<!-- Theme specific options -->
<!-- @def title = "Fredrik Ekre" -->
@def sitename = "Fredrik Ekre"
@def author.name = "Fredrik Ekre"

<!-- Social icons -->
@def social = (
        github = "https://github.com/fredrikekre",
    )

<!-- Logo -->
@def logo.mark = "\$"
@def logo.text = "cd /home/fredrik"

<!-- Menu -->
@def menu = [
        (name = "Posts", url = "/posts/"),
        #(name = "Research", url = "/research/"),
        (name = "About", url = "/about/"),
    ]


\newcommand{\codetoggle}[1]{
~~~
<div class="toggle-code-wrap" style="position:relative">
<input id="{{ unique_id new }}" type="checkbox" checked=true">
<label for="{{ unique_id }}" class="switch">
  <span class="slider round"></span>
</label>
<div class="toggle-code-new">
~~~
`````julia
!#1
`````
~~~
</div>
<div class="toggle-code-old">
~~~
`````julia-old
!#1
`````
~~~
</div>
</div>
~~~
}