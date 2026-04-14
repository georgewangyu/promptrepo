# Examples

Real-world code examples demonstrating the four principles. Adapted from the upstream `EXAMPLES.md` in `forrestchang/andrej-karpathy-skills`.

## 1. Think Before Coding

### Example 1: Hidden Assumptions

**User Request:** "Add a feature to export user data"

**What often goes wrong**

- Assumes it should export all users
- Assumes file location without asking
- Assumes which fields to include
- Assumes output format details silently

**Better response**

Ask first:
- export all users or a filtered subset?
- browser download, API response, or background job?
- which fields are allowed?
- how large is the expected export?

### Example 2: Multiple Interpretations

**User Request:** "Make the search faster"

**What often goes wrong**

The agent silently chooses one meaning of "faster" and starts optimizing.

**Better response**

Surface the interpretations:
- lower latency
- higher throughput
- faster perceived UX

Then ask which one actually matters.

## 2. Simplicity First

### Example 1: Over-abstraction

**User Request:** "Add a function to calculate discount"

**What often goes wrong**

The agent builds a strategy hierarchy, config layer, and extensibility framework for a simple percentage calculation.

**Better response**

Start with a small function that calculates the discount directly. Add structure only when new requirements actually exist.

### Example 2: Speculative Features

**User Request:** "Save user preferences to database"

**What often goes wrong**

The agent adds validation hooks, caching, merge behavior, notification flows, and other unused features.

**Better response**

Write the simple save path first. Add caching, merging, or validation only when they become real requirements.

## 3. Surgical Changes

### Example 1: Drive-by Refactoring

**User Request:** "Fix the bug where empty emails crash the validator"

**What often goes wrong**

The fix turns into a broad validator rewrite with new username rules, formatting changes, or unrelated cleanup.

**Better response**

Fix the empty-email crash only. If other problems are visible, mention them separately.

### Example 2: Unrelated Cleanup

**User Request:** "Add logging to payment processing"

**What often goes wrong**

The agent also renames helpers, reorders imports, rewrites comments, and "modernizes" nearby code.

**Better response**

Add the requested logging with the smallest diff possible.

## 4. Goal-Driven Execution

### Example 1: Vague Bug Fixing

**User Request:** "Fix the login bug"

**What often goes wrong**

The agent changes code based on a guess, then says it should work.

**Better response**

- reproduce the bug
- define the expected outcome
- implement the fix
- verify the reproduction no longer fails

### Example 2: Feature Requests Without Verification

**User Request:** "Add validation"

**What often goes wrong**

Validation gets added without specifying invalid cases or expected failures.

**Better response**

Define the invalid inputs first, then verify the implementation rejects them correctly.

## Takeaway

The examples all point to the same discipline:
- make ambiguity explicit
- choose simplicity by default
- keep the diff narrow
- define success in a way that can actually be checked
