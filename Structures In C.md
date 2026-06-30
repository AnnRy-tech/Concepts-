Typical use cases:

hardware registers, communication packets, configuration data, and memory optimization
Communication Packet
struct Packet
{
    uint8_t start;
    uint16_t id;
    uint8_t length;
    uint8_t data[10];
    uint8_t checksum;
};

EEPROM configuration 
typedef struct
{
    uint16_t deviceID;
    uint8_t mode;
    uint32_t baudRate;
    uint8_t checksum;
} Config;

Padding

Structure padding is the extra unused bytes that the compiler inserts between structure members 
(and sometimes at the end of a structure) to satisfy the CPU's memory alignment requirements. 
Proper alignment allows the processor to access data more efficiently.
Many processors access aligned data more efficiently.

For example:

A 4-byte int is most efficiently accessed when its address is divisible by 4.
An 8-byte double is often aligned to an 8-byte boundary.

If data is misaligned:

The CPU may require multiple memory accesses.
Some processors generate a hardware exception for unaligned access.
Performance may decrease.







