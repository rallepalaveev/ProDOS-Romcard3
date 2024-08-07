# ProDOS-Romcard3
ROMcard3 is a card for Apple II computers and is intended to work with a single EPROM 27C322 - the largest parallel UV EPROM ever produced.
The ROM is organized in 2048 banks of 2kB each, numbered #0000 to #07FF. Banks are selected by writing 2 bytes (#0000-#07FF) into $C0N0 and $C0N1, where N = 8 + [slot number], in the order LSB, then MSB.
Writing to $C0Nx at the same time activates the the ROM chip.
When a bank is selected, its content are seen in the address space $C800-$CFFF To de-enable the ROM chip a write must be performed to any address $C800-$CFFF or reset executed.
If a user program is accessing the card, it is important that at the end a write is performed to $C800-$CFFF so that the card is deactivated and does not conflict with other hardware, which is using the same address space.
The firmware is programmed in the first 128 16-bit words at address $100. It is always available at addresses $CM00-$CMFF, where M = [slot number]. It can also be seen at addresses $CA00-$CAFF of bank #0000.
The card is pre-loaded with ProDOS, programs and games. It is bootable and if it is the first boot device encountered, it will boot into ProDOS and a menu will appear of the programs pre-loaded. Tab can be pressed before cold-reset to omit the card from the boot sequence.

V2 removes the 74LS74. This functionality is performed by the PLD v2. The original version can be patched too by removing the 74LS74, shorting its pins 1 and 6 and using the v2 PLD.

Copyright (c) 2023 Ralle Palaveev All rights reserved.

Redistribution and use in source, binary, and manufactured forms, with or without modification, are permitted provided that the following conditions are met:

Redistributions of source code and design files must retain the above copyright notice, this list of conditions and the following disclaimer.
Redistributions in binary or manufactured form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
All advertising materials mentioning features or use of this software or hardware must display the following acknowledgement: This product includes software and hardware developed by Ralle Palaveev.
Neither the name of Ralle Palaveev nor the names of its contributors may be used to endorse or promote products derived from this software or hardware without specific prior written permission.

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

