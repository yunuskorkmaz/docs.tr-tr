---
title: "Nasıl yapılır: bir kullanıcı &#39; bağlanan yazıcıları seçme bilgisayarındaki Windows Forms'ta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms], choosing printers
- printers [Windows Forms], choosing
ms.assetid: 63c1172b-2931-4ac0-953f-37f629494bbf
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec334ff65095e11855d706f445fda1d4b7ea1472
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-choose-the-printers-attached-to-a-user39s-computer-in-windows-forms"></a>Nasıl yapılır: bir kullanıcı &#39; bağlanan yazıcıları seçme bilgisayarındaki Windows Forms'ta
Genellikle, kullanıcıların yazdırma için varsayılan yazıcı dışında bir yazıcı seçin istersiniz. Bir yazıcı olanlar kullanarak yüklü kümelerini seçmelerini etkinleştirebilirsiniz <xref:System.Windows.Forms.PrintDialog> bileşeni. Aracılığıyla <xref:System.Windows.Forms.PrintDialog> bileşeni <xref:System.Windows.Forms.DialogResult> , <xref:System.Windows.Forms.PrintDialog> bileşeni yakalanan ve yazıcı seçmek için kullanılır.  
  
 Aşağıdaki yordamda, bir metin dosyası varsayılan yazıcıda yazdırılmak üzere seçilir. <xref:System.Windows.Forms.PrintDialog> Sınıfının örneği sonra.  
  
### <a name="to-choose-a-printer-and-then-print-a-file"></a>Bir yazıcı seçin ve ardından dosya yazdırmak için  
  
1.  Kullanarak kullanılacak yazıcı seçin <xref:System.Windows.Forms.PrintDialog> bileşeni.  
  
     Aşağıdaki kod örneğinde işlenen iki olay vardır. İlk bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olayı <xref:System.Windows.Forms.PrintDialog> sınıfı örneği ve kullanıcı tarafından seçilen yazıcı, yakalanan <xref:System.Windows.Forms.DialogResult> özelliği.  
  
     İkinci olay <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı <xref:System.Drawing.Printing.PrintDocument> bileşeni, örnek bir belge belirtilen yazıcı yazdırılmıştır.  
  
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
  
     ([!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms yazdırma desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
