# Development roadmap

This document serves as a sort of ToDo list for the Alexandria project.

## v0.1.0

* API

  - [ ] Implement type inheritance
  - [ ] Implement relationship attributes
  - [ ] Implement predefined value constraints for attributes
  - [ ] Implement updates to CIs after changes to CI type schema
  - [ ] Add cleanup of orphaned collections during `blank_state.sh`
  - [ ] Implement attribute indexing options
  - [ ] Implement DB statistics methods such as:
    - [ ] Collection sizes
    - [ ] CI Counts
    - [ ] Index sizes
  - [ ] Improve API authentication
  - [ ] Improve logging
  - [ ] Implement error reporting via RESTful API
  - [ ] Packaging
  - [ ] Implement basic permissions for Root/Dashboard user
  - [ ] Implement HTTP PATCH
  - [ ] Implement HTTP caching
  - [ ] Fix URLs to prevent collisions across users and tenants for cachable
        content
  - [ ] Implement attribute selectors for all resource types
  - [ ] Add `CreatedDate` and `ModifiedDate` to JSON output
  - [ ] Implement change audit logging

* CLI

  - [x] Implement batch operation scripting
  - [ ] CSV data import and export
  - [ ] Remove dependency on `cli` library
  - [ ] Implement unit testing
  - [ ] Rename binary output to `alex`
  - [ ] Packaging

* Dashboard

  - [x] Implement internationalization in JS and Revel
  - [ ] Implement form validation
  - [ ] Prevent navigate-away from unsaved changes
  - [ ] Migrate data bindings to Angular JS
  - [ ] Implement unit testing
  - [ ] Fix installation error on `go get`
  - [ ] Packaging
  - [ ] Implement account management page
  - [ ] Improve logging
  - [ ] Add CI editor interface
  - [ ] Add CI browser interface
  - [ ] Find someone who has half a talent for GUI/UX
  - [ ] Allow users to retreive their API key

* Documentation

  - [ ] Integration with Jekyll
  - [ ] Document attribute types and options
  - [ ] Add theming

* Vagrant/Puppet

  - [ ] Improve Go and Git Puppet modules
  - [ ] Finalize and publish Puppet module

* Other

  - [ ] How to implement data connectors
    
    * Pluggability?
    * Staging area?
    * Association with external IDs?

  - [ ] Reassess open source license selection
  - [ ] Confirm licensing constraints of 3rd party libraries

## v0.2.0...

- [ ] Search by CI attribute values
- [ ] Implement granular permissions
- [ ] LDAP integration
- [ ] OAuth integration
- [ ] Integration with SysInv
- [ ] Data connector for XML
- [ ] Data connector for JSON
- [ ] Data connector for CSV
- [ ] Data connector for PostgreSQL
- [ ] Data connector for MySQL
- [ ] Data connector for Microsoft SQL Server
- [ ] Abstract database integration to support other DBs
- [ ] Integration with Nagios for provisioning hosts and services
- [ ] Integration with Zabbix for provisioning hosts and templates
- [ ] Integration with Puppet for Hieradata, facter, DB, etc.
