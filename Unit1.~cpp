//---------------------------------------------------------------------------

#include <vcl.h>
#pragma hdrstop

#include "Unit1.h"
//---------------------------------------------------------------------------
#pragma package(smart_init)
#pragma resource "*.dfm"
TForm1 *Form1;

        int x= 0;
        int y = 0;
        int punkt_gracz_prawy = 0;
        int punkt_gracz_lewy = 0;
        int ilosc_odbic = 0;
//---------------------------------------------------------------------------
__fastcall TForm1::TForm1(TComponent* Owner)
        : TForm(Owner)
{
}
//---------------------------------------------------------------------------

void __fastcall TForm1::Timer_pilkaTimer(TObject *Sender)
{
       b->Left+=x;
       b->Top +=y;

       //odbij od górnej sciany
       if(b->Top-5 <= tlo->Top)
                y=-y;

       //odbij od dolnej sciany
       if(b->Top+b->Height+5 >= tlo->Height)
                y=-y;

       //nieodbicie pi³ki z lewej strony
       if(b->Left <= p1->Left-p1->Width-15)
       {
                Timer_pilka->Enabled = false;
                b->Visible = false;
                Label3->Visible = true;
                Label2->Visible = true;
                Label3->Caption = ilosc_odbic;
                punkt_gracz_prawy++;
                Label4->Caption = punkt_gracz_lewy;
                Label6->Caption = punkt_gracz_prawy;
                Label4->Visible = true;
                Label5->Visible = true;
                Label6->Visible = true;
                Label8->Visible = true;
                Button2->Visible = true;
                Button3->Visible = true;
       }
       else if(b->Top < p1->Top+p1->Height && b->Top+b->Height > p1->Top && b->Left < p1->Left+p1->Width)
       {
                if(b->Top < p1->Top+(p1->Height/2)+25 && b->Top > p1->Top+(p1->Height/2)-25)
                {
                        x*=1.5;
                        y*=1.5;
                }
                if(x<0) x=-x;
                ilosc_odbic++;

                
       }

       //nieodbicie pi³ki z prawej strony
       if(b->Left-b->Width-5 >= p2->Left)
       {
                Timer_pilka->Enabled = false;
                b->Visible = false;
                Label3->Visible = true;
                Label2->Visible = true;
                Label3->Caption = ilosc_odbic;
                punkt_gracz_lewy++;
                Label4->Caption = punkt_gracz_lewy;
                Label6->Caption = punkt_gracz_prawy;
                Label4->Visible = true;
                Label5->Visible = true;
                Label6->Visible = true;
                Label7->Visible = true;
                Button2->Visible = true;
                Button3->Visible = true;
       }
       else if(b->Top < p2->Top+p2->Height && b->Top+b->Height > p2->Top && b->Left+b->Width > p2->Left)
       {

                if(b->Top < p2->Top+(p2->Height/2)+25 && b->Top > p2->Top+(p2->Height/2)-25)
                {
                        x*=1.5;
                        y*=1.5;
                }
                if(x>0) x=-x;
                ilosc_odbic++;
       }

}
//---------------------------------------------------------------------------
void __fastcall TForm1::gora1Timer(TObject *Sender)
{
        if(p1->Top > 10) p1->Top -= 10;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::dol1Timer(TObject *Sender)
{
        if(p1->Top + p1->Height < tlo->Height - 10) p1->Top += 10;
}
//---------------------------------------------------------------------------


void __fastcall TForm1::FormKeyDown(TObject *Sender, WORD &Key,
      TShiftState Shift)
{
        if(Key == 'A') gora1->Enabled = true;
        if(Key == 'Z') dol1->Enabled = true;
        if(Key == VK_UP) gora2->Enabled = true;
        if(Key == VK_DOWN) dol2->Enabled = true;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::FormKeyUp(TObject *Sender, WORD &Key,
      TShiftState Shift)
{
        if(Key == 'A') gora1->Enabled = false;
        if(Key == 'Z') dol1->Enabled = false;
        if(Key == VK_UP) gora2->Enabled = false;
        if(Key == VK_DOWN) dol2->Enabled = false;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::gora2Timer(TObject *Sender)
{
        if(p2->Top > 10) p2->Top -= 10;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::dol2Timer(TObject *Sender)
{
        if(p2->Top + p2->Height < tlo->Height - 10) p2->Top += 10;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::FormCreate(TObject *Sender)
{
        Application->MessageBox(
                        "Witaj w grze Ping Pong.\n"
                        "\n"
                        "Lewy gracz steruje wciskaj¹c klawisze A oraz Z.\n"
                        "Prawy gracz steruje wciskaj¹c strza³ki do góry i w dó³.\n"
                        "\n"
                        "Dla urozmaicenia zabawy:\n"
                        "Kiedy odbijesz pi³kê na œrodku paletki, wówczas zmienisz jej k¹t odbicia i pi³ka przyœpieszy.\n"
                        "Im d³u¿ej odbijasz, tym pi³ka szybciej przemieszcza siê.\n"
                        "Mo¿esz dowolnie zmieniaæ pole gry.\n"
                        "\n"
                        "Mi³ej zabawy!", "Ping Pong",
                        MB_OK);
}
//---------------------------------------------------------------------------

void __fastcall TForm1::Button1Click(TObject *Sender)
{
        Label1->Visible = false;
        Button1->Visible = false;
        Timer_pilka->Enabled = true;
        x = -6;
        y = -6;
}
//---------------------------------------------------------------------------

void __fastcall TForm1::Button2Click(TObject *Sender)
{

        if(Application->MessageBox("Czy na pewno chcesz zacz¹æ od nowa?", "PotwierdŸ",
                MB_YESNO | MB_ICONQUESTION | MB_DEFBUTTON2) == IDNO)
        {
                Action=caNone;
        }
        else
        {

                ilosc_odbic = 0;
                punkt_gracz_prawy = 0;
                punkt_gracz_lewy = 0;
                Label8->Visible = false;
                Label7->Visible = false;
                Label6->Visible = false;
                Label5->Visible = false;
                Label4->Visible = false;
                Label3->Visible = false;
                Label2->Visible = false;
                Button2->Visible = false;
                Button3->Visible = false;
                b->Visible = true;
                b->Left = 460;
                b->Top = 210;
                Timer_pilka->Enabled = true;
                x = -6;
                y = -6;
        }
        
}
//---------------------------------------------------------------------------

void __fastcall TForm1::Button3Click(TObject *Sender)
{
        ilosc_odbic = 0;
        Label8->Visible = false;
        Label7->Visible = false;
        Label6->Visible = false;
        Label5->Visible = false;
        Label4->Visible = false;
        Label3->Visible = false;
        Label2->Visible = false;
        Button2->Visible = false;
        b->Visible = true;
        b->Left = 460;
        b->Top = 210;
        Timer_pilka->Enabled = true;
        Button3->Visible = false;
        x = -6;
        y = -6;
}
//---------------------------------------------------------------------------


