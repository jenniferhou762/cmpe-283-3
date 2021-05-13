# This home work is finished by my own.

# Steps in detail:
1. Checkout linx kernel machine.
2. Apply the diff.
3. Run build make -j 8 modules && make -j 8 && sudo make modules_install && sudo make install
4. Reboot system.

# Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail?
Yes it is in a stable rate.
In my machine, there was 192400 exits.

# Of the exit types defined in the SDM, which are the most frequent? Least?
Most - External interrupt, WRMSR, EPT violation etc.
Least - MOV DR and WINVD.

# assignment 4
## Include a sample of your print of exit count output from dmesg from “with ept” and “without ept”.
Before: 
number of exits = 192400
After: 
number of exits = 192487

## What did you learn from the count of exits? Was the count what you expected? If not, why not?
Yes the count is expected.
nested paging will have fewer exits than the shadow paging.

## What changed between the two runs (ept vs no-ept)?
The exit number of shadow paging with ept=0 is higher than nexted paging.
After a vm shift from nested paging to shadow paging, the shadow page table will be managed by the VMM. In the shadow paging, CR3 points to the hypervisor shadow page table and it requires PF page fault exiting to be enabled. So when the vm check for a specific page, it can't be found in the guest page table. The hypervisor has to copy the whole shadow page table and also needs to populate TLB. Because of that, TLB flush exiting also needs to be enabled so that the shadow table can be always up to date.
