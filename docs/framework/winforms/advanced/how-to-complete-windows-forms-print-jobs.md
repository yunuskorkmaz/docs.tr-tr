---
title: Yazdırma işlerini Tamam
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: b8ef4fa05b2107247181e82b72389f9503507135
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746495"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Nasıl yapılır: Windows Forms Yazdırma İşlerini Tamamlama
Genellikle, Word işlemcileri ve yazdırmayı içeren diğer uygulamalar, bir yazdırma işinin tamamlandığını kullanıcılara bir ileti görüntüleme seçeneği sağlar. <xref:System.Drawing.Printing.PrintDocument> bileşeninin <xref:System.Drawing.Printing.PrintDocument.EndPrint> olayını işleyerek bu işlevselliği Windows Forms sağlayabilirsiniz.  
  
 Aşağıdaki yordam, Windows tabanlı bir uygulamadan yazdırmayı etkinleştirmenin standart yolu olan üzerinde <xref:System.Drawing.Printing.PrintDocument> bir bileşeni olan Windows tabanlı bir uygulama oluşturmanız gerekir. <xref:System.Drawing.Printing.PrintDocument> bileşenini kullanarak Windows Forms yazdırma hakkında daha fazla bilgi için bkz. [nasıl yapılır: standart Windows Forms Yazdırma Işleri oluşturma](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Bir yazdırma işini tamamlamaya yönelik  
  
1. <xref:System.Drawing.Printing.PrintDocument> bileşenin <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliğini ayarlayın.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <xref:System.Drawing.Printing.PrintDocument.EndPrint> olayını işlemek için kod yazın.  
  
     Aşağıdaki kod örneğinde, belgenin yazdırılmasını tamamladığını belirten bir ileti kutusu görüntülenir.  
  
    ```vb  
    Private Sub PrintDocument1_EndPrint(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintEventArgs) Handles PrintDocument1.EndPrint  
       MessageBox.Show(PrintDocument1.DocumentName + " has finished printing.")  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_EndPrint(object sender,   
    System.Drawing.Printing.PrintEventArgs e)  
    {  
       MessageBox.Show(printDocument1.DocumentName +   
          " has finished printing.");  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_EndPrint(System::Object ^ sender,  
          System::Drawing::Printing::PrintEventArgs ^ e)  
       {  
          MessageBox::Show(String::Concat(printDocument1->DocumentName,  
             " has finished printing."));  
       }  
    ```  
  
     (Görsel C# ve görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.printDocument1.EndPrint += new  
       System.Drawing.Printing.PrintEventHandler  
       (this.printDocument1_EndPrint);  
    ```  
  
    ```cpp  
    this->printDocument1->EndPrint += gcnew  
       System::Drawing::Printing::PrintEventHandler  
       (this, &Form1::printDocument1_EndPrint);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Printing.PrintDocument>
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)
