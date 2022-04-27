# bindtcp on macOS
https://packetstormsecurity.com/files/151731/macOS-TCP-4444-Bind-Shell-Null-Free-Shellcode.html
# asm compilation
nasm -f macho64 -o ipv4bind.o ipv4bind.s && ld -macosx_version_min 10.7.0 -o ipv4bind ipv4bind.o

# gcc compilation
gcc -o loader loader.c

# FIND OPEN PORTS
netstat -anvp tcp | awk 'NR<3 || /LISTEN/'

# CONNECTING TO BOUND TCP
nc -v 0.0.0.0 4444
