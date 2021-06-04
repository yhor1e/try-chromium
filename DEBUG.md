- launch Chromium `$ out/Default/Chromium.app/Contents/MacOS/Chromium`
- run lldb `$ lldb`
- Check the process id of tab in chromium
- Attach `(lldb) attach 4610`
- like below
```bash
(lldb) attach 4610
Process 4610 stopped
* thread #1, name = 'CrRendererMain', queue = 'com.apple.main-thread', stop reason = signal SIGSTOP
    frame #0: 0x00007fff7062bdfa libsystem_kernel.dylib`mach_msg_trap + 10
libsystem_kernel.dylib`mach_msg_trap:
->  0x7fff7062bdfa <+10>: retq   
    0x7fff7062bdfb <+11>: nop    

libsystem_kernel.dylib`mach_msg_overwrite_trap:
    0x7fff7062bdfc <+0>:  movq   %rcx, %r10
    0x7fff7062bdff <+3>:  movl   $0x1000020, %eax          ; imm = 0x1000020 
Target 0: (Chromium Helper (Renderer)) stopped.

:
:
```
- set breakpoint `(lldb) b Element::Element
```bash
(lldb) b Element::Element
Breakpoint 1: 41 locations.
```
- reload tab
```bash
(lldb) continue 
Process 4610 resuming
Process 4610 stopped
* thread #1, name = 'CrRendererMain', queue = 'com.apple.main-thread', stop reason = breakpoint 1.33
    frame #0: 0x00000001b68954a3 libblink_core.dylib`blink::Element::Element(this=0x00000018aaaa5768, tag_name=0x00000001ba6db860, document=0x00000018aaaa48f8, type=kCreateHTMLElement) at element.cc:572:21
   569 	Element::Element(const QualifiedName& tag_name,
   570 	                 Document* document,
   571 	                 ConstructionType type)
-> 572 	    : ContainerNode(document, type), tag_name_(tag_name) {}
   573 	
   574 	Element* Element::GetAnimationTarget() {
   575 	  return this;
```   


refs: 
- https://brookhong.github.io/2016/11/09/debug-chromium-with-lldb-under-mac-osx.html
- https://chromium.googlesource.com/chromium/src/+/refs/heads/main/docs/mac/debugging.md#The-Debugger

