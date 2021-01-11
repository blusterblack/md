## Why use Rust?

- SAFE
- bunch of compiler error to prevent bunch of bugs
- static type
- compile
- build CLI, system programming, server
- new C++  
- most loved in stack overflow survey
- trend surfing
  
  ## Ownership
  
  ### Ownership
  
  rules:
- each value have an owner
- only one owner at a time
- drop value when owner goes out of scope
  ways to return memory:
- garbage collector: gc do all
- no gc: manual , hard and buggy
- rust: auto return when out of scope, like RAII in C++
  move operation: s1=String.from("abc");s2=s1
  s1 will be invalid to avoid double free instead of copy stack data
  clone operation: deep copy, copy both stack and heap
  copy operation: copy normally for stack-only data
  pass variable to function will move or copy: heap variable will not be usable when pass to function
  
  ### Reference
  
  use reference (&String) to borrow ownership
  reference is immutable by default
  only one mutable ref in a scope to prevent data race at **compile time**
  date race:>2 pointer same data,>1 write, no synchronize
  reference scope start when introduce, end when last time used
  auto prevent dangling pointer
  reference rules:
- either 1 mut ref or many refs
- always valid( no dangling)
  
  ### Slice
  
  kinda like a start-end pointer, point to a continuous block of data in heap
  
  ## Struct
  
  literally object with type, only mutable as whole
  can have only type struct without names
  method : define in impl *yourClass* { fn *your method*(&self)}
  automatic reference: auto add &,&mut, * to match method signature
  associated function: define in impl without self, call with struct::aFunc()
  can have multiple impl
  
  ## Enum
  
  A type only have 1 value among possible finite variants
  can have data in variant with different type
  
  ### Option enum
  
  Rust doesn't have null
  Option<T> cause mismatch type with T at compile time, force us to convert to T aka handle the null case.
  
  ### match operator
  
  kinda like a switch case
  can bind data in "arms"
  must cover all enum case
  _ is default
  
  ### if let
  
  match with only one case
  can else for _
  
  ## Module
  
  ### Package and crate
  
  Crate is binary or library
  Crate root is source file where rustc start
  Package is one or more crate with a Cargo.toml file
  
  ### module
  
  interface without type?
  define access modifiers here
  
  ### path
  
  same as file path
  absolute start with crate
  relative start with current module, use super, self
  all are private by default
  can mix pub and private in struct
  must have public constructor for private field struct
  pub enum default all variant pub
  
  ### use
  
  bring module to scope
  **Idiom** Only bring the parent module to avoid confused local function, bring full with enum, struct
  use **as** to create alias
  can group multiple use
  **glob operator (*)** for importing all public
  split package into crates, crate into module
  
  ## Collections
  
  stored on heap
  
  ### Vector
  
  Vec<T>
  Same type, can use vec![1,2,3
  drop vector also drop all element
  access with [] (panic when access invalid index) and get (return None). 
  ONLY 1 MUTABLE REF (No hold mut ref then push)
  iterating: for in
  use enum for multi type vector
  
  ### String
  
  Create with ::new, ::from and .to_string
  append with push and push_str
  use format! for easier life
  No string indexing
  Careful when slice String( char boundary)
  can iterate over byte and char, grapheme cluster require additional help
  
  ### Hash map
  
  use insert and get
  owned value get moved
  iterate with for in
  use entry or insert for check if not exist then insert
  
  ## Error handling
  
  ### Unrecoverable error
  
  panic!
  
  ### Recoverable error
  
  
  
  
  
  ## 
  
  