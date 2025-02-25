## Virtualization

Virtualization is a process that allows a computer to **share** its **hardware resources** with **multiple** digitally separated **environments**. 

Each virtualized environment runs within its **allocated resources**, such as memory, processing power, and storage. 

With virtualization, organizations can switch between different operating systems on the same physical server without rebooting.

### **Virtual machine**

A _virtual machine_ is a software-defined computer that runs on a physical computer with a separate operating system and computing resources.

The physical computer is called the _host machine_ and virtual machines are _guest machines_. 
Multiple virtual machines can run on a single physical machine. 

Virtual machines are abstracted from the computer hardware by a **hypervisor**.

### **Hypervisor**

The _hypervisor_ is a software component that manages multiple virtual machines in a computer. It ensures that each virtual machine gets the allocated resources and does not interfere with the operation of other virtual machines. There are two types of hypervisors.

#### ****_Type 1 hypervisor_****

A type 1 hypervisor, or bare-metal hypervisor, is a hypervisor program installed directly on the computer’s hardware instead of the operating system. Therefore, type 1 hypervisors have better performance and are commonly used by enterprise applications. KVM uses the type 1 hypervisor to host multiple virtual machines on the Linux operating system.

#### ****_Type 2 hypervisor_****

Also known as a hosted hypervisor, the type 2 hypervisor is installed on an operating system. Type 2 hypervisors are suitable for end-user computing.

