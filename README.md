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

**UPDATE**: This appears to be a browser-specific issue.  Safari v9.0.2 seems to render the nested tabs correctly, while Chrome v47 and Firefox v43 do not.

## Tabs Are Rendered Extremely Wide

Tabs in code snippets are rendered extremely wide on npmjs.com.  This here is one single tab:

```js
{
	"code": 0,
	"location": "http://mycompany.com/usermanager/login.php?return="
}
```

Because the npmjs.com page content is locked at 740px width, it would be highly recommended to reduce the tab width, to about half of what it is.

## Incorrect Nested List Indents

Nested lists don't seem to indent properly, especially when mixing numbered and bullet lists:

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

Table content should align left unless explicitly set otherwise.  On npmjs.com it is all centered by default:

| Header 1 | Header 2 | Header 3 |
|----------|----------|----------|
| Sample 1 | Sample 2 | Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. |
| Sample 1 | Sample 2 | Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. |
| Sample 1 | Sample 2 | Lorem ipsum dolor sit amet, consectetur adipisicing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. |

Note: I am specifically referring to the table content, not the headers.

## ASCII art is misaligned in text blocks

The following is a simple ASCII box with text inside:

```
┌───────────────────────────────────────────────┐
│ The quick brown fox jumped over the lazy dog. │
└───────────────────────────────────────────────┘
```

And this is an ASCII table with several rows and columns:

```
┌──────────┬────────────────┬───────────────────┬───────────────┐
│ Username │ Full Name      │ Email Address     │ Status        │
├──────────┼────────────────┼───────────────────┼───────────────┤
│ jhuckaby │ Joseph Huckaby │ jhuckaby@test.com │ Administrator │
│ tsmith   │ Tom Smith      │ smith@email.com   │ Active        │
│ dcook    │ David Cook     │ dcook@hotmail.com │ Suspended     │
└──────────┴────────────────┴───────────────────┴───────────────┘
```

Both of these appear garbled on npmjs.com, with everything misaligned.  I believe the font being used for text blocks is not truly monospace, and several of the ASCII art characters are actually double-width, when they should be single-width.

Specifically, I believe the `─` character is being rendered double-width, and the `├` character is also misaligned.

These boxes and tables appear fine [on GitHub](https://github.com/jhuckaby/npm-markdown-bugs), and in various text editors and terminals I have tried.

## Test

Test.

