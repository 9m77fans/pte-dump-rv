# pte-dump-rv
This is gdb script help us dump PTE for riscv64.
This project only support riscv64(sv57) and test on QEMU.

# show 
    (gdb) lxtask 116 0x10000
          TASK          PID    COMM

    0xff600000851eb200  116  at1

    satp = 0xa00000000010532a << using this

    => target virtual address = 0x10000

    PGD virtual address = 0xff6000008532a000
    PGD offset = 0x0
    flag = 0b1 ['V']
    P4D physical address = 0x1052ec000
    P4D offset = 0x0
    P4D virtual address = 0xff600000852ec000
    flag = 0b1 ['V']
    PUD physical address = 0x105289000
    PUD offset = 0x0
    PUD virtual address = 0xff60000085289000
    flag = 0b1 ['V']
    PMD physical address = 0x1048a4000
    PMD offset = 0x0
    PMD virtual address = 0xff600000848a4000
    flag = 0b1 ['V']
    PTE physical address = 0x105333000
    PTE offset = 0x80
    PTE virtual address = 0xff60000085333080
    flag = 0b1011011 ['A', 'U', 'X', 'R', 'V']
    page physical address = 0x10542b000
    page virtual address = 0xff6000008542b000
    page * address 0xff1c000004150ac0
    page flag = 0xff1c000004150ac0 ['PG_mappedtodisk', 'PG_arch_1', 'PG_lru', 'PG_uptodate', 'PG_referenced']

    => target physical address = 0x10542b000

(gdb) source gdb-pt-dump/pt.py
(gdb) pt -satp 0xa00000000010532a -filter u
         Address :  Length   Permissions
         0x10000 :  0x1000 | W:0 X:1 R:1 S:0
         0x11000 :  0x1000 | W:0 X:0 R:1 S:0
         0x12000 :  0x2000 | W:1 X:0 R:1 S:0
  0x7fffaaffa000 :  0x2000 | W:1 X:0 R:1 S:0
  0x7fffaaffc000 :  0x1000 | W:0 X:1 R:1 S:0
  0x7fffaaffe000 : 0x2f000 | W:0 X:1 R:1 S:0
  0x7fffab02e000 : 0x12000 | W:0 X:1 R:1 S:0
  0x7fffab060000 : 0x1a000 | W:0 X:1 R:1 S:0
  0x7fffab07b000 : 0x12000 | W:0 X:1 R:1 S:0
  0x7fffab08e000 : 0x42000 | W:0 X:1 R:1 S:0
  0x7fffab100000 : 0x10000 | W:0 X:1 R:1 S:0
  0x7fffab120000 :  0xc000 | W:0 X:1 R:1 S:0
  0x7fffab12d000 :  0x7000 | W:0 X:1 R:1 S:0
  0x7fffab15c000 :  0x3000 | W:0 X:0 R:1 S:0
  0x7fffab15f000 :  0x3000 | W:1 X:0 R:1 S:0
  0x7fffab165000 :  0x2000 | W:1 X:0 R:1 S:0
  0x7fffab16d000 :  0x3000 | W:1 X:0 R:1 S:0
  0x7fffab172000 :  0x1000 | W:0 X:1 R:1 S:0
  0x7fffab174000 : 0x22000 | W:0 X:1 R:1 S:0
  0x7fffab196000 :  0x2000 | W:0 X:0 R:1 S:0
  0x7fffab198000 :  0x2000 | W:1 X:0 R:1 S:0
  0x7fffeaaae000 :  0x2000 | W:1 X:0 R:1 S:0
