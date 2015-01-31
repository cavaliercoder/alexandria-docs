---
layout: page
title: Concepts
permalink: /concepts/
---

Alexandria CMDB attempts to implement a CMDB as described in the ITIL
framework.

## Configuration Item Types

A Configuration Item Type (CI Type) describes the classification of a single
entity type such as a person, a business service or a server. The CI Type
describes the attributes and constraints that apply to all configuration items
of that type.

CI Type attributes are denoted using "dot notation" such as `Person.Name`.
Attributes can also be nested within a type such as `Person.Contacts.Email`.

CI Types can *inherit* the attributes and constraints from other CI Types to
ease administration. For example, you might define a simple `Person` type that
contains only the most common attributes of a person such as `Name` and `Date
of birth`. You could then create a `Customer` CI type which inherits from
`Person` but adds attributes specific to a customer, such as `Contract expiry`
or `Entitlements`. You might add another type `Employee` which also inherits
from `Person` but include attributes such as `Start date` and `Title`.

Relationships between CI types are described using attributes and can be
`one-to-one`, `one-to-many` or `many-to-many` relationships. The relationships
can optionally be described on both the source and destination type.

As an example, you might define a `one-to-many` relationship between
`Employee.TechnicalOwnerOf` and `Server.TechnicalOwner` where the
`TechnicalOwnerOf` attribute of an `Employee` CI would contain multiple
references to CIs of type 'Server' and the `TechnicalOwner` attribute on those
`Servers` would include a single reference to the owning `Employee`.

CI Types can define constraints on the attribute values entered for CIs
assigned to those types. Constraints might include minimum and maximum values,
regular expressions or a predefined list of possible values.

Attribute constraints are useful for enforcing the quality of data entered in
for a CI. For example you could ensure an `EmailAddress` attribute contains
a valid email address using a regular expression pattern.

### Configuration Items

A Configuration Item (CI) describes a single instance of a CI Type and
represents the lifecycle of that CI in your environment. A CI can only be
associated with a single CI Type.

CIs may contain values for the attributes described in the associated CI Type
and the values can be constrained by rules defined in the CI Type.

### Collections
Every CI Type is provisioned a single collection which stores all of the CIs of
that type. A collection acts like a collection in a document database or a
table in an RDBMS.

### Organisational units
An Organisational unit (OU or OrgUnit) describes a single container in a
hierarchical structure of CIs. OrgUnits can be used to separate CIs into
managable groupings to simplify tasks such as delegation of permissions,
administrative boundaries or user views.

An OrgUnit can contain multiple types of CIs. CIs can be manually assigned or
"pinned" to an OrgUnit or the OrgUnit can be automatically populated using a
filter. OrgUnits can also define contraints on the CIs that may be assigned to
them such as only allowing `Server` CIs with a predefined `TechnicalOwner`
attribute value.

