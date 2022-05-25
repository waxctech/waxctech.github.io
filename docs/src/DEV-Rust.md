# Statistics as of 2022 Jan
Rust developers in discord - around 40k active ~ 0.2%
total dev 25m worldwide -> 50% JS, 50% Java & Python.

# modern programming focus
- speed, stability, concurrency, functional programming
- 
# install rustup
`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`
# update rustup
`rustup update`
# install rust analyzer VCode plugin
`https://marketplace.visualstudio.com/items?itemName=matklad.rust-analyzer`
install better toml, grcov, evcxr plugin

# VC themes
- Darcula Theme

# intellij plugin
* toml and rust, grcov plugin, setup cargo project, git flow integration plus

# intellij theme
- install material darkers theme


# cargo new project
`cargo new hello_world --bin --vcs git`

# print out struct
`#[derive(Debug)]`
`println!("{:?}", user);`

# training path
0. [cheat sheet](https://cheats.rs/)
1. [overview - Rust in Motion](https://learning.oreilly.com/videos/rust-in-motion/10000MNLV201742/)
2. [MSFT training 5.5h](https://docs.microsoft.com/en-gb/learn/paths/rust-first-steps/)
3. [The book](https://doc.rust-lang.org/book/) & [tour of rust](https://tourofrust.com/)
4. [Advance Rust for Rustaceans](https://learning.oreilly.com/library/view/rust-for-rustaceans/9781098129828/)
5. [basic Rust cook book](https://rust-lang-nursery.github.io/rust-cookbook/intro.html)
6. [complete Rust by Example](https://doc.rust-lang.org/rust-by-example/) & [extended](https://rust-by-example-ext.com/)
7. [Rust Design Pattern](https://rust-unofficial.github.io/patterns/intro.html)
8. [CS242 Programming Languages (in Rust)](https://stanford-cs242.github.io/f19/)
9. [machine learning in Rust](https://learning.oreilly.com/library/view/practical-machine-learning/9781484251218/)
10. [hacking in Rust](https://kerkour.com/black-hat-rust)
11. [Network Programming with Rust](https://learning.oreilly.com/library/view/network-programming-with/9781788624893/) - parsing JSON with serde, networking, http, tcp, udp with tokio
12. [MEAP - Rust Web Development](https://www.manning.com/books/rust-web-development?query=rust)
13. [downstream service - Zero to production in rust](https://www.zero2prod.com/index.html?country=Taiwan&discount_code=SEA60) 
14. [microservice in AWS](https://www.amazon.co.uk/Hands-Microservices-Rust-2018-Scalable/dp/1789342759/ref=sr_1_6?s=books&ie=UTF8&qid=1545340800&sr=1-6&keywords=rust) as hyper, Tokio, and Actix, REST, Docker, Reactive, AWS lamdba

# video course
1. [24h intermediate - crust of rust](https://www.youtube.com/playlist?list=PLqbS7AVVErFiWDOAVrPt7aYmnuuOLYvOa)
   -lifetime, macros, iterators, smart pointers, channels, sort & algro, subtypes, variance, drop check, atomics, mem ordering, dispatch, await, function, trait
2. [7h data structure and algorithm](https://www.packtpub.com/product/hands-on-data-structures-and-algorithms-in-rust-video/9781839211942)
   - str, string, complexity, & sorting, linked list & binary trees, graph, hashmap, entity component, persistence. 
3. [3h CLI search, parser, chat, blog, tokio, actix, db](https://www.packtpub.com/product/rust-projects-video/9781788628549)
4. [1h real-time service - chat with tokio](https://livevideo.manning.com/module/537_1_1/creating-chat-server-with-async-rust-and-tokio-lily-mara-nate/author-talk/creating-a-chat-server-with-async-rust-and-tokio?)
5. [6h upstream service - advance data stream in Rust](https://www.manning.com/liveproject/data-streaming-with-async-rust?query=rust)
6. [7h process - build HTTP server](https://www.udemy.com/course/rust-fundamentals/)
7. [12h batch job - Build a Stock-Tracking CLI With Async Streams in Rust](https://www.manning.com/liveprojectseries/async-streams-in-rust-ser)
8. [3h System programming by Nathan Stocks](https://www.udemy.com/course/ultimate-rust-crash-course/)
9. [3h game development by Nathan Stocks](https://www.udemy.com/course/ultimate-rust-2/?referralCode=8ED694EBE5637F954414)
10. [2h reusable code by Shing Lyu - functional, generics, std](https://www.packtpub.com/product/building-reusable-code-with-rust-video/9781788399524)
11. [3h Eduonix Learning - Rc and ARC, trait, error handling, serde](https://www.packtpub.com/product/introduction-to-rust-programming-video/9781800565623)

# Reference
[rust forge - docs for rust lang](https://forge.rust-lang.org/index.html)
[rust compiler development](https://forge.rust-lang.org/index.html)
[rust internal forum](https://internals.rust-lang.org/)
[rust exercises](https://github.com/rust-lang/rustlings)
[Rust Awesome List](https://github.com/rust-unofficial/awesome-rust)
[Are we web yet](https://www.arewewebyet.org/)
[web framework comparison](https://github.com/flosse/rust-web-framework-comparison)
[book list](https://github.com/sger/RustBooks)
[Finite State Machine](https://github.com/eugene-babichenko/rust-fsm)
[state machine pattern](https://hoverbear.org/blog/rust-state-machine-pattern/)

# cloud framework 
[rust serverless in aws](https://www.serverless.com/plugins/serverless-rust)
[rust in cloudflare worker](https://developers.cloudflare.com/workers/)
[actix web framework](https://github.com/actix/actix-web)
[data class in rust](https://crates.io/crates/records)
[meilisearch engine](https://docs.meilisearch.com/)
[sonic search](https://github.com/valeriansaliou/sonic)
[simulation modelling](https://simlin.com/) 
[enso - low-code data science](https://enso.org/)
[weave - k8s & gitops, firecracker](https://github.com/weaveworks/ignite)
[linkerd: servicemesh](https://linkerd.io/)
[TiKV - tx KV database ](https://github.com/tikv/tikv)
[xsv - process cvs file](https://github.com/BurntSushi/xsv)
[arload - arweave uploader](https://crates.io/crates/arloader)
[CQRS-ES](https://doc.rust-cqrs.org/)
# beam and jvm
[Rustler - calling Rust from elixir](https://github.com/rusterlium/rustler)
[good article on Rust vs erlang](https://www.infoq.com/articles/rust-erlang-comparison/)
[Mnesia real time database](https://en.wikipedia.org/wiki/Mnesia)
[Rust and the JVM](https://blog.frankel.ch/start-rust/7/)

# Asynchronous programming
[Asychornous Runtime](https://github.com/tokio-rs)
[Rayon - parallel programming](https://github.com/rayon-rs/rayon)
[actors with tokio](https://ryhl.io/blog/actors-with-tokio/)
[eventador - lock free event bus inspired by LMAX Disruptor](https://docs.rs/eventador/latest/eventador/)
[LMAX disruptor pattern](https://github.com/polyfractal/Turbine)

Futures and async. This is: tokio, futures-rs and async-std.
Threadpools: Rayon and threadpool.
Thread-safe data structures: crossbeam.

The first category is about waiting for a whole bunch of things at once. For example if you have a web server, you spend most of the time waiting for I/O to send and receive a message. Futures allow you to compute other stuff while you wait for the response.

The second category is about doing a whole bunch of things at once. The rayon library is based on the principle of solving problems with divide and conquer. You have a problem. You split it up into smaller problems, which can be run on separate threads in a thread pool. Then you combine the results and you have your answer. As for the threadpool library, it also let's you spawn many tasks on a thread pool, but it's more primitive.

Crossbeam just gives you various data structures and algorithms that are useful when doing things on multiple threads. For example it provides various queues that allow pushing and popping items from several threads without a mutex.

[100 rust project](https://www.wezm.net/v2/posts/2020/100-rust-binaries/)


# Web development
[](https://thenewstack.io/the-case-for-rust-as-the-future-of-javascript-infrastructure/)
[wasm](https://yew.rs/?utm_source=thenewstack&utm_medium=website&utm_campaign=platform)
[](https://github.com/chinedufn/percy?utm_source=thenewstack&utm_medium=website&utm_campaign=platform)
[seed](https://github.com/chinedufn/percy?utm_source=thenewstack&utm_medium=website&utm_campaign=platform)
[wasm](https://github.com/sycamore-rs/sycamore?utm_source=thenewstack&utm_medium=website&utm_campaign=platform)

[standard library](https://doc.rust-lang.org/std/index.html)
[edition guide](https://doc.rust-lang.org/edition-guide/index.html)
[rustdoc book](https://doc.rust-lang.org/rustdoc/index.html)
[cargo book](https://doc.rust-lang.org/cargo/index.html)
[rustc book](https://doc.rust-lang.org/rustc/what-is-rustc.html)
[compiler error index](https://doc.rust-lang.org/error-index.html)
[CLI app in Rust](https://rust-cli.github.io/book/index.html)
[WASM book](https://rustwasm.github.io/docs/book/introduction.html)
[creative projects - 2D game](https://www.packtpub.com/product/creative-projects-for-rust-programmers/9781789346220)

# are we yet list
[are we yet list](https://github.com/UgurcanAkkok/AreWeRustYet)
[async](https://areweasyncyet.rs/)
[distributed](https://github.com/arewedistributedyet/arewedistributedyet)
[IPFS](https://areweipfsyet.rs/)
[machine learning](https://www.arewelearningyet.com/)

[The Difference between Functional Programming and Object-Oriented Programming](https://sdacademy.dev/difference-between-functional-programming-and-object-oriented-programming/)