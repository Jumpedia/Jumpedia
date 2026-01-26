# Jumpedia
In simple words, Jumpedia is a system that makes it easy for communities to create and manage tasks, which users in the community can then try to complete and easily manage.

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
Tasks are the "thing" users in the community should aim to complete. This can be anything from challenges, speedruns, trickjumps, quests or anything else completable. With the `task` command group, users can give themselves completed tasks (and possibly add their own data), browse through the tasks, get detailed information about specific tasks and more!

`/task info <task> [list]`
- `<task>`: The name or alias of a task.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of the specified task. 

---

`/task info_user <task> [user] [list]`
- `<task>`: The name or alias of a task.
- `[user]`: The user of whom to grab user attribute values from. By default the interacting user.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static, task and user attribute values of the specified task. The user attribute values are taken from the given user. 

---

`/tasks browse [filter] [sort] [yield] [list]`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. If not specified, no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. If not specified, sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. If not specified, the static attribute `name` and all attributes used in the `[filter]` and `[sort]` will be yielded.
- `[list]`: The name of the list of which the task should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of all tasks, with the possibility to set a filter, sort and yield.

---

`/tasks browse_user [filter] [sort] [yield] [user] [list]`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. By default no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. By default sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. By default the static attribute `name`, all attributes used in the `[filter]` and `[sort]` and all user attributes are yielded.
- `[user]`: The user of whom to grab the tasks and their user attribute values from. By default the interacting user.
- `[list]`: The name of the list of which the tasks should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static, task and user attribute values of all tasks a user has given themselves, with the possibility to set a filter, sort and yield. The user attribute values are taken from the given user. 

---

`/tasks browse_missing [filter] [sort] [yield] [user] [list]`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. By default no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. By default sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. By default the static attribute `name`, all attributes in the filters and sorts and all user attributes are yielded.
- `[user]`: The user of whom to check the tasks of. By default the interacting user.
- `[list]`: The name of the list of which the tasks should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of all tasks a user has **not** given themselves, with the possibility to set a filter, sort and yield.

---

`/task give <task> [user_attribute_value_mapping] [user] [list]`
- `<task>`: The name or alias of a task.
- `[user_attribute_value_mapping]`: User attributes with associated values, using [this]() syntax.
- `[user]`: The user whom the task is given. By default the interacting user.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Give the specified task to the given user. The opposite of the `/task take` command below.

If the given user is somebody other than the interacting user, the community rank **moderator** is required. 

---

`/task take <task> [user] [list]`
- `<task>`: The name or alias of a task.
- `[user]`: The user from whom the task is taken away. By default the interacting user.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Take away the specified task from the given user. The opposite of the `/task give` command above.

If the given user is somebody other than the interacting user, the community rank **moderator** is required. 

### Task (Privileged)
`/task create <name> <list> [aliases] [task_attribute_value_mapping]` 
- `<task>`: The name the new task should have.
- `<list>`: The name of the list in which the task should be searched for.
- `[aliases]`: The aliases the new task should have.
- `[task_attribute_value_mapping]`: Task attributes with associated values, using [this]() syntax.

Create a new task with the specified name, aliases and task attribute value mapping. 

The community rank **helper** is required.

---

`/task nuke <task> <list>`
- `<task>`: The name or alias of a task.
- `<list>`: The name of the list in which the task should be searched for.

Delete the specified task. This will also delete all associated user data!

The community rank **moderator** is required.

---

`/task edit name <task> <list> <new_name>`
- `<task>`: The name or alias of of a task.
- `<list>`: The name of the list in which the task should be searched for.
- `<new_name>`: The new name the task should be renamed to.

Rename the specified task from the specified list. 

The community rank **moderator** is required.

---

`/task edit aliases <task> <list> <new_aliases>`
- `<task>`: The name or alias of of a task.
- `<list>`: The name of the list in which the task should be searched for.
- `<new_aliases>`: The new aliases to replace the previous aliases of the task with, using [this]() syntax.

Replace the previous aliases of the specified task with the ones specified.

The community rank **moderator** is required.

---

`/task edit edit_attribute_value_mapping <task> <list> <new_attribute_value_mapping>`
- `<task>`: The name or alias of of a task.
- `<list>`: The name of the list in which the task should be searched for.
- `<new_attribute_value_mapping>`: The new task attribute value mapping to replace the previous task attribute value mapping of the task with, using [this]() syntax.

Replace the previous task attribute value mapping of the specified task with the one specified.

The community rank **moderator** is required.

### User
A user is any Discord user interacting with Jumpedia. Every user has 3 rank types that defines their privileges (see: [what-are-ranks]()



### What are ranks?
