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
ms.openlocfilehash: 44673e6b26f088e71813aaac26c4b9a03429597a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938236"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma
Windows Forms ' de yazdırma temeli <xref:System.Drawing.Printing.PrintDocument> bileşeni, özellikle <xref:System.Drawing.Printing.PrintDocument.PrintPage> de olaydır. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı işlemek için kod yazarak neyin yazdırılacağını ve nasıl yazdırılacağını belirtebilirsiniz.  
  
### <a name="to-create-a-print-job"></a>Bir yazdırma işi oluşturmak için  
  
1. Formunuza bir <xref:System.Drawing.Printing.PrintDocument> bileşen ekleyin.  
  
2. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı işlemek için kod yazın.  
  
     Kendi yazdırma mantığınızı kodlarınızın olması gerekir. Ayrıca, yazdırılacak malzemeleri belirtmeniz gerekir.  
  
     Aşağıdaki kod örneğinde, yazdırılacak malzeme olarak davranacak şekilde <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde kırmızı dikdörtgen şeklindeki bir örnek grafik oluşturulur.  
  
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
  
     (Görsel C# ve görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
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
  
     Ayrıca, her sayfanın yazdırıldığı şekilde azallanan <xref:System.Drawing.Printing.PrintDocument.BeginPrint> toplam <xref:System.Drawing.Printing.PrintDocument.EndPrint> sayfa sayısını temsil eden bir tamsayı de dahil olmak üzere, ve olayları için kod yazmak isteyebilirsiniz.  
  
    > [!NOTE]
    > Kullanıcılarınıza temiz ve verimli <xref:System.Windows.Forms.PrintDialog> bir kullanıcı arabirimi (UI) sağlamak için formunuza bir bileşen ekleyebilirsiniz. <xref:System.Windows.Forms.PrintDialog> Bileşenin özelliğinin ayarlanması, formunuz üzerinde çalıştığınız yazdırma belgesiyle ilgili özellikleri ayarlamanıza olanak sağlar. <xref:System.Windows.Forms.PrintDialog.Document%2A> <xref:System.Windows.Forms.PrintDialog> Bileşen hakkında daha fazla bilgi için bkz. [PrintDialog bileşeni](../controls/printdialog-component-windows-forms.md).  
  
     Program aracılığıyla yazdırma işi oluşturma da dahil olmak üzere Windows Forms Yazdırma işlerinin özellikleri hakkında daha fazla bilgi için bkz <xref:System.Drawing.Printing.PrintPageEventArgs>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)
