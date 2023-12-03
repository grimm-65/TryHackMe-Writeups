This challenge was about upload vulnerabilities
    You are to upload  a malicious file and get a reverse shell

    filters put in place only check for extension so to bypass
    
    upload a file with .png/.jpeg / .jpg

    intercept request using burp change to .jpeg.php 
    
    start a listener on machine eg nc -lnvp <port>
    
    visit where files are uploaded and youre done (in this case uploaded files are in <ip>/uploads/

    get a reverse shell 

    cat /var/www/flag.txt
