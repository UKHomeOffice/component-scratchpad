# component-scratchpad
A markdown-style syntax to describe gov.uk components and generate html code to copy into non-live and non-public projects

Original created 2nd March 2026 by Ian Smith.

Use this tool to quickly create html content for pages based on gov.uk components.

Instead of writing html code, users describe each component using (relatively) plain language.

Each new component description must start with ##. The format is:
##component_name | Label or text | Further options

Returns are allowed so you can write multiple paragraphs of content, e.g.
##p | This is simple paragraph of text.

And so is this.

Components with repeating elements, like the summary list, table or check answers components work like this:
##component_name | Label or text | column value:column value:column value

You can provide basic layout using Row and Column. You can define column width using the format 'Column|width' e.g. Column|100 will be full width, Column|50 will be 50%.

Once you're happy with the html, use the control below to copy it to the clipboard, then you can add it to your prototype.

For supported components (last updated: 2nd Mar 2026), see below.


====================================================
Component	Syntax	Notes

h1	h1|Text here	

h2	h2|Text here	

h3	h3|Text here	

h4	h4|Text here	

p	p|Text here	Can include styling and links

a	a|Text here|href	Href can be full or relative

input box	input|Label here:Hint text here	Hint text is optional, defined after a colon (&colon;)

Textarea box	textarea|Label here:Hint text here	Hint text is optional, defined after a colon (&colon;)

date input	date|Label here	

radio buttons	radios|Label here:Hint text here|Radio 1|Radio 2|...final radio	Hint text is optional, defined after a colon (&colon;)

checkboxes	checkboxes|Label here:Hint text here|checkbox 1|checkbox 2|...final checkbox	Hint text is optional, defined after a colon (&colon;)

select	select|Label here|option 1|option 2|...final option

goback	goback|Text here	Text is optional, defaults to 'Back'

button	button|Label here|font colour|background colour	Colours are optional, defaults to gov.uk primary button

button_p	button|Label here	gov.uk primary button

button_s	button|Label here	gov.uk secondary button

details	details|Title here|content	

inset	inset|Text here	

warning	warning|Text here	

panel	panel|Title here|Description	

tag	tag|Text here	

listb	listb|item:item:item:item|spaced	Bulleted list, takes list items first. 'spaced' is optional, for bigger spacing between items

listn	listn|item:item:item:item|spaced	Numbered list, takes list items first. 'spaced' is optional, for bigger spacing between items

summarylist	summarylist|Label|key1:value1|key2:value2|...final key:final value	Repeat as required

table	table|Label|row1value1:row1value2:row1value3... row1value10|row2value1:row2value2:row2value3... row2value10	Repeat as required

tablewheader	tablewheader|row1value1:row1value2 etc.	As per table but first row is a header

checkanswers	checkanswers|Label|key1:value1:link1|key2:value2:link2|...final key:final value:final link	Repeat as required. If link is left blank, it defaults to 'Change'

row	row	Use 'End Row' before defining a new row

column	column|width	Width is optional, defaults to 100%. Columns can only exist within a row. Use 'End Column' before defining a new column.

hr	hr	

spacer	spacer|height|background color	Provides an empty div for cheeky padding. Colour is optional, defaults to transparent

comment	comment|Text here	Appears as a comment in the html, not visible to end users





