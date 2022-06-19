# rest-api

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
