# Realtime syntax highlighter

This is a realtime syntax highlighter, which can use any syntax highlighter engine. It works by making the original code element 
transparent (invisible), and using a visible shadow element which holds the syntax highlighted version of the code.

See the [example](https://czirkoszoltan.github.io/realtime-syntaxhighlighter/).


## Internals

The expected markup looks like this:

```html
<pre>
    <code class="language-cpp editable">
        some_code();
    </code>
<pre>
```

After the DOM manipulation:

```html
<div class="realtime-editing-wrapper">
    <pre class="realtime-editing-shadow">
        <code class="editable language-cpp">
            {{{shadow code element}}}
        </code>
    </pre>
    <pre class="realtime-editing-editable">
        <code spellcheck="false" contenteditable="true">
            {{{original code element}}}
        </code>
    </pre>
</div>
```

The user edits the `<code>` element in the editable `<pre>`. An event handler bound to the `input` event of this element copies the 
edited code to the shadow element. There it is highlighted after each keypress. The shadow element is visible and determines the
size of the wrapper `<div>`; the editable element is invisible and absolutely positioned: it floats above the shadow.


## Files

- `index.html`: Basic example
- `realtime-syntaxhighlight.js`: JS code which does the job
- `realtime-syntaxhighlight.css`: minimal CSS to make it work
- `prism.js`: unmodified version of the [Prism library](https://prismjs.com/)
- `prism.css`: slightly modified version of the default Prism theme


## Configuration, browser support

See the source files. This is a proof of concept project only, not a widely configurable library.
