unit Principal;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls;

type
  TfrmPrincipal = class(TForm)
    lblNormal: TLabel;
    lblCriptografado: TLabel;
    btnCriptografa: TButton;
    btnDescriptografa: TButton;
    edtNormal: TMemo;
    edtFinal: TMemo;
    edtChave: TEdit;
    lblChave: TLabel;
    edtTamanhoChave: TEdit;
    lblTamanhoChave: TLabel;
    procedure btnCriptografaClick(Sender: TObject);
    procedure FormActivate(Sender: TObject);
    Function Criptografa(Texto: string; chave : Integer) : string;
    Function Descriptografa(Texto: string; chave : Integer) : string;
    procedure btnDescriptografaClick(Sender: TObject);
    procedure edtTamanhoChaveExit(Sender: TObject);
  private
    tamanhoChave : Integer;
  public
    { Public declarations }
  end;

var
  frmPrincipal: TfrmPrincipal;

implementation

{$R *.dfm}

Function TfrmPrincipal.Criptografa(Texto: string; chave : integer): string;
var Tamanho,i : integer;
    PalavraHex : String;
begin
  Tamanho := Length(Texto);
  for i := 1 to Tamanho do
    PalavraHex := CHR(chave + Ord(Texto[i]));

  Result := PalavraHex;
end;


Function TfrmPrincipal.Descriptografa(Texto: string; chave : integer): string;
var Tamanho,i : integer;
    PalavraHex : String;
begin
  Tamanho := Length(Texto);
  for i := 1 to Tamanho do
    PalavraHex := CHR(Ord(Texto[i]) - chave);

  Result := PalavraHex;
end;

procedure TfrmPrincipal.btnCriptografaClick(Sender: TObject);
var ASCII, chave : TStringList;
    i, codChave : Integer;
    original : String;
begin
  ASCII := TStringList.Create;
  ASCII.Clear;
  chave := TStringList.Create;
  chave.Clear;

  original := StringReplace(edtNormal.Lines.Text ,CHR(13)+CHR(10),'',[rfReplaceAll]);

  for i := 0 to tamanhoChave-1 do
    Chave.Add(IntToStr(Random(9)));

  i := 0;
  codChave := 0;

  while i <= Length(original) do
  begin
    ASCII.Add(Criptografa(original[i], StrToInt(chave[codChave])));

    Inc(i);
    Inc(codChave);
    if codChave = tamanhoChave then
      codChave := 0;
  end;

  edtFinal.Lines.Text := '';
  for i := 0 to ASCII.Count -1 Do
    edtFinal.Lines.Text := edtFinal.Lines.Text + ASCII[i];

  edtChave.Text := '';
  for i := 0 to chave.Count -1 Do
    edtChave.Text := edtChave.Text + chave[i];
                      
  FreeAndNil(chave);
  FreeAndNil(ASCII);    
end;






procedure TfrmPrincipal.FormActivate(Sender: TObject);
begin
  tamanhoChave := 3;
end;

procedure TfrmPrincipal.btnDescriptografaClick(Sender: TObject);
var ASCII, chave : TStringList;
    i, codChave : Integer;
    original, aux : String;
begin
  ASCII := TStringList.Create;
  ASCII.Clear;
  chave := TStringList.Create;
  chave.Clear;

  original := StringReplace(edtNormal.Lines.Text ,CHR(13)+CHR(10),'',[rfReplaceAll]);

  aux := edtChave.Text;
  for i := 1 to tamanhoChave do
    Chave.Add(aux[i]);

  i := 0;
  codChave := 0;

  while i <= Length(original) do
  begin
    ASCII.Add(Descriptografa(original[i], StrToInt(chave[codChave])));

    Inc(i);
    Inc(codChave);
    if codChave = tamanhoChave then
      codChave := 0;
  end;

  edtFinal.Lines.Text := '';
  for i := 0 to ASCII.Count -1 Do
    edtFinal.Lines.Text := edtFinal.Lines.Text + ASCII[i];

  FreeAndNil(chave);
  FreeAndNil(ASCII);

end;

procedure TfrmPrincipal.edtTamanhoChaveExit(Sender: TObject);
begin
  tamanhoChave := StrToInt(edtTamanhoChave.Text);
end;

end.
