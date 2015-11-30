This table controls the access to the `tabs` each `group of users` has.

A `tab` is each of the sections of the administration area, such as the
`Dashboard`, the `Catalog` section, the `Orders` section, etc...

A `group of users` is what PrestaShop calls `Profiles` (in the `Administration`
tab). There are 4 by default: `SuperAdmin`, `Logistician`, `Translator` and
`Salesman`.

Each row of `ps_access` contains a set of rules for a specific tab and a
specific group of users. The set of rules is:

* Can the group `view` that tab? (Can the group view orders?)
* Can the group `add` in that tab? (Can the group add products?)
* Can the group `edit` in that tab? (Can the group edit shipping methods)
* Can the group `delete` in that tab? (Can the group delete addresses)

## Rows

* `id_profile` - the ID of the user group (in the `ps_profile` and
`ps_profile_lang` tables) that the rule applies to.
* `id_tab` - the ID of the tab (in the `ps_tab` and `ps_tab_lang` tables) that
the rule applies to.
* `view` - boolean.
* `add` - boolean.
* `edit` - boolean.
* `delete` - boolean.

## Notes
* The rules in the tables are excluding, meaning that if a rule for a specific
group and a specific tab <b>isn't</b> found, a default `DENY` or `NOT ALLOWED`
will be assumed by PrestaShop.

* If a tab can't be `viewed` by a group of users, all the children tabs won't be
visible in the administration menu, but they still could be accessed via URL if
they have the right set of rules.

* When a user of a certain group creates a new tab, the tab will be created with
`GRANT` permissions for that group and all superior groups. Example, if an user
from group 3 creates a new tab, all users of group 3, 2 and 1 will be able
to view, add, edit and delete that tab.
