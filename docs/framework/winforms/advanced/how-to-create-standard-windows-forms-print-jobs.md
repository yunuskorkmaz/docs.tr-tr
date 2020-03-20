---
title: Standart Yazdırma İşleri Oluşturma
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
ms.openlocfilehash: d9607de7c74132e0d7dce605b16d62c79b7dbccb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182575"
---
# <a name="how-to-create-standard-windows-forms-print-jobs"></a>Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma
Windows Formlarında yazdırmanın <xref:System.Drawing.Printing.PrintDocument> temeli, daha spesifik <xref:System.Drawing.Printing.PrintDocument.PrintPage> olarak olayın bileşenidir. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı işlemek için kod yazarak, neyi yazdırabileceğinizi ve nasıl yazdırılacağınızı belirtebilirsiniz.  
  
### <a name="to-create-a-print-job"></a>Yazdırma işi oluşturmak için  
  
1. Formunuza <xref:System.Drawing.Printing.PrintDocument> bir bileşen ekleyin.  
  
2. <xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı işlemek için kod yazın.  
  
     Kendi yazdırma mantığınızı kodlamanız gerekir. Ayrıca, yazdırılacak malzemeyi belirtmeniz gerekir.  
  
     Aşağıdaki kod örneğinde, yazdırılacak malzeme olarak hareket etmek üzere <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi kırmızı dikdörtgen şeklinde bir örnek grafik oluşturulur.  
  
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
  
     (Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
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
  
     Ayrıca, her sayfa yazdırıldıkça yazdırılacak toplam sayfa sayısını temsil eden bir tamsayı da dahil olmak üzere, olaylar <xref:System.Drawing.Printing.PrintDocument.BeginPrint> ve <xref:System.Drawing.Printing.PrintDocument.EndPrint> olaylar için kod yazmak da isteyebilirsiniz.  
  
    > [!NOTE]
    > Kullanıcılarınıza temiz <xref:System.Windows.Forms.PrintDialog> ve verimli bir kullanıcı arabirimi (UI) sağlamak için formunuza bir bileşen ekleyebilirsiniz. Bileşenin <xref:System.Windows.Forms.PrintDialog.Document%2A> özelliğini <xref:System.Windows.Forms.PrintDialog> ayarlamak, formunuzda birlikte çalıştığınız yazdırma belgesiyle ilgili özellikleri ayarlamanızı sağlar. Bileşen hakkında daha <xref:System.Windows.Forms.PrintDialog> fazla bilgi için [PrintDialog Bileşeni'ne](../controls/printdialog-component-windows-forms.md)bakın.  
  
     Windows Forms yazdırma işlerinin özellikleri hakkında daha fazla bilgi için, programlı bir <xref:System.Drawing.Printing.PrintPageEventArgs>yazdırma işi oluşturma da dahil olmak üzere bkz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)
