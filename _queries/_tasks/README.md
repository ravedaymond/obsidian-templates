---
aliases: 
    - Template Tasks
tags:
    - template/readme
---
# Task Query Templates
All template file names follow this naming convention: 
	`_query-task` + `Todo/Done/Status`. If `Status` the append `-statusSubTag` .

All queries expect that these templates reside within a `_templates/` directory and exclude that folder from any search functions. Each query also has a bolded header defined which is more readable than the query itself when inserting these templates into other vault pages.

| Query Template                         | Description                                                                  |
| -------------------------------------- | ---------------------------------------------------------------------------- |
| [Open Tasks](_query-taskTodo.md)       | Shows all tasks that are not marked as done, regardless of status.           |
| [Done Tasks](_query-taskDone.md)       | Shows all tasks that are marked as done, regardless of status.               |
| [Status Open](_query-taskStatus-open.md) | Shows all tasks that that are not marked as done, with the status of 'open'. |
| [Status WIP](_query-taskStatus-wip.md)   | Shows all tasks that that are not marked as done, with the status of 'open'. |
| [Status Done](_query-taskStatus-done.md)                            | Shows all tasks that are marked as done, with a status of 'done'.            |

Continue reading to understand the concept behind redefining the task workflow in [Obsidian](https://obsidian.md/).

---
## How Obsidian Defines Tasks
All templates within this folder relate to what [Obsidian](https://obsidian.md/) considers to be a `task`. Tasks have 2 states:
- [ ] task-todo
	Markdown syntax uses a space(` `) character: `- [ ] task-todo`
- [x] task-done
	Markdown syntax uses the `x` character: `- [x] task-done`
The default "task workflow" considers a task as "task-done" as long as the character used is not the "space" character. This applies to all [checkbox variants](#Obsidian-Checkbox-Variants).

### Default Task Search Function
The checkbox list items within this section will be found when using the generic search functionality in [Obsidian](https://obsidian.md/) that searches for tasks across files. For example:
- Search: `task:""` OR `task:("")`  will find all tasks, unchecked/checked.
- Search: `task-todo:""` or `task-todo:("")` will find all tasks that are unchecked.
- Search: `task-done:""` or `task-done:("")` will find all tasks that are checked (regardless of which character is used).

---
## Redefining 'Task' in the Workflow
These templates utilize the above built in search functions but expand them using tags and  [#regex](https://en.wikipedia.org/wiki/Regular_expression). This method utilizes the built in search functions but attempts to redefine what is considered a 'task' in our workflow to the following:

- [ ] This is a generic checkbox list item that is not checked.
- [x] This is a generic checkbox list item that is checked.
- [?] Any checkbox variant is also considered a generic checkbox list item. 

- [ ] #task This is a redefined 'task' item that is open.
- [x] #task This is a redefined 'task' item that is done.

A simple, flexible, redefinition.

If wanted, you can adapt these templates to have regex for searching for checkbox variants as well, however that is outside the scope of this redefined workflow.

### Expanding a 'Task' with Status
We can expand upon our redefined task workflow by using sub-tags to define a 'status' for any tasks:
- [ ] #task This task has no status (considered 'open' by default).
- [ ] #task/open This task has the 'open' status.
- [ ] #task/wip This task has the 'wip' status (work-in-progress).
- [ ] #task/blocked This task has the 'blocked' status.
- [x] #task This task has no status, but is marked as done (considered done by default).
- [x] #task/done This task has the 'done' status.

The above are just a few examples of expected status sub-tags that could be used. 

---
## Obsidian Task Checkbox Variants
This section can be used as an offline reference to the checkbox variants that are available within Obsidian. You can view also this list on the official documentation.

*The below list is up to date as of: 2023-03-18*
- [ ] `- [ ] `: To-Do; Open; Incomplete; Unchecked;
- [x] `- [x] `: Done; Closed; Complete; Checked;
      Markdown syntax standard is to use the `x` character when marking a list checkbox. Characters that have no variant will default to this checkbox.
- [i] `- [i] `: Info; Information; Informational;
- [?] `- [?] `: Question; FAQ; 
- [!] `- [!] `: Important; Alert; Warning; 
- [<] `- [<] `: Date; Calendar; Event;
- [>] `- [>] `: Arrow;
- [*] `- [*] `: Star;
- [p] `- [p] `: Positive; Approved; Thumbs-up;
- [c] `- [c] `: Negative; Declined; Thumbs-down;
- [u] `- [u] `: Upwards; Rising; Gain;
- [d] `- [d] `: Downwards; Falling; Loss;
- [b] `- [b] `: Bookmark
- [l] `- [l] `: Location; GPS; Pin;
- [f] `- [f] `: Hot; Trending; Popular;
- [k] `- [k] `: Key; Password; 
- [w] `- [w] `: Event; 
- [/] `- [/] `: 
- [^] `- [^] `: Footnote;
- [-] `- [-] `: Strikethrough;

---
## Regex Help
All regex used is placed within the parenthesis of the built in Obsidian search functions. Below are some helpful resources for regex:
- https://regexone.com/
- https://regex101.com/
- https://regexr.com/

Query Reference
```regex
// Matches the characters `#task` literally. Followed by any number of spaces. Finally matched by a non-space character.
\#task\s+\S

//Matches the characters `#task` literally. Followed by any number of spaces OR any number of additional sub tags (eg. /subtag/subtag...) that have any number of spaces after the last subtag. Finally matched by a non-space character.
\#task(\s+|((\/\w+)+\s+))\S
```
