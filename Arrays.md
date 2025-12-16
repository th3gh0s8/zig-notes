# Arrays in zig
- Arrays are declared with:
  ```zig
   var foo: [3]u32 = [3]u32{ 42, 108, 5423 };
  ```
  Zig can infer the size of the array, you can use '_' for the size. You can also let Zig infer the type of the value so the declaration is much less verbose.
  ```zig
  var foo = [_]u32{ 42, 108, 5423 };
  ```
- Getting values from an array using array[index] notation:
  ```zig
  const bar = foo[2]; // 5423
  ```
- Setting values to an array using array[index] notation:
  ```zig
  foo[2] = 16;
  ```
- We can get the length of an array using the len property:
  ```zig
  const length = foo.len;
  ```
- example:
  ```zig
  const std = @import("std");
  
  pub fn main() void {
  
      var some_primes = [_]u8{ 1, 3, 5, 7, 11, 13, 17, 19 };
    
      some_primes[0] = 2;
  
      const first = some_primes[0];
      
      const fourth = some_primes[3];
  
      const length = some_primes.len;
  
      std.debug.print("First: {}, Fourth: {}, Length: {}\n", .{
          first, fourth, length,
      });
  }
  ```