---
title: 'Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma'
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
ms.openlocfilehash: 7ccebf128d533a0e0cf0a17e5702807371e1bea7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59170982"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma
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
