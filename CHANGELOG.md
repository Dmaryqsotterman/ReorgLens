# Changelog

All notable changes to this project are documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Documentation

- Note the JSON output format in the README.

## [0.7.0] - 2026-05-18

### Added

- `-format json` for machine-readable reports.

## [0.6.0] - 2024-11-02

### Added

- `-follow` to keep reading a file as it grows.
- Orphaned/adopted/common transaction sets in the report.

### Fixed

- A reorg deeper than the retained window is reported as `depth: unknown` instead
  of silently reporting the wrong height.

## [0.5.0] - 2023-02-14

### Added

- Line-level error reporting: the parser now names the line and the reason and
  continues instead of aborting the run.

## [0.4.0] - 2021-06-30

### Added

- Initial report format with height, depth and the two branch transaction sets.

## [0.1.0] - 2019-04-08

### Added

- First working chain follower over a JSONL capture.
