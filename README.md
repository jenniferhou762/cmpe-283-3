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