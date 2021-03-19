## Usage
**NOTE:** In Windows or Linux use <kbd>ctrl</kbd> instead of <kbd>⌘</kbd>

* <kbd>⌘ + enter</kbd> or <kbd>⌘ + i</kbd>: new task

* <kbd>⌘ + d</kbd>: toggle task as completed.

* <kbd>ctrl + c</kbd>: toggle task as cancelled on Mac. <kbd>alt + c</kbd> on Windows/Linux.

* <kbd>⌘ + shift + a</kbd> will archive the done tasks, by removing them from your list and appending them to the bottom of the file under Archive project

* <kbd>⌘ + shift + o</kbd> will archive in Org-Mode style, removing the entire subtree after cursor and appending it to new file next to original one, e.g. if original is `filename.TODO` then new would be `filename_archive.TODO`

* <kbd>⌘ + shift + u</kbd> will open the url under the cursor in your default browser, other than http(s) schemes must be enclosed within `<>`, e.g. `<skype:nickname>`

* Anything with colon at the end of the line is a project title, you can also nest projects by indenting them. 

* You can write plain text as notes or descriptions wherever you want. Use `_` or `*` for italic and bold just like in Markdown.

* You can add tags using **`@`** sign. To filter by tag, right click on a tag and then _Filter by tags under cursors_

* You can navigate tags in current document via <kbd>⌘+shift+r</kbd>.

* Type `---` and then <kbd>tab</kbd> to insert a separator.

* Completion rules (<kbd>ctrl+space</kbd> or <kbd>alt+/</kbd> to see list of them):  

- type `t`, press <kbd>tab</kbd> — it’ll become `@today` — this one is highlighted differently than other tags;
- `c`, <kbd>tab</kbd> — `@critical`;
- `h`, <kbd>tab</kbd> — `@high`;
- `l`, <kbd>tab</kbd> — `@low`;
- `s`, <kbd>tab</kbd> — `@started` — press <kbd>tab</kbd> again and current date will be inserted, when you’ll complete or cancel a task with such tag, you’ll know how many time has passed since start; if you have to change done/cancelled/started time, then you can recalculate the time spent on task by pressing <kbd>tab</kbd> while cursor is placed on a tag;
- `tg`, <kbd>tab</kbd>, <kbd>tab</kbd> work in the same manner as `s`, but inserts `@toggle(current date)` — so you can pause and resume to get more correct result when done/cancel; each toggle tag is either pause or resume depending on its place in sequence;
- `cr`, <kbd>tab</kbd>, <kbd>tab</kbd> — `@created(current date)` (<kbd>⌘ + shift + enter</kbd> creates a new task with this tag);
- `d`, <kbd>tab</kbd> — `@due( )`  
  If you press <kbd>tab</kbd> again, it’ll insert current date, same for `@due( 0)`.  
  You can type short date (similar to [OrgMode’s date prompt](http://orgmode.org/manual/The-date_002ftime-prompt.html), but not the same) and then press <kbd>tab</kbd> to expand it into default format.  
  Short date should be __`@due(year-month-day hour:minute)`__  
  Dot can be used instead of hyphen, but should be consistent _`year.month.day`_

    - year, month, minute, hour can be omitted:

        <table>
         <tr>
          <th>  Notation    </th><th>   Meaning     </th>
         </tr>
         <tr>
          <td>  <code>@due(1)</code>    </td>
          <td>  1st day of next month always    </td>
         </tr>
         <tr>
          <td>  <code>@due(--1)</code>    </td>
          <td>  1st day of current month always    </td>
         </tr>
         <tr>
          <td>  <code>@due(5)</code>    </td>
          <td>  5th day of current month (or next month if current day is 5th or older) </td>
         </tr>
         <tr>
          <td>  <code>@due(2-3)</code>  </td>
          <td>  February 3rd of current year or next one    </td>
         </tr>
         <tr>
          <td>  <code>@due(31 23:)</code>   </td>
          <td>  31st day of current/next month at 23 hours and minutes are equal to current moment  </td>
         </tr>
         <tr>
          <td>  <code>@due(16.1.1 1:1)</code>   </td>
          <td>  January 1st of 2016 at 01:01    <code>@due(16-01-01 01:01)</code>  </td>
         </tr>
        </table>

    - relative period of time starts with a plus sign or two  
      __`+[+][number][DdWw][h:m]`__ — number is optional as well as letter `d` for days or letter `w` for weeks.

        <table>
         <tr>
          <th>  Notation    </th><th>   Meaning     </th>
         </tr>
         <tr>
          <td>  <code>@due(+)</code>    </td>
          <td>  tomorrow as well as <code>@due( +1)</code> or <code>@due( +1d)</code></td>
         </tr>
         <tr>
          <td>  <code>@due(+w)</code>    </td>
          <td>  one week since current date, i.e. <code>@due( +7)</code></td>
         </tr>
         <tr>
          <td>  <code>@due(+3w)</code>  </td>
          <td>  3 weeks since current date, i.e. <code>@due( +21d)</code></td>
         </tr>
         <tr>
          <td>  <code>@due(++)</code>   </td>
          <td>  one day since <code>@created(date)</code> if any, otherwise it is equal to <code>@due(+)</code></td>
         </tr>
         <tr>
          <td>  <code>@due(+2:)</code>   </td>
          <td>  two hours since current date</td>
         </tr>
         <tr>
          <td>  <code>@due(+:555)</code>   </td>
          <td>  555 minutes since current date</td>
         </tr>
         <tr>
          <td>  <code>@due(+2 12:)</code>   </td>
          <td>  2 days and 12 hours since current date</td>
         </tr>
        </table>

* You can create a link to a file within your project by prefixing the file name with a dot and (back)slash like: `.\filename\` or `./another filename/`.  
  The line and column can be specified by colons: `.\filename:11:8`.  
  In SublimeText 3 you can specify a symbol inside that file by using \> character like: `.\filename>symbol`.  
  In SublimeText 2 you can specify a text inside that file by using inch characters like: `.\filename"any text"`.  
  Pressing <kbd>ctrl + o</kbd> (<kbd>alt + o</kbd> on Windows/Linux) will open the file in Sublime and scroll to specific position if any.  
  Also in SublimeText 3 link may point to directory, open such link will add the directory to current project (sidebar).  
  In addition, Markdown and “wiki” (Org-Mode, NV, etc.) styles are supported as well, examples:

```
[](path)
[](path ":11:8")
[](path ">symbol")
[](path "any text")
[[path]]
[[path::11:8]]
[[path::*symbol]]
[[path::any text]]
[[path]] ":11:8"
[[path]] ">symbol"
[[path]] "any text"
```

* To convert current document to HTML, bring up the command palette <kbd>⌘ + shift + p</kbd> and type `Tasks: View as HTML` — it will be opened in default webbrowser, so you can view and save it.  
`Tasks: Save as HTML…` ask if you want to save and if yes, allow to choose directory and filename (but won’t open it in webbrowser).

### Editor Useful Tools:

* Use **<kbd>⌘ + control + up/down</kbd>** (**<kbd>ctrl + shift + up/down</kbd>** on Windows) to move tasks up and down.

* Use **<kbd>⌘ + r</kbd>** to see a list of projects and quickly jump between them


★ See the [Tutorial](https://github.com/aziz/PlainTasks/blob/master/messages/Tutorial.todo) for more detailed information.
