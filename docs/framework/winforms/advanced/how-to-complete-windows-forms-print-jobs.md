---
title: 'Nasıl yapılır: Windows Forms Yazdırma İşlerini Tamamlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- print jobs [Windows Forms], completing in Windows Forms
- printing [Windows Forms], print jobs
ms.assetid: 23ec74f7-34c5-4710-82a0-ee2914518548
ms.openlocfilehash: a95e07596a10e67d32fdd0af036a14e8d66390c7
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053030"
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Nasıl yapılır: Windows Forms Yazdırma İşlerini Tamamlama
Genellikle, sözcük işlemciler ve yazdırma gerektiren diğer uygulamaları yazdırma işi tamamlandığını kullanıcılara bir ileti görüntülemek için seçeneği sunacak. Bu işlevsellik, Windows Forms'ta işleyerek sağlayabilir <xref:System.Drawing.Printing.PrintDocument.EndPrint> olayı <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
 Aşağıdaki yordam, Windows tabanlı bir uygulama ile oluşturduğunuz gerektirir bir <xref:System.Drawing.Printing.PrintDocument> bileşen üzerindeki, Windows tabanlı bir uygulama yazdırma etkinleştirme standart yoludur. Kullanarak Windows Forms yazdırma hakkında daha fazla bilgi için <xref:System.Drawing.Printing.PrintDocument> bileşeni Bkz [nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma](how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Yazdırma işi tamamlamak için  
  
1. Ayarlama <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliği <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2. İşlemek için kod yazma <xref:System.Drawing.Printing.PrintDocument.EndPrint> olay.  
  
     Aşağıdaki kod örneğinde, belgeyi yazdırma tamamlandığını belirten bir ileti kutusu görüntülenir.  
  
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
  
     (Visual C# ve görsel C++) Aşağıdaki kod, olay işleyicisi kaydetmek için formun oluşturucuda yerleştirin.  
  
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
