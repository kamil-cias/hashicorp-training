# How to connect with HashiCorp Vault API

> Aby uzyskać dostęp do danych przechowywanych w skarbcu należy posłużyć się tokenem - przekazując go w zapytaniu. Istotą tego rozwiązania jest poprawne stworzenie polityki.

Przykładem może być użycie tajemnicy w "cubbyhole". W tym przypadku tworzymy sobie nową ścieżkę np. "pin" i opisujemy wartości. Aby otrzymać wynik za pomocą API należy teraz wywołać np.

```shell
curl -s -k -X 'GET' \
'https://vault.go:8200/v1/cubbyhole/yoyo' \
-H 'accept: */*' \
-H 'X-Vault-Token: hvs.tnikQJX1uwujVB4xs8PGT3B4' | jq .data | tr -d '"'
```
aplikacja przyjmuje parametry "s - silent", "k lub insecure - powodujące ignorowanie błędów po stronie TLS/SSL". Podajemy następnie w metodzie "GET" adres naszego zasobu w HashiCorp Vault akceptując nagłówki. Wymogiem jest podanie tokena. Na koniec, dla lepszej czytelności kierujemy wynik do parsera "jq" wyodrębniając jedynie dane z ".data". Ostatnim wywołaniem jest wycięcie znaków "".
