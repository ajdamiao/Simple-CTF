# Simple-CTF
Passos de como resolvi o Simple CTF no TryHackMe
Dificuldado: Fácil

1- Primeiramente comecei usando o NMAP para scanear portas abertas e os servicos rodando nas portas.
nmap: ![nmap scan](https://user-images.githubusercontent.com/52061729/97948201-9fd3d480-1d6e-11eb-9380-78987655df0f.png)
Encontrei as portas:
21 - FTP
80 - apache
2222 - SSH

2- Como tem um servico apache rodando usei o gobuster para achar diretorios do site, mas acabou que nem precisei do resultado e também não me levou a nada.
3- Enquanto o GoBuster rodava eu tentei entrar no FTP como anonymous e funcionou logo consegui localizar um arquivo chamado ForMitch.txt onde tinha a seguinte mensagem:
![ftp](https://user-images.githubusercontent.com/52061729/97948256-ca259200-1d6e-11eb-8d41-46624404d0ab.png)

4- Entao pensei em fazer um bruteforce no SSH com o usuario mitch e consegui a senha
![hydra](https://user-images.githubusercontent.com/52061729/97948303-e88b8d80-1d6e-11eb-9138-efbd69658f5c.png)

5- Logando no SSH com o usuario mitch consegui a primeira flag.
![primeira flag](https://user-images.githubusercontent.com/52061729/97948322-f3deb900-1d6e-11eb-9f74-a64c385bd71e.png)

5- Apos pegar a primeira flag usei o comando sudo -l para saber onde o usuario mitch poderia usar o comando sudo entao encontrei q ele poderia usar o /usr/bin/vim, posso fazer um privilege escalation com o seguinte comando: sudo vim -c '!sh'
![sudo -l](https://user-images.githubusercontent.com/52061729/97948337-fd682100-1d6e-11eb-8eb1-2463146f4ebc.png)
6- Após fazer o privilege escalation ja tive acesso ao usuario root, então fui na pasta /root e encontrei a segunda flag.
![flag root](https://user-images.githubusercontent.com/52061729/97948353-0a851000-1d6f-11eb-8444-938cd788d199.png)
