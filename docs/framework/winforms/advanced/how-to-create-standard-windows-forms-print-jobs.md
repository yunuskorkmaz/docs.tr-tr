---
title: 'Nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- printing [Windows Forms]
- printing [Windows Forms], creating print jobs
- printing [Visual Basic], in Windows applications
ms.assetid: 03342b90-9cfe-40b2-838b-b479a13c5dea
ms.openlocfilehash: b0568472dadceb46257a8d35211034a718aef74c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705235"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma
Windows Forms'ta baskı temelidir <xref:System.Drawing.Printing.PrintDocument> bileşeni — daha açık belirtmek gerekirse <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay. İşlemek için kod yazarak <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay ne yazdırma ve yazdırma nasıl belirtebilirsiniz.  
  
### <a name="to-create-a-print-job"></a>Bir yazdırma işi oluşturmak için  
  
1.  Ekleme bir <xref:System.Drawing.Printing.PrintDocument> formunuza bileşen.  
  
2.  İşlemek için kod yazma <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.  
  
     Yazdırma mantığınızı kod gerekecektir. Ayrıca, yazdırılması malzeme belirtin gerekecektir.  
  
     Aşağıdaki kod örneği, örnek grafik kırmızı bir dikdörtgen şeklinde oluşturulan <xref:System.Drawing.Printing.PrintDocument.PrintPage> yazdırılması malzeme olarak görev yapacak bir olay işleyicisi.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillRectangle(Brushes.Red, New Rectangle(500, 500, 500, 500))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Red,   
         new Rectangle(500, 500, 500, 500));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Red,  
             Rectangle(500, 500, 500, 500));  
       }  
    ```  
  
     (Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
     İçin kod yazma isteyebilirsiniz <xref:System.Drawing.Printing.PrintDocument.BeginPrint> ve <xref:System.Drawing.Printing.PrintDocument.EndPrint> belki de her bir sayfa olarak azaltılır yazdırmak için sayfaların toplam sayısını temsil eden bir tamsayı gibi etkinlikler.  
  
    > [!NOTE]
    >  Ekleyebileceğiniz bir <xref:System.Windows.Forms.PrintDialog> kullanıcılarınız için bir temiz ve verimli bir kullanıcı arabirimi (UI) sağlamak için formunuza bileşen. Ayarı <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliği <xref:System.Windows.Forms.PrintDialog> yazdırmak için ilgili özellikleri ayarlamak için belge bileşen etkinleştirir, form üzerinde çalıştığınız. Hakkında daha fazla bilgi için <xref:System.Windows.Forms.PrintDialog> bileşeni Bkz [PrintDialog bileşeni](../controls/printdialog-component-windows-forms.md).  
  
     Daha fazla Windows Forms hakkında bilgi için ayrıntıları yazdırma işlerini yazdırma işi programlama yoluyla oluşturma da dahil olmak üzere, bkz. <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)
