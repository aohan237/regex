# regex

A Rust library for parsing, compiling, and executing regular expressions. Its
syntax is similar to Perl-style regular expressions, but lacks a few features
like look around and backreferences. In exchange, all searches execute in
linear time with respect to the size of the regular expression and search text.
Much of the syntax and implementation is inspired
by [RE2](https://github.com/google/re2).

[![Build status](https://github.com/rust-lang/regex/workflows/ci/badge.svg)](https://github.com/rust-lang/regex/actions)
[![Crates.io](https://img.shields.io/crates/v/regex.svg)](https://crates.io/crates/regex)
[![Rust](https://img.shields.io/badge/rust-1.41.1%2B-blue.svg?maxAge=3600)](https://github.com/rust-lang/regex)

## Feature Instructions

original regex does not support unicode characters in capture group names, maybe unicode is too much, then they can not decide which to use.

this repo adds support for this feature.

**this is not strictly tested, use with your own risk**

with this feature you can do:

```rust
let re = regex!(r"^(?P<名字>.+)$");
let cap = re.captures(t!("abc")).unwrap();
assert_eq!(&cap[0], t!("abc"));
assert_eq!(&cap[1], t!("abc"));
assert_eq!(&cap["名字"], t!("abc"));
```

but without it will show not support, originally it only supports characters in capture group names.
