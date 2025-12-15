# Basic Concepts
- ### Basic Zig Program Structure
  ```zig
  const std = @import("std");
  
  pub fn main() void {
      std.debug.print("Hello world!\n", .{});
  }
  ```
- ### Variables and Constants
- #### Mutable variable
  ```zig 
  var n: u8 = 50;
  n = n + 5;
  ```
- #### Constants
  ```zig 
  const negative_eleven: i8 = -11;
  ```
- #### Mutability Rules
- #### Valid
  ```zig
  var n: u8 = 5;
  n = 6; // valid
  ```
- #### Invalid
  ```zig
  const m: u8 = 5;
  m = 6; // compile-time error
  ```
- ### Integer Types
- #### Unsigned Integers (uN)
  ```zig 
  const a: u8  = 255;
  const b: u16 = 65535;
  const c: u32 = 4_294_967_295;
  ```
- #### Signed Integers (iN)
  ```zig 
  const x: i8  = -128;
  const y: i16 = -32_768;
  ```
- #### Overflow Safety
  ```zig 
  var n: u8 = 250;
  n = n + 10; // ❌ compile-time or runtime error (safe modes)
  ```
  Zig does not silently overflow in safe builds.
  ```zig
  zig run hello.zig
  condition is invalidthread 15835 panic: integer overflow
  /home/gh0s8/Documents/dev/ziging/part2/hello.zig:23:11: 0x113d2ed in main (hello.zig)
      n = n + 10;
            ^
  /usr/lib/zig/std/start.zig:627:37: 0x113da9d in posixCallMainAndExit (std.zig)
              const result = root.main() catch |err| {
                                      ^
  /usr/lib/zig/std/start.zig:232:5: 0x113d291 in _start (std.zig)
      asm volatile (switch (native_arch) {
      ^
  ???:?:?: 0x0 in ??? (???)
  fish: Job 1, 'zig run hello.zig' terminated by signal SIGABRT (Abort)
  ```