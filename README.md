# rest-api

### Design (DB structure)
`name.json`
```jsonc
  "name_of_plugin": 2137 // name: pgid
```

`data.json`
```jsonc
  2137: {
    "name": "Full name of plugin",
    "icon": "99999AF", // icon: cid
    "license": "GPL-3.0-or-later", // license: spdx
    "archived": false,
    "gitUrl": "https://github.com/mbledkowski/name_of_plugin.git",
    "description": "The best plugin in the entire world", // description: short description
    "data": [{
      "id": "213769", // if other than spigot/bukkit then optional
      "type": "spigot",
      "url": "https://spigotmc.org/resources/213769",
      "name": "Full name of plugin - The best plugin in the fing world", // optional
      "description": "The best plugin in the world. Download right now.", // optional
      "archived": false, // optional for custom websites
      "author": "Slayer420", // optional for custom websites
      "icon": "666FFF", // optional, icon: cid
      "numberOfDownloads": 2115, // optional for other than spigot/bukkit
      "releasesPageUrl": "https://spigotmc.org/resources/213769/releases" // optional for custom
    }, {
      "type": "github",
      "url": "https://github.com/mbledkowski/name_of_plugin",
      "archived" false,
      "author": "mbledkowski",
      "releasesPageUrl": "https://github.com/mbledkowski/name_of_plugin/releases"
    }]
  }
```

`versions.json`
```jsonc
  2137: [
    "2.1.3.7": {
      "about": [{
        "type": "github",
        "sourceUrl": "https://github.com/mbledkowski/name_of_plugin/releases/2137",
        "downloadUrl": "https://github.com/mbledkowski/name_of_plugin/releases/2137/plugin.jar",
      }, {
        "type": "spigot",
        "sourceUrl": "https://spigotmc.org/resources/213769/releases/2137",
        "downloadUrl": "https://spigotmc.org/resources/213769/releases/2137/plugin.jar",
        "rating": 2, // scale 0-10
        "downloads": 5000,
      }],
      "cid": "777AAA",
      "supportedApis": ["spigot", "paper", "glowkit"],
      "dependencies": ["essentialsx-core"]
    }
  ]
```

### Design (API endpoints)

#### https://pluget.net/api/v1
- Description: The main url to access the REST-API.

#### /all
- Description: Returns all the data. One page could show a maximum of 20 plugins for example.
- Example: https://pluget.com/api/v1/all?pageID=0&pagesShown=5
- Required params: pageID, pagesShown
- Optional params:

#### /find
- Description: Returns an array containing only the objects that match the query.
- Examples:
  - https://pluget.net/api/v1/find?author=queryString 
  - https://pluget.net/api/v1/find?name=queryString
  - https://pluget.net/api/v1/find?pgid=queryString
  - https://pluget.net/api/v1/find?name=queryString&author=queryString
- Required params (at least one): author, name, pgid

# TODO:

[![Tests](https://github.com/ndelvalle/rustapi/actions/workflows/ci.yml/badge.svg?branch=master)](https://github.com/ndelvalle/rustapi/actions/workflows/ci.yml)

RESTful API template built with Rust lang. It uses [MongoDB](https://docs.mongodb.com/)
database and [Axum](https://github.com/tokio-rs/axum) HTTP framework.

### Requirements

- [Rust](https://www.rust-lang.org/tools/install)
- [MongoDB](https://docs.mongodb.com/manual/installation/)

### How to

To use this template as your project starting point, click "Use this template" at the top of this page, or click [here](https://github.com/ndelvalle/rustapi/generate).

### Features

* Authentication. Based on [jsonwebtoken](https://github.com/Keats/jsonwebtoken)
* Layered configuration system. Based on [config-rs](https://github.com/mehcode/config-rs)
* Logs. Based on [tracing](https://github.com/tokio-rs/tracing)
* Error handling
* CI Jobs based on Github actions
* E2E Tests
* Dependabot configuration

### Project structure

```bash
├── Cargo.toml
├── README.md
├── config
│   ├── default.json    # Default configuration
│   └── production.json # Production configuration (Overwrites the default)
├── rustfmt.toml
└── src
    ├── context.rs      # Shared state and functionality across the APP
    ├── database.rs
    ├── errors.rs
    ├── lib             # Helpers not related to the business model
    │   ├── authenticate_request.rs
    │   ├── date.rs
    │   ├── mod.rs
    │   ├── models.rs   # Base Database Model trait
    │   ├── to_object_id.rs
    │   └── token.rs
    ├── logger.rs
    ├── main.rs
    ├── models
    │   ├── cat.rs
    │   ├── mod.rs
    │   └── user.rs
    ├── routes
    │   ├── cat.rs
    │   ├── mod.rs
    │   └── user.rs
    └── settings.rs
```

## Contributing

Contributors are welcome, please fork and send pull requests! If you find a bug
or have any ideas on how to improve this project please submit an issue.
