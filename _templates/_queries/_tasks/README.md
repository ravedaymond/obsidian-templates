# Task Query Templates
All file names follow this naming convention: `_query-task` + `Todo`/`Done` + `-status`. Below is a table of all task related query templates. 

| Query Template                       | Description                                                  |
| ------------------------------------ | ------------------------------------------------------------ |
| [Todo](_query-taskTodo.md)           | Shows all tasks that are not marked as done, regardless of status. |
| [Done](_query-taskDone.md)           | Shows all tasks that are marked as done, regardless of status. |
| [Todo-open](_query-taskTodo-open.md) | Shows all tasks that that are not marked as done, with the status of 'open'. |
| [Todo-wip](_query-taskTodo-wip.md)   | Shows all tasks that that are not marked as done, with the status of 'open'. |

For more information on how these templates adapt the task workflow see the below sections, starting with [What is a task?](#What-is-a-task).

---
## What is a task?
All templates within this folder relate to what [Obsidian](https://obsidian.md/) considers to be a `task`. 
Tasks in Obsidian have 2 states across 3 different views:
- [ ] Task ToDo
	Markdown syntax: `- [ ] Task ToDo`
- [x] Task Done
	Markdown syntax uses 'x' character: `- [x] Task ToDo`
- [?] Task Done (strikeless)
	Markdown syntax uses any other character: `- [?] Task ToDo`

## Default Task Search Function
The above tasks without any further intervention will be visible with the generic search functionality in obsidian to find all tasks across files. For example:
- Search: `task:""` OR `task:("")`  will find all tasks, unchecked/checked.
- Search: `task-todo:""` or `task-todo:("")` will find all tasks that are unchecked.
- Search: `task-done:""` or `task-done:("")` will find all tasks that are checked (regardless of which character is used).

## Redefining 'Task' in the Workflow
These templates utilize the above built in search functions but expand them using tags and  [#regex](https://en.wikipedia.org/wiki/Regular_expression). This method allows to still utilize the built in search functions but attempts to redefine what is considered a 'task' in our workflow to the following:
- [ ] This is a generic checkbox list item.
- [ ] #task This is a redefined 'task' item.

## Defining Task 'Status'
We can expand upon this by using sub-tags to define a 'status' for any tasks:
- [ ] #task This task has no status (considered 'open' by default)
- [ ] #task/open This task has the 'open' status.
- [ ] #task/wip This task has the 'wip' status (work-in-progress).
- [x] #task/done This task has the 'done' status.
- [?] #task/done This task has the 'done' status w/out strikethrough.
- [x] #task This task has no status, but is marked as done (considered done by default).

## Regex Help
All regex used is placed within the parenthesis of the built in Obsidian search functions. Below are a few sandbox resources for regex:
- https://regexone.com/
- https://regex101.com/
- https://regexr.com/

---
