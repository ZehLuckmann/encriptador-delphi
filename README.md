# CodificadorDelphi
##José Henrique Luckmann
Aplicativo para codificar e decodificar uma mensagem baseado em uma chave.

#Funções

```
Function Criptografa(Texto: string; chave : integer): string;
var Tamanho,i : integer;
    PalavraHex : String;
begin
  Tamanho := Length(Texto);
  for i := 1 to Tamanho do
    PalavraHex := CHR(chave + Ord(Texto[i]));

  Result := PalavraHex;
end;
```

```
Function Descriptografa(Texto: string; chave : integer): string;
var Tamanho,i : integer;
    PalavraHex : String;
begin
  Tamanho := Length(Texto);
  for i := 1 to Tamanho do
    PalavraHex := CHR(Ord(Texto[i]) - chave);

  Result := PalavraHex;
end;
```
