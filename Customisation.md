# Customisation
PlainTasks is an opinionated plugin, which means that it is highly configured to look in a specific way, but this does not mean that you can not customize it. If you feel that something does not look right and you want to change it, you can easily do it in your user settings file. 

Go to `Preferences → Package Settings → PlainTasks` and open `Settings - User`, there you can override all the default settings, to get an idea you can take a look at `Settings - Default`.

Here is a list of PlainTasks’ specific settings. Items in bold are features added by this fork:

|            Setting             |     Default      |                                 Options/Description                                 |
| ------------------------------ | ---------------- | ----------------------------------------------------------------------- |
| open_tasks_bullet          | `☐`              | `-` `❍` `❑` `■` `□` `☐` `▪` `▫` `–` `—` `≡` `→` `›` `[ ]`             |
| done_tasks_bullet          | `✔`              | `✓` `☑` `+` `[x]`                                                      |
| cancelled_tasks_bullet     | `✘`              | `x` `[-]`                                                               |
| date_format                | `(%y-%m-%d %H:%M)` | See [strfti.me](http://www.strfti.me/) for quick reference; detailed documentation: [ST2](https://docs.python.org/2.6/library/datetime.html#strftime-and-strptime-behavior), [ST3](https://docs.python.org/3.3/library/datetime.html#strftime-and-strptime-behavior) |
| done_tag                   | true             | Determines whether done tasks should gain a `@done` tag or not          |
| done_date                  | true             | Determines whether done tasks should gain a date or not                 |
| before_tasks_bullet_margin | 1                | Determines the number of spaces (default indent) before the task bullet |
| project_tag                | true             | Postfix archived task with project tag, otherwise prefix                |
| archive_name               | `Archive:`       | Make sure it is the unique project name within your todo files          |
| new_on_top                 | true             | How to sort archived tasks (done_tag=true and default date_format are required)|
| **split_archived_by_date**                 | true             | Split archived tasks by date, using a dividor (done_tag=true, default date_format and new_on_top=true are required)|
| **jira_domain**                 |              | Set domain to open JIRA tickets at. Do not include `https://`. |
| header_to_task             | false            | If true, a project title line will be converted to a task on the certain keystroke  |
| decimal_minutes            | false            | If true, minutes in lasted/wasted tags will be percent of hour, e.g. 1.50 instead of 1:30 |
| tasks_bullet_space         | whitespace or tab | String to place after bullet, might be any character(s)                |
| highlight_past_due         | true             | If true, highlight past, soon, and invalid `@due(something)`            |
| highlight_due_soon         | 24               | Hours as int, threshold to define which `@due` will be soon             |
| scope_past_due             | `string.other.tag.todo.critical` | Any scope, define color for past `@due`                 |
| scope_due_soon             | `string.other.tag.todo.high`     | Any scope, define color for `@due` will be soon         |
| scope_misformatted         | `string.other.tag.todo.low`      | Any scope, define color for `@due` mismatch **date_format** |
| icon_past_due              | `"circle"`       | Gutter icon¹                                                            |
| icon_due_soon              | `"dot"`          | Gutter icon¹                                                            |
| icon_misformatted          | `""`             | Gutter icon¹                                                            |
| icon_critical              | `""`             | Gutter icon¹                                                            |
| icon_high                  | `""`             | Gutter icon¹                                                            |
| icon_low                   | `""`             | Gutter icon¹                                                            |
| icon_today                 | `""`             | Gutter icon¹                                                            |
| show_remain_due            | false            | In Sublime 3, show remain or overdue time under due tags                |
| show_calendar_on_tags      | false            | In Sublime 3, if true, automatically show date picker when cursor is on tag (you can get date picker any time via context menu) |
| due_preview_offset         | 0                | Place preview date outside of parens of `@due()`, 1 — within            |
| due_remain_format          | `"{time} remaining"` | `{time}` will be replaced with actual value                         |
| due_overdue_format         | `"{time} overdue"` | `{time}` will be replaced with actual value                           |

<b>¹</b> Icon value can be  `"dot"`, `"circle"`, `"bookmark"`, `"cross"`, `""`, or custom relative path to existing png file,
e.g. `"Packages/User/my-icon.png"`.

## Changing color scheme
If you don't like colors used in bundled schemes just copy any `.hidden-tmTheme` from PlainTasks to 
your User directory, change colors and paste the code below in your user settings file:

``` json
{ "color_scheme": "Path to your custom color scheme file. e.g. Packages/User/custom_plaintasks.hidden-tmTheme" }
```

**N.B.**, sometimes you have to restart Sublime Text to apply changes made in tmTheme file.

**N.B.**, `scope_past_due`, `scope_due_soon`, and `scope_misformatted` settings can assign any scopes defined in tmTheme file, e.g. 
you can set `"scope_past_due": "my.own.super.expired.whatever"` and then just add style definition in tmTheme for this scope.

## Taskpaper Compatibility
If you need to keep your files compatible with Taskpaper, go to 
`Preferences → Package Settings → PlainTasks` and open `Settings - User`, then
add these settings to the json file:

```json
{
  "translate_tabs_to_spaces": false,
  "date_format": "(%y-%m-%d)",
  "taskpaper_compatible": true
}
```

## Spell check
It is build-in feature of Sublime, you can toggle spell check with <kbd>F6</kbd>.  
For convinience, you may add bullets in list of ignored words into **`Preferences → Settings - User`**, e.g.

```json
{
  "ignored_words": [ "☐", "✔", "✘", "✄" ]
}
```

# Custom todo icon
PlainTasks comes with a custom todo icon that you can find in the `icons` folder. You can assign it to your todo files to give them a better look and distinguish them from other plain text files. Google and find out how to assign a custom icon to a file type in your operating system.

![](http://f.cl.ly/items/2t312B30121l2X1l0927/todo-icon.png)

# Custom Statistics
Statistics of current file are represented in status-bar, based on `stats_format`, which is `"$n/$a done ($percent%) $progress Last task @done $last"` by default — as you can see it’s just a string containing special directives (see table bellow) and regular chars.

| Directive    | Description                                           |
| ------------ | ----------------------------------------------------- |
| `$o`         | Amount of pending tasks                               |
| `$d`         | Amount of completed tasks                             |
| `$c`         | Amount of cancelled tasks                             |
| `$n`         | Sum of completed and cancelled tasks                  |
| `$a`         | Sum of all tasks                                      |
| `$percent`   | Ratio of `$n` to `$a`                                 |
| `$progress`  | Percent as pseudo graphics (absents if less than 10%) |
| `$last`      | Date of lastly completed task                         |
| `{{...}}`    | Return `pending/completed/cancelled` tasks which matched by regex `...`;<br> e.g. `{{@tag}}` — amounts of tasks with `@tag`; or `{{@a|@b}}` — tasks with either `@a` or `@b` or both.<br> You may add several `{{...}}` to get separate stats for different tags. |

So you can customise it as you like, by adding to `Settings - User`, e.g.

```
{
    "stats_format": "☐$o ✔$d ✘$c",

    // if you want the statistics do not include the archived tasks:
    "stats_ignore_archive": true
}
```

## Copy statistics
Bring up the command palette and type `Tasks: Copy Statistics`.

## Additional settings for progress bar
```
{
    "bar_full": "■",   // any char
    "bar_empty": "☐", // any char

    // if you want to avoid Unicode when copy stats — you can define replacements
    // e.g. to convert ■■■■■■☐☐☐☐ to [======    ]
    "replace_stats_chars": [[" ■", " [="], ["■", "="], ["☐ ", " ] "], ["☐", " "]]
}
```
