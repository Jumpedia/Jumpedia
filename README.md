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

### Attribute

`/attribute info <attribute> [list]`
- `<attribute>`: The name or alias of an attribute.
- `[list]`:  The name of the list in which the attribute should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show the name, aliases, type, slot type, position, min slots, max slots and collection of the specified attribute.

---

`/attributes browse [type] [list]`
- `[type]`: The type to only show attributes of. By default show all types.
- `[list]`: The name of the list from where the attribute should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show the name, aliases, type, slot type, position, min slots, max slots and collection of all attributes in the given list.

### Attribute (Privileged)

`/attribute create <list> <name> <type> <slot_type> <max_slots> [aliases] [collection]`
- `<list>`: The name of the list in which the attribute should be created in.
- `<name>`: The name the new attribute should have.
- `<type>`: The type the new attribute should have.
- `<slot_type>`: The slot type the new attribute should have.
- `<max_slots>`: The maximum amount of slots the new attribute should have.
- `[aliases]`: The aliases the new attribute should have, using [this]() syntax. By default empty.
- `[collection]` The collection the new attribute should have, using [this]() syntax. By default empty.

Create a new alias with the given name, type, slot type, max slots, aliases and collection.

---

...
...
...

### Task

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
- `[list]`: The name of the list from where the task should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of all tasks in the given list, with the possibility to set a filter, sort and yield.

---

`/tasks browse_user [filter] [sort] [yield] [user] [list]`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. By default no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. By default sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. By default the static attribute `name`, all attributes used in the `[filter]` and `[sort]` and all user attributes are yielded.
- `[user]`: The user of whom to grab the tasks and their user attribute values from. By default the interacting user.
- `[list]`: The name of the list from where the tasks should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static, task and user attribute values of all tasks in the given list a user has given themselves, with the possibility to set a filter, sort and yield. The user attribute values are taken from the given user. 

---

`/tasks browse_missing [filter] [sort] [yield] [user] [list]`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. By default no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. By default sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. By default the static attribute `name`, all attributes in the filters and sorts and all user attributes are yielded.
- `[user]`: The user of whom to check the tasks of. By default the interacting user.
- `[list]`: The name of the list from where the tasks should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of all tasks in the given list a user has **not** given themselves, with the possibility to set a filter, sort and yield.

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

`/task create <list> <name> [aliases] [task_attribute_value_mapping]` 
- `<list>`: The name of the list in which the task should be created in.
- `<name>`: The name the new task should have.
- `[aliases]`: The aliases the new task should have, using [this]() syntax. By default empty.
- `[task_attribute_value_mapping]`: Task attributes with associated values, using [this]() syntax. By default empty.

Create a new task with the given name, aliases and task attribute value mapping. 

The community rank **helper** is required.

---

`/task nuke <list> <task>`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of a task.

Delete the specified task. This will also delete all associated user data!

The community rank **moderator** is required.

---

`/task edit name <list> <task> <new_name>`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of of a task.
- `<new_name>`: The new name the task should be renamed to.

Rename the specified task from the specified list. 

The community rank **moderator** is required.

---

`/task edit aliases <list> <task> <new_aliases>`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of of a task.
- `<new_aliases>`: The new aliases to replace the previous aliases of the task with, using [this]() syntax.

Replace the previous aliases of the specified task with the ones specified.

The community rank **moderator** is required.

---

`/task edit edit_attribute_value_mapping <list> <task> <new_attribute_value_mapping>`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of of a task.
- `<new_attribute_value_mapping>`: The new task attribute value mapping to replace the previous task attribute value mapping of the task with, using [this]() syntax.

Replace the previous task attribute value mapping of the specified task with the one specified.

The community rank **moderator** is required.

### User

`/user info [user]`
- `[user]`: The user of whom to get info from. By default the interacting user.

Show the name, ranks and selected list of the given user. If the command is not executed in a server that is connected to a community, the community specific information is left out.

---

`/user set_selected_list [list] [user]`
- `[list]`: The name of the list that should be set as the default. If not specified, this will unset the user's selected list.
- `[user]`: The user for whom the list should be set as the default. By default the interacting user.

Set the selected list of the given user. This is the list that is automatically selected whenever that user executes a command with a `[list]` parameter, but doesn't explicitly specify it.
If the user has no selected list yet or unsets it, in case of executing such a command, it will fallback to the community's `default selected list`. If that is also unset, an error will appear that tells the interacting user to sepcify a list explicitly. 

If the given user is somebody other than the interacting user, the community rank **moderator** is required.

### User (Privileged)

`/user set_community_rank <user> <community_rank>`
- `<user>`: The user of whom the community rank should be set.
- `<community_rank>`: The community rank that should be set for the user.

Set the specified user's community rank to the one specified.

The interacting user's community rank must be higher than the community rank of the specified user and the interacting user may only set the community rank of the specified user to a community rank lower than their own.

---

`/user set_jumpedia_rank <user> <jumpedia_rank>`
- `<user>`: The user of whom the jumpedia rank should be set.
- `<jumpedia_rank>`: The jumpedia rank that should be set for the user.

Set the specified user's jumpedia rank to the one specified.

The interacting user's jumpedia rank must be higher than the jumpedia rank of the specified user and the interacting user may only set the jumpedia rank of the specified user to a jumpedia rank lower than their own.

## Concepts

### Community

### List

### Attribute

### Task
Tasks are the "thing" users in the community should aim to complete. This can be anything from challenges, speedruns, trickjumps, quests or anything else completable. With the `task` command group, users can give themselves completed tasks (and possibly add their own data), browse through the tasks, get detailed information about specific tasks and more!

### User
#### Rank

