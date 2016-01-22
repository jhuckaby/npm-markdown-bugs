# NPM Markdown Bugs

Here are a few Markdown bugs I've found while viewing READMEs [on npmjs.com](https://npmjs.com/npm-markdown-bugs).  For comparison, all of these view fine [on GitHub](https://github.com/jhuckaby/npm-markdown-bugs) using the same Markdown syntax.

## Incorrect Code Indents

When indenting code using real tabs (not spaces), npmjs.com renders it with very odd spacing:

```js
var server = new PixlServer({
	
	__name: 'MyServer',
	__version: "1.0",
	
	config: {
		"log_dir": "/var/log",
		"debug_level": 9,
		
		"Storage": {
			"engine": "File",
			"File": {
				"base_dir": "/var/data/myserver"
			}
		},
		
		"WebServer": {
			"http_port": 80,
			"http_htdocs_dir": "/var/www/html"
		},
		
		"API": {
			"base_uri": "/api"
		},
		
		"User": {
			"free_accounts": 0,
			"sort_global_users": 1
		}
	},
	
	components: [
		require('pixl-server-storage'),
		require('pixl-server-web'),
		require('pixl-server-api'),
		require('pixl-server-user')
	]
	
});
```

Basically, anything nested more than one tab deep is collapsed to the left side.

## Tabs Are Rendered Extremely Wide

Tabs in code snippets are rendered with an extremely wide margins.  This here is one single tab:

```js
{
	"code": 0,
	"location": "http://mycompany.com/usermanager/login.php?return="
}
```

Because the npmjs.com page content is locked at 740px width, it would be highly recommended to reduce the tab width, to about half of what it is.

## Incorrect Nested List Indents

Nested lists don't seem to indent properly, when mixing numbered and bullet lists:

1. This is an outer list item.
2. This is an outer list item.
3. This is an outer list item.
	* This is a nested bullet list item.
	* This is a nested bullet list item.
	* This is a nested bullet list item.

## No Space After Lists

Nested lists seem to have a spacing issue below them:

1. This is an outer list item.
2. This is an outer list item.
3. This is an outer list item.
	* This is a nested bullet list item.
	* This is a nested bullet list item.
	* This is a nested bullet list item.

Here is text below a list.  On npmjs.com this text is crammed up against the list bottom.

## Tables Centered By Default

Table columns should align left.  On npmjs.com they are all centered:

| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Sample 1 | Sample 2 | Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. |
| Sample 1 | Sample 2 | Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. |
| Sample 1 | Sample 2 | Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. |

