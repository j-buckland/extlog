
This repository adds support for **external logs**, and for statistics tracking through those logs, to the [`slog`](https://github.com/slog-rs/slog/) ecosystem.

# Overview

**External logs** are logs that form an external API that end users can rely on, and that do not change without explicit agreement.

This repository provides the following.
 - An API for easily defining external logs.
 - An API for defining statistic values to track, and to modify them based on the external logs
 - A `StatisticsLogger` type that wraps an `slog::Logger`, which handles logging and updating tracked stats.
 - An `xlog!` macro for making the logs through the `StatisticsLogger`.

# Use of this crate

In theory, an external log can be defined simply by making any type implement `ExtLoggable`.  In practice, external logs will be generated by auto-deriving the `ExtLoggable` trait using the `slog-extlog-derive` crate from this repository.

Logs can then be generated by using the `xlog!` macro to make the logs using a `StatisticsLogger` - a wrapper around `slog::Logger` which can also track stats.

For more details, see:
 - the Rust documentation (TODO - add link once published)
 - the [basic tests](slog-extlog-derive/tests/loggable.rs) for logging examples
 - the [stats tests](slog-extlog-derive/tests/stats_extlog.rs) for examples with metrics and statistics tracking.