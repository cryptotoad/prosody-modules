# Introduction #

On a server with public registration it is usually desirable to prevent registration of certain "reserved" accounts, such as "admin".

This plugin allows you to reserve individual usernames, or those matching certain patterns. It also allows you to ensure that usernames conform to a certain pattern.

# Configuration #

Enable the module as any other:

```
    modules_enabled = {
        "block_registrations";
    }
```

You can then set some options to configure your desired policy:

| **Option** | **Default** | **Description** |
|:-----------|:------------|:----------------|
| block\_registrations\_users | { "admin" } | A list of reserved usernames |
| block\_registrations\_matching | { } | A list of patterns matching reserved usernames (slower than block\_registrations\_users) |
| block\_registrations\_allow | nil | A pattern that registered user accounts MUST match to be allowed |

Some examples:

```
    block_registrations_users = { "admin", "root", "xmpp" }
    block_registrations_matching = {
        "master$" -- matches postmaster, hostmaster, webmaster, etc.
    }
    block_registrations_allow = "^[a-zA-Z0-9_-.]$" -- Allow only simple ASCII characters in usernames
```

# Compatibility #
| 0.9 | Works |
|:----|:------|
| 0.8 | Should work |