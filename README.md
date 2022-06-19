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
      "id": 213769, // if other than spigot/bukkit then optional
      "type": "spigot",
      "url": "https://spigotmc.org/resources/213769",
      "name": "Full name of plugin - The best plugin in the fing world", // optional
      "description": "The best plugin in the world. Download right now.", // optional
      "archived": false, // optional for custom websites
      "authors": ["Slayer420"], // optional for custom websites
      "icon": "666FFF", // optional, icon: cid
      "iconUrl": "https://www.spigotmc.org/data/resource_icons/9/9089.jpg"
      "numberOfDownloads": 2115, // optional for other than spigot/bukkit
      "releasesPageUrl": "https://spigotmc.org/resources/213769/releases" // optional for custom
    }, {
      "type": "github",
      "url": "https://github.com/mbledkowski/name_of_plugin",
      "archived" false,
      "authors": ["mbledkowski"],
      "numberOfStars": 1400, //optional for other than github/gitlab
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

#### https://api.pluget.net/v1
- Description: The main url to access the REST-API.

#### /all
- Description: Returns all the data. One page could show a maximum of 20 plugins.
- Example: https://api.pluget.net/v1/all?pageID=0&pagesShown=5
- Required params: pageID, pagesShown
- Optional params:

#### /find
- Description: Returns an array containing only the objects that match the query.
- Examples:
  - https://api.pluget.net/v1/find?author=queryString 
  - https://api.pluget.net/v1/find?name=queryString
  - https://api.pluget.net/v1/find?pgid=queryString
  - https://api.pluget.net/v1/find?name=queryString&author=queryString
- Required params (at least one): author, name, pgid

### Requirements

- [Rust](https://www.rust-lang.org/tools/install)

  It uses json files as a database and [Rocket](https://github.com/SergioBenitez/Rocket) HTTP framework.

### 🔧 Building and Testing

#### debug mode
> cargo run

#### release mode
> cargo build --release && cargo run --release

#### unit testing
> cargo test

### Project structure (to be updated)

```bash
├── Cargo.toml
├── README.md
├── Rocket.toml
└── src
    ├── db
    │   ├── customer.rs
    │   └── mod.rs
    ├── errors
    │   ├── mod.rs
    │   └── response.rs
    ├── fairings
    │   ├── cors.rs
    │   ├── counter.rs
    │   └── mod.rs
    ├── main.rs
    ├── models
    │   ├── customer.rs
    │   ├── mod.rs
    │   └── response.rs
    ├── request_guards
    │   ├── basic.rs
    │   └── mod.rs
    ├── routes
    │   ├── customer.rs
    │   └── mod.rs
    └── tests
        └── mod.rs
```

## Contributing

Contributors are welcome, please fork and send pull requests! If you find a bug
or have any ideas on how to improve this project please submit an issue.
