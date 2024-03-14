# How this works. (Instructions)

1. Open the DLL file. **(CreateFile)**

2. Read the DLL into memory. **(ReadFile)**

3. Validate the **DLL image**.

4. Open the target process. **(OpenProcess)**

5. Allocate memory for the DLL and loader code in the target process. **(VirtualAllocEx)**

6. Copy the DLL image into target process's address space. **(WriteProcessMemory)**

7. Copy the loader code into target process's address space. **(WriteProcessMemory)**

8. Create a remote thread to execute the loader code in target process's address space. **(CreateRemoteThread)**

9. Wait for the loader code to complete **(WaitForSingleObject)**. The loader code perform relocations and resolve DLL imports for the image, and then call the entry point if found.

10. Free the loader code. **(VirtualFreeEx)**
