# Jumpedia
In simple words, Jumpedia is a system that makes it easy for communities to create and manage tasks, which users in the community can then try to complete, give themselves and easily manage.

## Quick Guides
This whole documentation can be overwhelming, and we know that! This category's purpose is to make it easier for users to find the information they need.

**Attention:** All guides listed below are ordered from simplest to most advanced. For every guide, it is recommended to read and understand the previous (upper) guides first, even those not in the same category!

If you want to create or connect a community, continue [here](#createconnect-a-community).

### Community User Guides
These guides are for basic community users that aren't part of staff. 
- **Newcomer's Guide:** link
- **Regular's Guide:** link

### Community Staff Guides
These guides are recommended for users who got promoted to a new rank inside of a community.
- **Helper's Guide:** link
- **Moderator's Guide:** link
- **Administrator's Guide:** link
- **Owner's Guide:** link

### Jumepedia Staff Guides
- **Meta Administrator's Guide:** link


## Create/Connect a Community
If you want to connect an existing community to your Discord server, [click here]() to invite the Jumpedia Discord bot to your server and then use the [community connect](#community-connect) command to actually connect the specfic community to your server.

If you want to create a community, you will have to be patient for just a tiny bit longer. Jumpedia is currently in its stress testing phase in the "SMO Trickjumping" community and will be available to other communities in the coming updates (approx. March 2026).

## Slash Commands
Discord slash commands are currently the only way to interact with Jumpedia. You can use them by being on a Discord server in which the Jumpedia bot is also on.

Parameters wrapped in `<>` are required, while parameters wralled in `[]` are optional.

### Task
`/task info <task> [list]`
- `<task>`: The name or alias of a task.
- `[list]`: The name of the list in which the task should be searched for. By default the executing user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of the specified task. 

---

`/task info_user <task> [user] [list]`
- `<task>`: The name or alias of a task.
- `[user]`: The user of whom to grab user attribute values from. By default the executing user.
- `[list]`: The name of the list in which the task should be searched for. By default the executing user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static, task and user attribute values of the specified task. The user attribute values are taken from the given user. 

---

`/task browse [filter] [sort] [yield] [list]`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. If not specified, no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. If not specified, sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. If not specified, the static attribute `name` and all attributes used in the `[filter]` and `[sort]` will be yielded.
- `[list]`: The name of the list of which the task should be taken from. By default the executing user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of all tasks, with the possibility to set a filter, sort and yield.

---

`/task browse_user [filter] [sort] [yield] [user] [list]`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. By default no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. By default sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. By default the static attribute `name`, all attributes used in the `[filter]` and `[sort]` and all user attributes are yielded.
- `[user]`: The user of whom to grab the tasks and their user attribute values from. By default the executing user.
- `[list]`: The name of the list of which the tasks should be taken from. By default the executing user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static, task and user attribute values of all tasks a user has given themselves, with the possibility to set a filter, sort and yield. The user attribute values are taken from the given user. 

---

`/task browse_missing [filter] [sort] [yield] [user] [list]`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. By default no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. By default sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. By default the static attribute `name`, all attributes in the filters and sorts and all user attributes are yielded.
- `[user]`: The user of whom to check the tasks of. By default the executing user.
- `[list]`: The name of the list of which the tasks should be taken from. By default the executing user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of all tasks a user has **not** given themselves, with the possibility to set a filter, sort and yield.

---

`/task give <task> [user_attribute_value_mapping] [user] [list]`
- `<task>`: The name or alias of a task.
- `[user_attribute_values]`: User attributes with associated values, using [this]() syntax.
- `[user]`: The user whom is given the task. By default the executing user.
- `[list]`: The name of the list in which the task should be searched for. By default the executing user's selected list, if the user has it set, otherwise the community's default selected list.

Give the specified task to the given user.

If the given user is somebody other than the executing user, the community rank **moderator** is required. 

---

`/task remove <task> [user] [list]`
- `<task>`: The name or alias of a task.
- `[user]`: The user whom is given the task. By default the executing user.
- `[list]`: The name of the list in which the task should be searched for. By default the executing user's selected list, if the user has it set, otherwise the community's default selected list.

Remove the specified task from the given user.

If the given user is somebody other than the executing user, the community rank **moderator** is required. 

### Task (Privileged)
`/task create <name> <list> [aliases] [task_attribute_values]` 
- `<name>`: The name the new task should have.
- `<list>`: The name of the list in which the task should be created in. It needs to be specified explicitly for security reasons.
- `[aliases]`: The aliases the new task should have.
- `[task_attribute_values]`: Task attributes with associated values, using [this]() syntax.

Create a new task with the specified name, aliases......... 
