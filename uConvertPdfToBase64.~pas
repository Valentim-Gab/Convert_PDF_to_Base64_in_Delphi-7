unit uConvertPdfToBase64;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, IdBaseComponent, IdCoder, IdCoder3to4, IdCoderMIME, EncdDecd;

type
  TForm1 = class(TForm)
    Edit1: TEdit;
    Button1: TButton;
    Button2: TButton;
    OpenDialog1: TOpenDialog;
    IdEncoderMIME1: TIdEncoderMIME;
    Memo1: TMemo;
    procedure Button1Click(Sender: TObject);
    procedure Button2Click(Sender: TObject);
  private
    { Private declarations }
    procedure Encode64;
    function buscaArquivo(mensagem: string): Boolean;
  public
    { Public declarations }
  end;

var
  Form1: TForm1;

implementation

{$R *.dfm}

procedure TForm1.Button1Click(Sender: TObject);
begin
  buscaArquivo('Carregado com sucesso!');
end;

procedure TForm1.Button2Click(Sender: TObject);
begin
  if Edit1.Text <> '' then
    Encode64
  else
    if MessageDlg('Localize um arquivo primeiro!' + #13#10 + 'Deseja localizar arquivo?', mtConfirmation, [mbNo,mbYes],0) = mrYes then
    begin
      if buscaArquivo('Carregado com sucesso e convertido para base64!') then
        Encode64;
    end;
end;

procedure TForm1.Encode64;
var
  LStream: TMemoryStream;
  Base64String: string;
begin
  LStream := TMemoryStream.Create;
  try
    LStream.LoadFromFile(OpenDialog1.FileName);
    Base64String := IdEncoderMIME1.Encode(LStream);
  finally
    Memo1.Lines.Text := Base64String;
    LStream.Free;
  end;
end;

function TForm1.buscaArquivo(mensagem: string): Boolean;
begin
  Result := False;
  if OpenDialog1.Execute then
   begin
     Edit1.Text := OpenDialog1.FileName;
     ShowMessage(mensagem);
     Memo1.Lines.Clear;
     Result := True;
   end;
end;

end.
