# VHDL Style Guidelines
## File rules
1. the filename shall match the entity name
2. each file contains one entity and one architecture
3. every file contains the standard header
4. prefer the architecture to be `entityname_arch`
5. MIT license
6. copyright: Flat Earth Inc, Bozeman MT

## General style
1. NO TABS, use TWO spaces instead
2. for entity ports, prefer modes "in" and "out" instead of "inout" when possible
3. limit line lengths to 120 characters
    1. this is a soft limit
4. keywords are *lowercase*
5. align colons, port directions, and signal types in port map declarations
6. align assignment operators
7. group related signals together
8. vector indexes are defined as downto
9. least significant bit is always 0

## Naming conventions
1. signal names are snake_case
2. constants are ALL_CAPS

## Processes
1. synchronous processes
    1. only sensitive to clock and reset
    2. always use rising_edge(clk)
    3. initialize registers on reset
    ```vhdl
    process(clk, reset):
      if reset = '1' then
        ...
      elsif rising_edge(clk) then
        ...
      end if;
    end process;
    ```
2. in a combinatorial process sensitivty list, include all signals that are read inside the process

## Instantiation
1. always use named signal mapping in component instantiation
2. prefer `for generate` for reptitive instantiation

## Generics and constants
1. prefer generics to constants
2. put shared constants and types in a package
3. use constants instead of magic numbers
    1. define data widths with constants

## Assignments and Initialization
1. explicitly initialize register values
2. prefer using conversion functions instead of bit literals
    ```vhdl
    a <= std_logic_vector(to_unsigned(512, data_width));
    ```
    instead of 
    ```vhdl
    a <= "00000000000000000000001000000000";
    ```

## Data types
1. only use std_logic and std_logic_vector at the top level
2. use the most abstract data type that fits your purpose
    1. for a counter, use an integer rather than std_logic_vector
    2. for conditional flags, prefer booleans over std_logic
    3. for arithmetic, use signed and unsigned over std_logic_vector


# References
[Tampere Style Guide](http://www.tkt.cs.tut.fi/kurssit/50200/S17/Harjoitukset/dcs_vhdl_coding_rules_es_v4_4.pdf)

[Effective Coding with VHDL](https://mitpress.mit.edu/books/effective-coding-vhdl)

[VHDL Reference Guide](https://www.ics.uci.edu/~jmoorkan/vhdlref/)

