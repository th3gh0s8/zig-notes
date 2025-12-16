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
- ###  Zig has some fun array operators.
- We can use '++' to concatenate two arrays:
  ```zig
   const a = [_]u8{ 1,2 };
   const b = [_]u8{ 3,4 };
   const c = a ++ b ++ [_]u8{ 5 }; // equals 1 2 3 4 5
  ```
- We can use '**' to repeat an array:
  ```zig
  const d = [_]u8{ 1,2,3 } ** 2; // equals 1 2 3 1 2 3
  ```
- #### Note:
  both '++' and '**' only operate on arrays while your program is _being compiled_. This special time is known in Zig parlance as "comptime" and we'll learn plenty more about that later.
- example:
  ```zig
  const std = @import("std");
  
  pub fn main() void {
      const le = [_]u8{ 1, 3 };
      const et = [_]u8{ 3, 7 };
      
      const leet = le ++ et;
      
      const bit_pattern = [_]u8{ 1, 0, 0, 1 } ** 3;
      
      std.debug.print("LEET: ", .{});
  
      for (leet) |n| {
          std.debug.print("{}", .{n});
      }
  
      std.debug.print(", Bits: ", .{});
  
      for (bit_pattern) |n| {
          std.debug.print("{}", .{n});
      }
  
      std.debug.print("\n", .{});
  }
  ```