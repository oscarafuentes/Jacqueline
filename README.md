# Jacqueline

## Table of Contents

* Getting Started
* Introduction
* Requirements
* Installation
* Usage
* Documentation
* Versioning
* Maintainers
* License

## Getting Started

### Introduction

A wrapper class which enables the observation of an object, including attachments, "will set" event types, and "did set" event types.

### Requirements

The minimum deployment targets are as follows:

1. iOS - 10.0
2. watchOS - 3.0
3. tvOS - 10.0
4. macOS - 10.11

### Installation

- **Integrate as a sub-project**

Drag the .xcodeproj file into your workspace.

### Usage

The follow scenario will log "1", followed by "2".

```swift
import Jacqueline

let observable = JObservable(1)
observable.observeDidSet { value in
    print(value)
}

observable.value = 2
```

## Documentation

### JObservable (Generic Type T)

#### Instance Variables

* `value: T`: The current value, an element of generic type T.

#### Initializers

* `init(_ value: T)`
    * Parameter `value`: An intial value which conforms to the designated generic type.

#### Instance Functions

* `observeDidSet(_ block: @escaping (T) -> Void)` - Property observer which is called immediately after the new value is stored.
    * Parameter `block`: The code block to run immediately after the new value is stored.

* `observeWillSet(_ block: @escaping (T) -> Void)` - Property observer which is called just before the new value is stored.
    * Parameter `block`: The code block to run just before the new value is stored.

* `attach(_ dependency: JObservable<T>)` - Create a unidirectional dependency on another observable object.
    * Parameter `dependency`: The obserable object to bind to.

## Versioning

This module uses [semantic versioning](http://semver.org/). For the versions available, see the [tags on this repository](https://github.com/oscarafuentes/Jacqueline/tags).

## Maintainers

* **Oscar Fuentes** - *Initial work* - [oscarafuentes](https://github.com/oscarafuentes)

## License

This project is licensed under the [MIT License](LICENSE.md)
