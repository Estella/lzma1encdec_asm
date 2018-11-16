# lzma1encdec_asm
LZMA1 decoder/encoder from my EXE packer.

Example (using lzma.cpp to pack and LzmaDecodeSize.c to depack):
```
DWORD compressed;
DWORD original_sz;
DWORD aplibbed;
BYTE *Original = Load_Input_File("unpacker.bin", &original_sz);
BYTE* compressed_data = compress_lzma(Original, original_sz, &compressed);
PVOID testmem = (unsigned char*)malloc(original_sz);
unsigned char* workmem = (unsigned char*)malloc(0xC4000);
int result;
LzmaDecode((UInt16*)workmem, compressed_data + LZMA_PROPS_SIZE, (SizeT)compressed - LZMA_PROPS_SIZE, (unsigned char*)testmem, (SizeT)original_sz);
free(Original);
free(compressed_data);
free(workmem);
```
