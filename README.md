# Jumpedia
In simple words, Jumpedia is a Discord bot that makes it easy for communities to create and manage so called "tasks", which are objectives the users of the community try to complete and collect.

## About this documentation
> [!IMPORTANT]
> This documentation covers the most important parts, but is not polished yet and is missing some smaller details. For any questions, visit the Jumpedia Discord server: https://discord.gg/S4hPp6PWWr


## Connect or Create a Community
If you want to connect an existing community to a Discord server you own, [click here](https://discord.com/oauth2/authorize?client_id=1467573198622036145&permissions=4503599627447360&integration_type=0&scope=bot) to invite the Jumpedia Discord bot to your server and then use the [community connect](#community-connect) command to actually connect the specific community to your server.

If you want to create a community, you will have to be patient for a bit longer. Jumpedia is currently in its stress testing phase and will be available to other communities soon. If you still want to experimentally use Jumpedia for your community, DM [@jonikauf](https://discord.com/users/679564566769827841) on Discord.

## Slash Commands
Discord slash commands are currently the only way to interact with Jumpedia. You can use them by being on a Discord server in which the Jumpedia bot is also on.

Parameters wrapped in `<>` are required, while parameters wrapped in `[]` are optional.

### Community

#### `/community info`

Show the name, lists, default selected list, connected server count and limits of the community.

---

#### `/communities browse`

Show the name, lists, default selected list, connected server count and limits for all communities of Jumpedia.

### Community (Privileged)

#### `/community create`
- `<name>`: The name the new community should have.
- `<owner>`: The user that should be the owner of the new community.
- `[default_selected_list_name]`: The name of the list that should automatically be created with the community and also set as the default selected list. By default don't create it.

Create a new community with the specified name and if specified create a default selected list. 

The Jumpedia rank **meta administrator** is required.

---

#### `/community nuke`

Delete the community. This will also delete all associated lists and all of their associated data! 

The community rank **owner** is required.

---

#### `/community connect`
- `<community>`: The name of the community.

Connect the Discord server the command is executed in to the specified community.

The server rank **owner** is required.

---

#### `/community disconnect`

Disconnect the Discord server the command is executed in from the connected community.

The server rank **owner** is required.

---

#### `/community edit default_selected_list`
- `[list]`: The name of the list. If not specified, the default selected list of the community will be unset.

Set the default selected list of the community. If no list is specified, the community's default selected list is unset.

The community rank **administrator** is required.

### List

#### `/list info`
- `[list]`: The name of the list. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show the name, attributes, task count and whether it is the default selected list of the community for the specified list.

---

#### `/lists browse`

Show the name, attributes, task count and whether it is the default selected list of the community for all lists in the community.

### List (Privileged)

#### `/list create`
- `<name>`: The name the new list should have.

Create a new list with the specified name. With its creation it also automatically creates the static attributes "Id", "Name" and "Alias".

The community rank **administrator** is required.

---

#### `/list nuke`
- `<list>`: The name of the list.

Delete the specified list. This will also delete all associated tasks, attributes, and all of their associated data as well!

The community rank **administrator** is required.

---

#### `/list edit name`
- `<list>`: The name of the list.
- `<new_name>`: The new name the list should be renamed to.

Rename the specified list. 

The community rank **administrator** is required.

### Attribute

#### `/attribute info`
- `<attribute>`: The name or alias of the attribute.
- `[list]`:  The name of the list in which the attribute should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show the name, aliases, type, slot type, position, min slot count, max slot count and collection of the specified attribute.

---

#### `/attributes browse`
- `[type]`: The type to only show attributes of. By default show all types.
- `[list]`: The name of the list from where the attribute should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show the name, aliases, type, slot type, position, min slot count, max slot count and collection of all attributes in the specified list.

### Attribute (Privileged)

#### `/attribute create`
- `<list>`: The name of the list in which the attribute should be created in.
- `<type>`: The type the new attribute should have.
- `<name>`: The name the new attribute should have.
- `<slot_type>`: The slot type the new attribute should have.
- `<max_slot_count>`: The maximum amount of slots the new attribute should have.
- `[aliases]`: The aliases the new attribute should have, using [this](#alias-syntax) syntax. By default empty.
- `[collection]`: The collection the new attribute should have, using [this](#mapping-syntax) syntax to describe names mapping to aliases. By default empty.

Create a new attribute with the specified name, type, slot type, max slot count, aliases and collection.

The community rank **administrator** is required.

---

#### `/attribute nuke`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.

Delete the specified attribute. This will also delete all associated task or user data!

The community rank **administrator** is required.

---

#### `/attribute edit name`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.
- `<new_name>`: The new name the attribute should be renamed to.

Rename the specified attribute. 

The community rank **administrator** is required.

---

#### `/attribute edit aliases`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.
- `<new_aliases>`: The new aliases to replace the previous aliases of the attribute with, using [this](#alias-syntax) syntax.

Replace the previous aliases of the specified attribute with the ones specified.

The community rank **administrator** is required.

---

#### `/attribute edit min_and_max_slot_count`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.
- `<new_min_slot_count>`: The new minimum slot count to replace the previous minimum slot count of the attribute with.
- `<new_max_slot_count>`: The new maximum slot count to replace the previous maximum slot count of the attribute with.

Replace the previous minimum and maximum slot count of the specified attribute with the ones specified.
If the specified attribute is a task attribute, all tasks' values in the specified list for the specified attribute must fit the new bounds, otherwise the values must be manually adjusted beforehand.
If the specified attribute is a user attribute, **none** of the users' values in the specified list for the specified attribute are required to fit the new bounds. Values set from that point onwards must match the new bounds though.

The community rank **administrator** is required.

---

#### `/attribute edit collection`
- `<list>`: The name of the list in which the attribute should be searched for.
- `<type>`: The type of the attribute.
- `<attribute>`: The name or alias of the attribute.
- `<collection>`: The new collection to replace the previous collection of the attribute with, using [this](#mapping-syntax) syntax to describe names mapping to aliases.

Replace the previous collection of the specified attribute with the one specified.

The community rank **administrator** is required.

**Coming soon...**

### Task

#### `/task info`
- `<task>`: The name or alias of the task.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of the specified task. 

---

#### `/task info_user`
- `<task>`: The name or alias of the task.
- `[user]`: The user of whom to grab user attribute values from. By default the interacting user.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static, task and user attribute values of the specified task. The user attribute values are taken from the specified user. 

---

#### `/tasks browse`
- `[filter]`: The filter, using [this](#filter-syntax) syntax, to apply to all tasks of the specified list. If not specified, no filter is applied.
- `[sort]`: The sort, using [this](#sort-syntax) syntax, to apply to all tasks of the specified list. If not specified, sort by the static attribute `name`.
- `[yield]`: The yield to apply to all tasks of the specified list. If not specified, the static attribute `name` and all attributes used in the `[filter]` and `[sort]` will be yielded.
- `[list]`: The name of the list from where the task should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static and task attribute values of all tasks in the specified list, with the possibility to set a filter, sort and yield.

---

#### `/tasks browse_user`
- `[filter]`: The filter, using [this](#filter-syntax) syntax, to apply to all tasks of the specified list. By default no filter is applied.
- `[sort]`: The sort, using [this](#sort-syntax) syntax, to apply to all tasks of the specified list. By default sort by the static attribute `name`.
- `[yield]`: The yield to apply to all tasks of the specified list. By default the static attribute `name`, all attributes used in the `[filter]` and `[sort]` and all user attributes are yielded.
- `[given]`: Whether to only show the tasks a user has been given or to only show the tasks a user is missing. By default true (show only the given tasks).
- `[user]`: The user of whom to get the tasks and their user attribute values from. By default the interacting user.
- `[list]`: The name of the list from where the tasks should be taken from. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show all static, task and user attribute values of all tasks in the specified list the specified user has been given, with the possibility to set a filter, sort and yield. 
The user attribute values are taken from the specified user. 
If `[given]` is false, only show the tasks that have not yet been given to the user (and therefore don't show any user attributes either).

---

#### `/task give`
- `<task>`: The name or alias of the task.
- `[user_attribute_value_mapping]`: User attributes with associated values, using [this](#mapping-syntax) syntax.
- `[user]`: The user whom the task is given. By default the interacting user.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Give the specified task to the specified user. The opposite of the [task take](#task-take) command below.

If the specified user is somebody other than the interacting user, the community rank **moderator** is required. 

---

#### `/task take`
- `<task>`: The name or alias of the task.
- `[user]`: The user from whom the task is taken away. By default the interacting user.
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Take away the specified task from the specified user. The opposite of the [task give](#task-give) command above.

If the specified user is somebody other than the interacting user, the community rank **moderator** is required. 

### Task (Privileged)

#### `/task create` 
- `<list>`: The name of the list in which the task should be created in.
- `<name>`: The name the new task should have.
- `[aliases]`: The aliases the new task should have, using [this](#alias-syntax) syntax. By default empty.
- `[task_attribute_value_mapping]`: Task attributes with associated values, using [this](#mapping-syntax) syntax. By default empty.

Create a new task with the specified name, aliases and task attribute value mapping. 

The community rank **helper** is required.

---

#### `/task nuke`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of the task.

Delete the specified task. This will also delete all associated user data!

The community rank **moderator** is required.

---

#### `/task edit name`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of the task.
- `<new_name>`: The new name the task should be renamed to.

Rename the specified task. 

The community rank **moderator** is required.

---

#### `/task edit aliases`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of the task.
- `<new_aliases>`: The new aliases to replace the previous aliases of the task with, using [this](#alias-syntax) syntax.

Replace the previous aliases of the specified task with the ones specified.

The community rank **moderator** is required.

---

#### `/task edit attribute_value_mapping`
- `<list>`: The name of the list in which the task should be searched for.
- `<task>`: The name or alias of the task.
- `[new_attribute_value_mapping]`: The new task attribute value mapping to replace the previous task attribute value mapping of the task with, using [this](#mapping-syntax) syntax. By default empty.

Replace the previous task attribute value mapping of the specified task with the one specified.

The community rank **moderator** is required.

### User

#### `/user info`
- `[user]`: The user of whom to get info from. By default the interacting user.

Show the name, selected list and ranks of the specified user. If the command is not executed in a server that is connected to a community, the community specific information is left out.

---

#### `/users browse`

Show the name, selected list and ranks of all users in the community.

**Coming soon...**

---

#### `/users browse_task`
- `<task>`: The name or alias of the task of which the user attribute values should be taken from.
- `[given]`: Whether to only show the users that have been given the task or to only show the users that are missing it. By default true (show only the users with the task given). 
- `[list]`: The name of the list in which the task should be searched for. By default the interacting user's selected list, if the user has it set, otherwise the community's default selected list.

Show the name, ranks, selected list and user attribute values of all users in the community that have been given the specified task.
If `[given]` is false, only show the users that have not yet been given the task (and therefore don't show any user attributes either).

**Coming soon...**

---

#### `/user edit_selected_list`
- `[list]`: The name of the list that should be set as the default. If not specified, this will unset the user's selected list.
- `[user]`: The user for whom the list should be set as the default. By default the interacting user.

Set the selected list of the specified user. This is the list that is automatically selected whenever that user executes a command with a `[list]` parameter, but doesn't explicitly specify it.

If the specified user is somebody other than the interacting user, the community rank **moderator** is required.

### User (Privileged)

#### `/user edit_community_rank`
- `<user>`: The user of whom the community rank should be set.
- `<community_rank>`: The community rank that should be set for the user.

Set the specified user's community rank to the one specified.

The interacting user's community rank must be higher than the community rank of the specified user and the interacting user may only set the community rank of the specified user to a community rank lower than their own.

---

#### `/user edit_jumpedia_rank`
- `<user>`: The user of whom the Jumpedia rank should be set.
- `<jumpedia_rank>`: The Jumpedia rank that should be set for the user.

Set the specified user's Jumpedia rank to the one specified.

The interacting user's Jumpedia rank must be higher than the Jumpedia rank of the specified user and the interacting user may only set the Jumpedia rank of the specified user to a Jumpedia rank lower than their own.

## Structures

### Community
A community is the structure that stores all information about your, well, community. Every Discord server with the Jumpedia bot on it can be [connected](#community-connect) to one community at a time, but the amount of Discord servers that can be connected to a community is limitless. This way, a Discord server may only represent one specific community, but the community may also spread across multiple Discord servers, if required.

Every community has any amount of lists. One of these lists may be [selected as the default](#community-edit-default_selected_list). When a user doesn't have a list selected themselves and they don't explicitly specify one in a command, the community's default will be used.

### List
A list is the structure that holds tasks and attributes. It can be compared to a spreadsheet, where the attributes are the columns and the tasks are the rows.

Here is an example:

Id  | Name               | Alias               | Difficulty
----|--------------------|---------------------|-----------
`1` | `Do your homework` | `Homework`<br/>`HW` | `9/10`
`2` | `Do the laundry`   | `Laundry`           | `5/10`

This is also exactly how the [task browse](#task-browse) command previews data.


### Attribute
An attribute is the "column" that describes which kind of data a task may contain (see the table above) in each cell of a task's row. 

All attributes have the following properties...

#### Name
The primary identifier of the attribute. It must be unique across all other attributes' names and aliases in the same list.

#### Alias
Secondary identifiers of the attribute. They must be unique across all other attributes' names and aliases in the same list.

#### Slot Type
The type each slot of a task's value must fit. May be either `Boolean (true/false)`, `Integer`, `Decimal` or `String (Text)`. 

#### Position
A number which attributes are ordered by when using the [task info](#task-info) or [task browse](#task-browse) command. Currently not editable, but coming soon...

#### Min Slot Count
The minimum amount of slots each value of a task may have for this attribute. When [creating an attribute](#attribute-create), this is forced to be 0, but may be [edited](#attribute-edit-min_and_max_slot_count) after creation.

#### Max Slot Count
The maximum amount of slots each value of a task may have for this attribute.

#### Collection 
A set of all allowed slots a task can have for this attribute.
Each entry of the collection contains a value and aliases for that value. 
Currently not editable, but coming soon... (high priority)

#### Type 
Each attribute also has a type. This is listed as the last property here because it requires knowledge of the previous properties. The three types are:

##### Static Attribute
A static attribute is a special kind of attribute. It cannot manually be created or deleted, but edited in a few limited ways. Whenever a list is created, the three static attributes `Id`, `Name` and `Alias` get created automatically as well. 

For the static attribute `Id` every task has completely unique positive integer value, that is automatically assigned on creation of said task. No two tasks across all of Jumpedia ever share the same ID. 

The static attributes `Name` and `Alias` work the same way the properties `Name` and `Alias` do for attributes. `Name` is the primary identifier to lookup tasks with, while `Alias` includes all secondary identifiers. All names and aliases must be unique across a list.

Here are the default properties of all static attributes:
Name    | Alias | Type               | Slot Type       | Position | Min Slot Count | Max Slot Count    | Collection
--------|-------|--------------------|-----------------|----------|----------------|-------------------|-----------
`Id`    |       | `Static Attribute` | `Integer`       | `1`      | `1`            | `1`               |
`Name`  |       | `Static Attribute` | `String (Text)` | `2`      | `1`            | `1`               |
`Alias` |       | `Static Attribute` | `String (Text)` | `3`      | `1`            | Community's Max   |


###### Task Attribute
A task attribute is similar to a static attribute, but it doesn't have special treatment. It can be created, edited and deleted as required. 

For example, a list might contain the following task attribute:
Name         | Alias | Type             | Slot Type | Position | Min Slot Count | Max Slot Count | Collection         
-------------|-------|------------------|-----------|----------|----------------|----------------|---------------------
`Difficulty` | `D`   | `Task Attribute` | `Integer` | 4        | 1              | 1              | (`1`)<br/>(`2`)<br/>(`3`)<br/>(`4`)<br/>(`5`)

This task attribute has the following properties:
- The attribute's name is `Difficulty` and it has one alias, `D`. 
- It is (obviously) a task attribute.
- It requires all slots in a task's value to be an integer, but due to it having a collection also requires any value to be exactly either `1`, `2`, `3`, `4` or `5`.
- It is sorted after the attribute with the position `3` and before the attribute with the position `5`.
- A task's value for this attribute has exactly one slot, because the min and max slot count is 1.

In a nutshell: A task is required (min slot count > 0) to have a value with exactly one slot consisting of any integer from 1 to 5 for this task attribute.

The task attribute contains one value per task, unlike user attributes...

###### User Attribute
A user attribute is an attribute that contains one value per task per user. In other words: it lets each user assign their own value to tasks they completed and then [give themselves](#task-give).

For example, a list might contain the following user attribute:
Name    | Alias           | Type             | Slot Type       | Position | Min Slot Count | Max Slot Count | Collection         
--------|-----------------|------------------|-----------------|----------|----------------|----------------|---------------------
`Proof` | `Prove`<br/>`P` | `User Attribute` | `String (Text)` | 12       | 0              | 2              |

This user attribute has the following properties:
- The attribute's name is `Proof` and it has the aliases `Prove` and `P`. 
- It is (obviously) a user attribute.
- It requires all slots in a task's value to be any kind of text.
- It is sorted after the attribute with the position `11` and before the attribute with the position `13`.
- A user's value for this attribute must contain 0 to 2 slots (inclusive). 

In a nutshell: When a user [gives themselves a task](#task-give), they can decide to either set no proof or to add up to 2 proof links for this user attribute. The proof may be any kind of string, with no restrictions.


### Task
Tasks are the thing users in the community should aim to complete. This can be anything from challenges, speedruns, trickjumps, quests or anything else completable.

A task can be thought of as a row in a spreadsheet, while attributes are the columns that describe what kind of value should go into each cell of the task's row.

Whenever a user completes a task, they can use the [task give](#task-give) command to give themselves that specific task. This marks the task as completed for that user.

### User
A user is any person interacting with Jumpedia. Jumpedia stores the following properties about a user:
- Their Discord ID
- Their global display name, if given, otherwise their unique @ name.

Users are identified by their Discord ID, so make sure to not lose your Discord account!
The name is tracked to mention users in messages and it is the last name Jumpedia saw of that user.

For a user inside of a specific community, Jumpedia stores additional data:
- Their selected list 
- All of their task data

Most importantly, Jumpedia keeps track of users' ranks...

#### Server Rank
Server ranks are not managed, but only read by Jumpedia. They describe the power a user already has in a Discord server.

The following server ranks exist:
Name          | Description                                                    | Privileges
--------------|----------------------------------------------------------------|----------------------------------------------------------------------------------
User          | Basic user without any privileges                              | None
Administrator | User that has administrator rights on the given Discord server | Currently none
Owner         | The owner of a Discord server                                  | [Connect](#community-connect) and [disconnect](#community-disconnect) a community


They have no permission across Jumpedia's ecosystem but can be used to manage how Discord servers are able to interact with Jumpedia.


#### Community Rank
A community rank is the rank a user has inside of a specific community.

The following community ranks exist:
Name          | Description                                                    | Privileges
--------------|----------------------------------------------------------------|----------------------------------------------------------
User          | Basic user without any privileges                              | None
Helper        | User with no destructive power, but the ability to help        | Create tasks
Moderator     | User with the ability to affect other users and managing power | Edit task data of other users and edit tasks
Administrator | User with almost full power inside of a community              | Edit everything about the community, lists and attributes
Owner         | The owner of a community                                       | Delete the community


#### Jumpedia Rank
Jumpedia ranks are the most powerful kind of rank. Users with these ranks are Jumpedia staff and have power across communities. Any Jumpedia rank (besides user) is more powerful than any other kind of rank. This allows Jumpedia staff to support communities that are facing issues immediately.

The following Jumpedia ranks exist:
Name               | Description                                                     | Privileges
-------------------|-----------------------------------------------------------------|---------------------------
User               | Basic user without any privileges                               | None
Meta Administrator | User with full power across all of Jumpedia and its communities | All of them
JoniKauf           | The rank of JoniKauf                                            | Manage meta administrators



## Syntax
For some command parameters more than just a single value is required to be entered. For this reason, multiple syntaxes exist to fit the shape of the data that is required.

For any syntax that requires inputting attributes or collection values, their aliases may be used as well.

> [!IMPORTANT]
> Whenever it is required to only enter a single value into a parameter, like a `name` for example, the user must type it without any quotation marks or other special symbols. Otherwise, these special symbols are included in the actual data.

Every syntax has the same basic rules:

#### 1. Special Symbols

All syntaxes share a common set of special symbols, though individual syntaxes may define additional ones.

If a string of text contains any special symbol, the syntax will interpret it as having a special meaning instead of treating it as literal text. To ensure the text is interpreted correctly, the string must be wrapped in quotation marks.

The base special symbols are:

1. Any kind of space  
2. Any quotation mark (`'` or `"`)

---

#### 2. Keywords

Each syntax may define keywords that are not interpreted literally, but instead have a predefined meaning.

If a sequence of characters should be interpreted as a literal string rather than as a keyword, it must be enclosed in quotation marks as well.

---

#### 3. Quoted Strings

Quotation marks are required when a string:

- Contains special symbols  
- Matches a keyword  

Either single quotes (`'`) or double quotes (`"`) may be used, but the string must end with the same quotation mark it starts with.

To include the same quotation mark inside a quoted string, it must be escaped using a backslash (`\`).  
To include a backslash itself, it must also be escaped with another backslash.

**Example:**

```text
"This is a \"cool\" string of text \\o/"
```

This will be interpreted as:

```text
This is a "cool" string of text \o/
```

If escaping is done incorrectly, an error will be returned.

> [!TIP]  
> When quotation marks are needed inside a string, the other quotation mark type can be used to wrap the string instead of escaping.  
>  
> Examples:  
> - `"Bob's House"`  
> - `'They called him "Mark"'`

### Alias Syntax
The alias syntax allows the user to input one to any number of aliases.

#### Special symbols or keywords:
This syntax has no additional special symbols or keywords. 

#### How it works:
The user must simply chain strings in a row.

#### Example:
`Alias1 "Alias2 With Spaces" Alias3 "Alias4"`


A task with this string in `aliases` specified will have the following aliases:
- `Alias1`
- `Alias2 With Spaces`
- `Alias3`
- `Alias4`


### Mapping Syntax
The mapping syntax allows the user to input anything that associates a unique key with zero or more values. For example, when a user [gives themselves a task](#task-give), they can use this syntax to specify their user attribute value mapping.

#### Special symbols or keywords:
This syntax additionally has the special symbols `(`, `)` and `:`, but no keywords.

#### How it works:
A key-value pair starts with the key, which is always identified by a leading colon (`:`). It may then be followed by values (exactly like the [alias syntax](#alias-syntax)) until the next key-value pair is identified (via an opening parenthesis (`(`) or a colon (`:`)) or the string ends. A key-value pair may be wrapped in parentheses (`()`). 

#### Example:
`(Proof: "my proof link1" "my proof link 2") Rating: "5/5 Stars" Notes:`

The example above represents a user attribute value mapping when a user gives themselves a task.
- To the user attribute `Proof` they assigned two pseudo proofs
- To the user attribute `Rating` they assigned one rating, `5/5 Stars`
- To the user attribute `Notes` they assigned nothing

In any case, the parentheses could have been included or removed, whatever may be preferred.

### Sort Syntax
The sort syntax allows the user to input a sort for when they are browsing tasks.

#### Special symbols or keywords:
This syntax additionally has the special symbols `+` and `-`, but no keywords.

#### How it works:
This syntax works exactly like the [alias syntax](#alias-syntax), but a plus (`+`) or minus (`-`) must be placed before every string.

Plus (`+`) means to sort by that attribute in ascending order, while (`-`) means to sort by that attribute in descending order. The first attribute specified is the primary sort, but if the value for two tasks is the same, then the secondary sort is used between them and so on. For attributes with collections, attributes get sorted by the values' positions in the collection instead of the actual value. 

#### Example:
`+Difficulty -Name`

This example sorts all tasks by difficulty in ascending order. All tasks with the same difficulty will be sorted by their name in descending order.


### Filter Syntax
The filter syntax is the most powerful syntax and therefore the most complex. It allows the user to filter data in any way they may desire, using a compact syntax.

#### Special symbols or keywords:
This syntax additionally has the special symbols `(`, `)` and `_`. It also has the keywords `and`, `or`, `is`, `is not`, `<`, `<=`, `>` and `>=`.

#### How it works:
This syntax works by alternating comparisons with boolean operators (`and`, `or`), to represent boolean logic that should be checked for each task. A comparison is an attribute, followed by a comparison operator (`is`, `is not`, `<`, `<=`, `>`, `>=`), followed by a value. The underscore (`_`), called the empty value symbol, can be used with the operators `is` and `is not` to check whether a task's value is empty. Parentheses (`()`) can be used around a singular or multiple comparisons to change in which order boolean operators are applied, similar to how they are used in maths. By default, the `and` boolean operator has a higher precedence than the `or` boolean operator.

#### Example:
`(Difficulty < 9/10 or Name >= Y) and (Proof is not _)`

For a task to **not** be filtered out, the following must be true:
The difficulty must be lower than 9/10 OR the name must be lexicographically higher than `Y` or exactly equal to `Y`. If that is the case AND proof is also non-empty, only then will the task be included.


## Credits
A huge thanks to the following people for helping me on the way to build Jumpedia:
- xKilimili
- Xeter
- Jess
- The SMO Trickjumping staff team
- And many more...
