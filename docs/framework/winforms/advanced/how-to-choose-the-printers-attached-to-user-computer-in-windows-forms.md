---
title: 'Nasıl YapIlir: Kullanıcının Bilgisayarına Bağlı Yazıcıları Seçin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 2afbccd02ef42a78d5eac1a01841516fca27c92e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182606"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Bir Kullanıcının Bilgisayarına Bağlanan Yazıcıları Seçme
Genellikle, kullanıcılar yazdırılacak varsayılan yazıcı dışında bir yazıcı seçmek ister. Kullanıcıların bileşeni kullanarak şu anda yüklü olanlar arasından <xref:System.Windows.Forms.PrintDialog> bir yazıcı seçmelerini sağlayabilirsiniz. <xref:System.Windows.Forms.PrintDialog> Bileşen aracılığıyla, <xref:System.Windows.Forms.DialogResult> <xref:System.Windows.Forms.PrintDialog> bileşenin yakalanan ve yazıcı seçmek için kullanılır.  
  
 Aşağıdaki yordamda, varsayılan yazıcıya yazdırılmak üzere bir metin dosyası seçilir. Sınıf <xref:System.Windows.Forms.PrintDialog> daha sonra anında.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Yazıcı seçmek ve ardından dosya yazdırmak için  
  
1. Bileşeni kullanarak kullanılacak yazıcıyı <xref:System.Windows.Forms.PrintDialog> seçin.  
  
     Aşağıdaki kod örneğinde, ele alınmakta olan iki olay vardır. İlk olarak, <xref:System.Windows.Forms.Button> bir denetim <xref:System.Windows.Forms.Control.Click> olayı, <xref:System.Windows.Forms.PrintDialog> sınıf anında ve kullanıcı tarafından seçilen yazıcı <xref:System.Windows.Forms.DialogResult> özelliği yakalanır.  
  
     İkinci olayda, <xref:System.Drawing.Printing.PrintDocument.PrintPage> <xref:System.Drawing.Printing.PrintDocument> bileşenin durumunda, bir örnek belge belirtilen yazıcıya yazdırılır.  
  
    ```vb  
    Private Sub Button1_Click(ByVal sender As Object, ByVal e As System.EventArgs) Handles Button1.Click  
       Dim PrintDialog1 As New PrintDialog()  
       PrintDialog1.Document = PrintDocument1  
       Dim result As DialogResult = PrintDialog1.ShowDialog()  
  
       If (result = DialogResult.OK) Then  
         PrintDocument1.Print()  
       End If
  
    End Sub  
  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       PrintDialog printDialog1 = new PrintDialog();  
       printDialog1.Document = printDocument1;  
       DialogResult result = printDialog1.ShowDialog();  
       if (result == DialogResult.OK)  
       {  
          printDocument1.Print();  
       }  
    }  
  
    private void printDocument1_PrintPage(object sender,
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void button1_Click(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          PrintDialog ^ printDialog1 = gcnew PrintDialog();  
          printDialog1->Document = printDocument1;  
          System::Windows::Forms::DialogResult result =
             printDialog1->ShowDialog();  
          if (result == DialogResult::OK)  
          {  
             printDocument1->Print();  
          }  
       }  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     (Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    this->button1->Click += gcnew  
       System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)
