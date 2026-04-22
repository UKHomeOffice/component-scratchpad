# component-scratchpad
A markdown-style syntax to describe gov.uk components and generate html code to copy into non-live and non-public projects

Original file and repo created 2nd March 2026 by Ian Smith.

Use this tool to quickly create html content for pages based on gov.uk components.

Instead of writing html code, describe each component using (relatively) plain language called scratchdown.

Each new component description must start with ##. 

The format is: `##component_name | Label or text | Further options`

Returns are permitted, allowing multiple paragraphs of content e.g.
`##p | This is part of a simple paragraph of text.

And so is this.`

Components with repeating elements, like the summary list, table or check answers components work like this:
`##component_name | Label or text | column value:column value:column value`

Provide basic layout using Row and Column. Define column width using the format 'Column|width' e.g. Column|100 will be full width, Column|50 will be 50%.

Once you're happy with the html, use the control below to copy it to the clipboard, then you can add it to your prototype.

**Supported components**

| Component     | Syntax                                                                                                         | Notes                                                                                                                    |
| ------------- | -------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| h1            | h1\|Text here\|Caption                                                                                                | Caption is optional                                                                                                                         |
| h2            | h2\|Text here\|Caption                                                                                                | Caption is optional                                                                                                                       |
| h3            | h3\|Text here\|Caption                                                                                                | Caption is optional                                                                                                                        |
| h4            | h4\|Text here                                                                                                  |                                                                                                                          |
| p             | p\|Text here                                                                                                   | Can include styling and links                                                                                            |
| a             | a\|Text here\|href                                                                                             | Href can be full or relative                                                                                             |
| input box     | input\|Label here (Hint text here)                                                                               | Hint text is optional, defined within brackets                                                                      |
| Textarea box  | textarea\|Label here (Hint text here)\|Rows                                                                           | Hint text is optional, defined within brackets.  Number of rows is optional, defaults to 3.                                                                       |
| date input    | date\|Label here (Hint text here)                                                                                              | Hint text is optional, defined within brackets.                                                                                                                          |
| radio buttons | radios\|Label here (Hint text here) \|Radio 1\|Radio 2\|...final radio                                            | Hint text is optional, defined within brackets                                                                         |
| checkboxes    | checkboxes\|Label here (Hint text here) \|checkbox 1\|checkbox 2\|...final checkbox                                              | Hint text is optional, defined within brackets                                                                                                                               |
| select        | select\|Label here (Hint text here) \|option 1\|option 2\|...final option<br>                                                    | Hint text is optional, defined within brackets                                                                                                                             |
| go back link       | goback\|Text here                                                                                              | Text is optional, defaults to 'Back'                                                                                     |
| button        | button\|Label here\|font colour\|background colour                                                             | Colours are optional, defaults to gov.uk primary button                                                                  |
| primary button      | button_p\|Label here                                                                                             | gov.uk primary button                                                                                                    |
| secondary button      | button_s\|Label here                                                                                             | gov.uk secondary button                                                                                                  |
| details       | details\|Title here\|content                                                                                   |                                                                                                                          |
| inset         | inset\|Text here                                                                                               |                                                                                                                          |
| warning       | warning\|Text here                                                                                             |                                                                                                                          |
| panel         | panel\|Title here\|Description                                                                                 |                                                                                                                          |
| tag           | tag\|Text here                                                                                                 |                                                                                                                          |
| bullet list         | listb\|item:item:item:item\|spaced                                                                             | Takes list items first. 'spaced' is optional, for bigger spacing between items                            |
| number list         | listn\|item:item:item:item\|spaced                                                                             | Takes list items first. 'spaced' is optional, for bigger spacing between items                            |
| summarylist   | summarylist\|Label\|key1:value1\|key2:value2\|...final key:final value                                         | Repeat as required                                                                                                       |
| table         | table\|Label\|row1value1:row1value2:row1value3... row1value10\|row2value1:row2value2:row2value3... row2value10 | Repeat as required                                                                                                       |
| table with header  | tablewheader\|Label\|row1value1:row1value2:row1value3... row1value10\|row2value1:row2value2:row2value3... row2value10 | As per table, but first row is a header                                                                                                      |
| check answers | checkanswers\|Label\|key1:value1:link1\|key2:value2:link2\|...final key:final value:final link                 | Repeat as required. If link is left blank, it defaults to 'Change'                                                       |
| task list | tasklist\|Label\|Task name1:URL:status\|Task name2:URL:status\|...final task name: url:status                 | Repeat as required. Status of 'Completed' is shown without a tag. Status of 'Cannot be started' removes link from task name.                                                    |
| tabs | tabs\|Label\|Tab one\|Tab two\|Tab three\|Tab four\|Tab five                 | Add as many tabs as you wish. Tab names should be unique. Stand-in content is provided for each tab.                                                    |
| row           | row                                                                                                            | Use 'End Row' before defining a new row                                                                                  |
| column        | column\|width                                                                                                  | Width is optional, defaults to 100%. Columns can only exist within a row. Use 'End Column' before defining a new column. |
| hr            | hr                                                                                                             |                                                                                                                          |
| spacer        | spacer\|height\|background color                                                                               | Provides an empty div for cheeky padding. Colour is optional, defaults to transparent                                    |
| comment       | comment\|Text here                                                                                             | Appears as a comment in the html, not visible to end users                                                               |


**Conditional reveals**
Create a conditional reveal from a radio button or checkbox by specifying an ID which you can then attach to a _hidden\_component_ e.g.  
  
`##radios|Where do you live?|At home|At University|In a box:size1 `
`##hidden_input|How big is the box?|size1`  
  
will reveal the input box defined as 'size1' when the radio button 'In a box' is clicked.  
  
Add more than one component with the same id and they will all be revealed.  
  
Add different ids to different radios and checkboxes to reveal different components. e.g.    
`##radios|Where do you live?|At home:home1|At University:uni1|In a box:box1`  \
`##hidden_p|Who do you live with?|home1 `  \
`##hidden_checkbox|Mum|home1 `  \
`##hidden_checkbox|Dad|home1 `  \
`##hidden_checkbox|Carers|home1 `  \
`##hidden_date|When did you start?|uni1`   \
`##hidden_input|How big is the box?(Tell us roughly)|box1    `  
`##hidden_select|How rough is that?(Be honest)||Slightly|Very|Extremely|box1`

  
Supported components:  
`hidden_input, hidden_textarea, hidden_radio, hidden_checkbox, hidden_date, hidden_select, hidden_p, hidden_button_p, hidden_button_s, hidden_h2, hidden_h3`  
  
Important note: conditional reveals only work when _all_ the IDs and hidden components have been specified. If its not working check you have at least one hidden component for every ID specified in the radio or checkox components.

**Error summaries and error states**  
Put an input component into an error state by appending 'Error:error message' to the component label e.g.  
  
`##input|What is your name? (Include any middle names) Error: Please enter your full name`
`##date|When did you arrive (Give the exact date) Error: Tell us when you arrived`  
  
will display the component label, the hint, will create an error summary box at the top of the page and link to each component in error state.


