---
title: 'Nasıl yapılır: bir kullanıcının bilgisayarına bağlı yazıcıları seçme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
ms.openlocfilehash: 7fc2427468540ac0a1480f6140cbb34c3a0f1ab3
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746503"
---
# <a name="how-to-choose-the-printers-attached-to-a-users-computer-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Bir Kullanıcının Bilgisayarına Bağlanan Yazıcıları Seçme
Genellikle, kullanıcılar, yazdırma için varsayılan yazıcıdan farklı bir yazıcı seçmek ister. Kullanıcıların, <xref:System.Windows.Forms.PrintDialog> bileşenini kullanarak şu anda yüklü olanlardan bir yazıcı seçmesini sağlayabilirsiniz. <xref:System.Windows.Forms.PrintDialog> bileşeni aracılığıyla <xref:System.Windows.Forms.PrintDialog> bileşenin <xref:System.Windows.Forms.DialogResult> yakalanır ve yazıcıyı seçmek için kullanılır.  
  
 Aşağıdaki yordamda, varsayılan yazıcıda yazdırılmak üzere bir metin dosyası seçilidir. <xref:System.Windows.Forms.PrintDialog> sınıfı daha sonra oluşturulur.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Bir yazıcı seçmek ve sonra bir dosyayı yazdırmak için  
  
1. <xref:System.Windows.Forms.PrintDialog> bileşeni kullanılarak kullanılacak yazıcıyı seçin.  
  
     Aşağıdaki kod örneğinde, işlenen iki olay vardır. İlk olarak, bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olayında <xref:System.Windows.Forms.PrintDialog> sınıfı örneklenmiştir ve Kullanıcı tarafından seçilen yazıcı <xref:System.Windows.Forms.DialogResult> özelliğinde yakalanır.  
  
     İkinci olayda, <xref:System.Drawing.Printing.PrintDocument> bileşenin <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı, belirtilen yazıcıda bir örnek belge yazdırılır.  
  
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
  
     (Görsel C# ve görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
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
