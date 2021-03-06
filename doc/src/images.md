# Image Elements

Ornate extends the use of standard Markdown image elements to non-image objects. These are not limited to external files, they can be included directly in the page depending on the [URI scheme](uris.md).

## Table of Contents {#toctree}

`toctree` URIs represent the generated Table of Contents. They can be used in image elements or parts of the theme configuration. URIs are of the form `toctree:key=value,key=value,...` with case-insentive keys. The following keys are supported:

- `maxLevel`: The maximum nesting level to show in the TOC. Pages have level 0, heading elements have levels 1 to 6. When unset, this defaults to the configuration setting `global.tocMaxLevel`.
- `mergeFirst`: Whether to merge the page and the first heading (`true` or `false`). Usually pages have a single level-1 heading at the top and no separate title, so it does not make sense to show them in the TOC. With `mergeFirst=true` the first heading is shown as the title but the link goes to the page. When unset, this defaults to the configuration setting `global.tocMergeFirst`.
- `local`: Whether to include only TOC entries from the current page. Defaults to `false`.
- `focusMaxLevel`: A separate maximum nesting level for the current page. When unset, this is the same as `maxLevel`.

A `toctree` image elements may only be used in a paragraph of its own. It cannot be used as an inline element. Title and text of the element are ignored.

For example, this image element references the TOC of the current page:

```markdown
![](toctree:maxLevel=6,local=true,mergeFirst=false)
```

It is rendered as:

![](toctree:maxLevel=6,local=true,mergeFirst=false)

## Configuration Values {#config}

`config` URIs can be used in image elements. They expand to strings from the page configuration. Title and text of the element are ignored.

Example:

```markdown
The current theme is ![](config:global.theme).
```

It is rendered as:

The current theme is ![](config:global.theme).

## Theme-Specific URI Schemes

The [default theme](default-theme.md) supports the `foundation-icon` and `font-awesome` schemes to render images from the [Foundation Icon Fonts 3](http://zurb.com/playground/foundation-icon-fonts-3) and [Font Awesome](http://fontawesome.io/icons/). The scheme-specific part of the URI is the image name. Only the canonical names are supported, no aliases.

While such images *can* be used like any other image in a source document, this is not recommended because they would not be rendered correctly with different themes. Theme-specific URI schemes are intended to be used in Markdown snippets that are part of the theme configuration, for example in the navigation bar links as defined in the default configuration:

```yaml src=../../core/src/main/resources/ornate-reference.conf#--doc-navlinks
```
