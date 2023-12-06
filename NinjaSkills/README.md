

(1)Which of the above files are owned by the best-group group(enter the answer separated by spaces in alphabetical order)

    find / -type f -group best-group 2>/dev/null

        -type f  specifies  to search for files
        -group  specifies group of user

        2/dev/null handles errors 
(2)Which of these files contain an IP address?




(3)Which file has the SHA1 hash of 9d54da7584015647ba052173b84d45e8007eba94

find / -type f \( -name 8V2L -o -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -name X1Uy \) -exec sha1sum {} \; 2>/dev/null

    Finds SHA1 value of files we are interested in only
    -exec sha1sum executes sha1sum on the files

    choose the one that matches 

(4)Which file contains 230 lines?

find / -type f \( -name 8V2L -o -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -name X1Uy \) -exec wc -l  {} \; 2>/dev/null


(5) Which file is executable by everyone?

find / -type f \( -name 8V2L -o -name bny0 -o -name c4ZX -o -name D8B3 -o -name FHl1 -o -name oiMO -o -name PFbD -o -name rmfX -o -name SRSq -o -name uqyw -o -name v2Vb -o -name X1Uy \) -exec ls ln {} \; 2>/dev/null


TODO:
    update for more explanation on commands 
