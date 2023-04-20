# How to install HashiCorp Vault on Debian/Ubuntu

### Aktualizacja i instalacja pakietu GPG
```shell
sudo apt update && sudo apt install gpg -y
```

### Dodanie klucza HashiCorp GPG do pęku kluczy serwera
```shell 
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
```

### Weryfikacja odcisku klucza
```shell 
gpg --no-default-keyring --keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg --fingerprint
```
* [Sprawdź odcisk palca klucza](https://www.hashicorp.com/official-packaging-guide)
* [Weryfikacja sumy kontrolnej pakietu Linux](https://www.hashicorp.com/security)


### Dodanie repozytorium HashiCorp do listy repozytorów systemu
```shell
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
```

### Ponowna aktualizacja pakietów oraz instalacja aplikacji Vault.
```shell
sudo apt update && sudo apt install vault -y
```

### Weryfikacja instalacji, sprawdzenie wersji oraz wywołanie menu
```shell
vault --version && vault
```
