---
title: Tam Yazdırma İşleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: 62f67002bfbaf46e73bae06fdaff26efde865c06
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182593"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Nasıl yapılır: Windows Forms Yazdırma İşlerini Tamamlama
Sık sık, sözcük işlemcileri ve yazdırma içeren diğer uygulamalar, kullanıcılara yazdırma işinin tamamladığını belirten bir ileti görüntüleme seçeneği sağlar. Bu <xref:System.Drawing.Printing.PrintDocument.EndPrint> <xref:System.Drawing.Printing.PrintDocument> işlevselliği, bileşenin olayını işleyerek Windows Formlarınızda sağlayabilirsiniz.  
  
 Aşağıdaki yordam, üzerinde bir bileşen bulunan Windows <xref:System.Drawing.Printing.PrintDocument> tabanlı bir uygulama oluşturmanızı gerektirir ve bu da Windows tabanlı bir uygulamadan yazdırmayı etkinleştirmenin standart yoludur. Bileşeni kullanarak Windows Formlarından yazdırma hakkında daha fazla bilgi için [bkz: Standart Windows Formları Yazdırma İşleri Oluşturma](how-to-create-standard-windows-forms-print-jobs.md). <xref:System.Drawing.Printing.PrintDocument>  
  
### <a name="to-complete-a-print-job"></a>Yazdırma işini tamamlamak için  
  
1. Bileşenin <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliğini <xref:System.Drawing.Printing.PrintDocument> ayarlayın.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. <xref:System.Drawing.Printing.PrintDocument.EndPrint> Olayı işlemek için kod yazın.  
  
     Aşağıdaki kod örneğinde, belgenin yazdırmayı tamamladığını belirten bir ileti kutusu görüntülenir.  
  
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
  
     (Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
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
