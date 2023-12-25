Para criptografar todos os arquivos em uma pasta usando Python, nos vamos usar a biblioteca cryptography.

import cryptography from cryptography.fernet import Fernet

Criar um objeto Fernet para criptografar os arquivos
fernet = Fernet()

Iterar sobre todos os arquivos na pasta
for file in os.listdir("."): # Ignorar arquivos ocultos e arquivos que não são arquivos regulares if file.startswith("."): continue file_path = os.path.join(".", file) if not os.path.isfile(file_path): continue

# Criptografar o arquivo
with open(file_path, "rb") as file_obj:
    file_data = file_obj.read()
    encrypted_data = fernet.encrypt(file_data)

# Salvar o arquivo criptografado na pasta original
with open(file_path, "wb") as file_obj:
    file_obj.write(encrypted_data)

print(f"Arquivo {file} criptografado com sucesso!")
Este código itera sobre todos os arquivos na pasta atual (.) e ignora arquivos ocultos (file.startswith(".")``) e arquivos que não são arquivos regulares (os.path.isfile(file_path)). Em seguida, ele abre cada arquivo, lê seu conteúdo, o criptografa usando a classe Fernet` e, em seguida, salva o arquivo criptografado na pasta original.

Para descriptografar os arquivos, você pode usar o mesmo código, mas com uma pequena modificação:

import cryptography from cryptography.fernet import Fernet

Criar um objeto Fernet para criptografar os arquivos
fernet = Fernet()

Iterar sobre todos os arquivos na pasta
for file in os.listdir("."): # Ignorar arquivos ocultos e arquivos que não são arquivos regulares if file.startswith("."): continue file_path = os.path.join(".", file) if not os.path.isfile(file_path): continue

# Descriptografar o arquivo
with open(file_path, "rb") as file_obj:
    encrypted_data = file_obj.read()
    decrypted_data = fernet.decrypt(encrypted_data)

# Salvar o arquivo descriptografado na pasta original
with open(file_path, "wb") as file_obj:
    file_obj.write(decrypted_data)

print(f"Arquivo {file} descriptografado com sucesso!")
