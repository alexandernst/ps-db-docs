## Description

This table stores the addresses of customers, manufacturers, suppliers and
warehouses.

## Rows

* `id_address` - `PK` - the ID of the address.
* `id_country` - `K` - the ID of the country (in the `ps_country` and
`ps_country_lang` tables).
* `id_state` - `K` - the ID of the state (in the `ps_state` table).
* `id_customer` - `K` - the ID of the customer (in the `ps_customer` table) or 0
if the address doesn't belong to a customer.
* `id_manufacturer` - `K` - the ID of the manufacturer (in the `ps_manufacturer`
and `ps_manufacturer_lang` tables) or 0 if the address doesn't belong to a
manufacturer.
* `id_supplier` - `K` - the ID of the supplier (in the `ps_supplier` and
`ps_supplier_lang` tables) or 0 if the address doesn't belong to a supplier.
* `id_warehouse` - `K` - the ID of the warehouse (in the `ps_warehouse` table)
or 0 if the address doesn't belong to a warehouse.
* `alias` - text.
* `company` - text.
* `lastname` - text.
* `firstname` - text.
* `address1` - text.
* `address2` - text.
* `postcode` - text.
* `city` - text.
* `other` - text.
* `phone` - text.
* `phone_mobile` - text.
* `vat_number` - text.
* `dni` - text.
* `date_add` - datetime.
* `date_upd` - datetime.
* `active` - boolean.
* `deleted` - boolean.

## Notes

* Customers can't have two addresses with the same alias (even if the alias
field is a plan `VARCHAR` field). However, a customer can create two exact
copies of the same address with their alias being the only difference.

* A customer's address can't be *deactivated*. It can only be removed (check
next point). That means that the `active` field is pretty much useless.

* A customer can delete his/her address(es) and two things can happen. If the
address that is being deleted hasn't been used in any order, it will be deleted
from the database. Else, the address's `deleted` field will be set to `1`. Also
note that the `active` field will remain set to `1`.

### TODO: Manufacturer notes
### TODO: Supplier notes
### TODO: Warehouse notes

* Note that in order to be able to create warehouses, you must enable the
`Advanced stock management` option located in `Preferences -> Products`.
