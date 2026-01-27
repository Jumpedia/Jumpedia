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

`/attribute info`
- `<attribute>`: The name or alias of the attribute.
- `[list]`:  The name of the list in which the attribute should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show the name, aliases, type, slot type, position, min slots, max slots and collection of the specified attribute.

---

`/attributes browse`
- `[type]`: The type to only show attributes of. By default show all types.
- `[list]`: The name of the list from where the attribute should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show the name, aliases, type, slot type, position, min slots, max slots and collection of all attributes in the specified list.

### Attribute (Privileged)

`/attribute create`
- `<list>`: The name of the list in which the attribute should be created in.
- `<type>`: The type the new attribute should have.
- `<name>`: The name the new attribute should have.
- `<slot_type>`: The slot type the new attribute should have.
- `<max_slots>`: The maximum amount of slots the new attribute should have.
- `[aliases]`: The aliases the new attribute should have, using [this]() syntax. By default empty.
- `[collection]` The collection the new attribute should have, using [this]() syntax. By default empty.

Create a new alias with the specified name, type, slot type, max slots, aliases and collection.

The community rank **administrator** is required.

---

`/attribute nuke`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.

Delete the specified attribute. This will also delete all associated task or user data!

The community rank **administrator** is required.

---

`/attribute edit name`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.
- `<new_name>`: The new name the attribute should be renamed to.

Rename the specified attribute. 

The community rank **administrator** is required.

---

`/attribute edit aliases`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.
- `<new_aliases>`: The new aliases to replace the previous aliases of the attribute with, using [this]() syntax.

Replace the previous aliases of the specified attribute with the ones specified.

The community rank **administrator** is required.

---

`/attribute edit min_and_max_slots`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.
- `<new_min_slots>`: The new minimum slot count to replace the previous minimum slot count of the attribute with.
- `<new_max_slots>`: The new maximum slot count to replace the previous maximum slot count of the attribute with.

Replace the previous minimum and maximum slot count of the specified attribute with the ones specified.
If the specified attribute is a task attribute, all tasks' values in the specified list for the specified must fit the new bounds, otherwise the values must be manually adjusted beforehand.
If the specified attribute is a user attribute, **none** of the users' values in the specified list for the specified attribute are required to fit the new bounds. Values set from that point onwards must
match the new bounds though.

The community rank **administrator** is required.

`/attribute edit collection`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.
- `<collection>`: The new collection to replace the previous collection of the attribute with, using [this]() syntax.

**Coming soon...**

Replace the previous collection of the specified attribute with the one specified.

The community rank **administrator** is required.

### Task

`/task info`
- `<task>`: The name or alias of the task.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of the specified task. 

---

`/task info_user`
- `<task>`: The name or alias of the task.
- `[user]`: The user of whom to grab user attribute values from. By default the interacting user.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static, task and user attribute values of the specified task. The user attribute values are taken from the specified user. 

---

`/tasks browse`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. If not specified, no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. If not specified, sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. If not specified, the static attribute `name` and all attributes used in the `[filter]` and `[sort]` will be yielded.
- `[list]`: The name of the list from where the task should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of all tasks in the specified list, with the possibility to set a filter, sort and yield.

---

`/tasks browse_user`
- `[filter]`: The filter, using [this]() syntax, to apply to all tasks of the specified list. By default no filter is applied.
- `[sort]`: The sort, using [this]() syntax, to apply to all tasks of the specified list. By default sort by the static attribute `name`.
- `[yield]`: The yield, using [this]() syntax, to apply to all tasks of the specified list. By default the static attribute `name`, all attributes used in the `[filter]` and `[sort]` and all user attributes are yielded.
- `[given]`: Whether to only show the tasks a user has been given or to only show the tasks a user is missing. By default true (show only the given tasks).
- `[user]`: The user of whom to grab the tasks and their user attribute values from. By default the interacting user.
- `[list]`: The name of the list from where the tasks should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static, task and user attribute values of all tasks in the specified list the specified user has been given, with the possibility to set a filter, sort and yield. 
The user attribute values are taken from the specified user. 
If `[given]` is false, only show the tasks that have not yet been given to the user (and therefore don't show any user attributes either).

---

`/task give`
- `<task>`: The name or alias of the task.
- `[user_attribute_value_mapping]`: User attributes with associated values, using [this]() syntax.
- `[user]`: The user whom the task is given. By default the interacting user.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Give the specified task to the specified user. The opposite of the `/task take` command below.

If the specified user is somebody other than the interacting user, the community rank **moderator** is required. 

---

`/task take`
- `<task>`: The name or alias of the task.
- `[user]`: The user from whom the task is taken away. By default the interacting user.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Take away the specified task from the specified user. The opposite of the `/task give` command above.

If the specified user is somebody other than the interacting user, the community rank **moderator** is required. 

### Task (Privileged)

`/task create` 
- `<list>`: The name of the list in which the task should be created in.
- `<name>`: The name the new task should have.
- `[aliases]`: The aliases the new task should have, using [this]() syntax. By default empty.
- `[task_attribute_value_mapping]`: Task attributes with associated values, using [this]() syntax. By default empty.

Create a new task with the specified name, aliases and task attribute value mapping. 

The community rank **helper** is required.

---

`/task nuke`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of the task.

Delete the specified task. This will also delete all associated user data!

The community rank **moderator** is required.

---

`/task edit name`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of the task.
- `<new_name>`: The new name the task should be renamed to.

Rename the specified task. 

The community rank **moderator** is required.

---

`/task edit aliases`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of the task.
- `<new_aliases>`: The new aliases to replace the previous aliases of the task with, using [this]() syntax.

Replace the previous aliases of the specified task with the ones specified.

The community rank **moderator** is required.

---

`/task edit edit_attribute_value_mapping`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of the task.
- `<new_attribute_value_mapping>`: The new task attribute value mapping to replace the previous task attribute value mapping of the task with, using [this]() syntax.

Replace the previous task attribute value mapping of the specified task with the one specified.

The community rank **moderator** is required.

### User

`/user info`
- `[user]`: The user of whom to get info from. By default the interacting user.

Show the name, ranks and selected list of the specified user. If the command is not executed in a server that is connected to a community, the community specific information is left out.

---

`/users browse`

**Coming soon...**

Show the name, ranks and selected list of all users in the community.

---

`/users browse_task`
- `<task>`: The name or alias of the task for which the user attribute values should be taken from.
- `[given]`: Whether to only show the users that have been given the task or to only show the users that are missing it. By default true (show only the users with the task given). 
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

**Coming soon...**

Show the name, ranks, selected list and user attribute values of all users in the community that have been given the specified task.
.......

---

`/user set_selected_list`
- `[list]`: The name of the list that should be set as the default. If not specified, this will unset the user's selected list.
- `[user]`: The user for whom the list should be set as the default. By default the interacting user.

Set the selected list of the specified user. This is the list that is automatically selected whenever that user executes a command with a `[list]` parameter, but doesn't explicitly specify it.
If the user has no selected list yet or unsets it, in case of executing such a command, it will fallback to the community's `default selected list`. If that is also unset, an error will appear that tells the interacting user to sepcify a list explicitly. 

If the specified user is somebody other than the interacting user, the community rank **moderator** is required.

### User (Privileged)

`/user set_community_rank`
- `<user>`: The user of whom the community rank should be set.
- `<community_rank>`: The community rank that should be set for the user.

Set the specified user's community rank to the one specified.

The interacting user's community rank must be higher than the community rank of the specified user and the interacting user may only set the community rank of the specified user to a community rank lower than their own.

---

`/user set_jumpedia_rank`
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

