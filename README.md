# swift_sequence_of_operations_chained_with_a_single_closure

Here's how a sequence of operations can be chained together, by combining their functions into a single closure:

```swift
internal func +<A, B, C>(lhs: @escaping (A) throws -> B,
                         rhs: @escaping (B) throws -> C) -> (A) throws -> C {
    return { try rhs(lhs($0)) }
}

public func run() throws {
    try (determineTarget + build + analyze + output)()
}
```
