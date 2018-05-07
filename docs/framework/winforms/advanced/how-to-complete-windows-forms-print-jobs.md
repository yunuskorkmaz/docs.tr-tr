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
ms.openlocfilehash: 74a8e3721df72415437dd0c39b3298d67c19990b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-complete-windows-forms-print-jobs"></a>Nasıl yapılır: Windows Forms Yazdırma İşlerini Tamamlama
Genellikle, sözcük işlemciler ve yazdırma ile ilgili diğer uygulamaları bir ileti bir yazdırma işi tamamlandıktan kullanıcılara görüntülenecek seçeneğini sağlar. Windows Forms'ta işleyerek bu işlevselliği sağlayabilen <xref:System.Drawing.Printing.PrintDocument.EndPrint> olayı <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
 Aşağıdaki yordam Windows tabanlı bir uygulama ile oluşturduğunuz gerektiren bir <xref:System.Drawing.Printing.PrintDocument> bileşen üzerindeki, Windows tabanlı bir uygulama yazıcıdan etkinleştirme standart yoludur. Windows Forms kullanarak yazdırma hakkında daha fazla bilgi için <xref:System.Drawing.Printing.PrintDocument> bileşeni Bkz [nasıl yapılır: standart Windows Forms yazdırma işleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md).  
  
### <a name="to-complete-a-print-job"></a>Yazdırma işi tamamlamak için  
  
1.  Ayarlama <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliği <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
    ```vb  
    PrintDocument1.DocumentName = "MyTextFile"  
    ```  
  
    ```csharp  
    printDocument1.DocumentName = "MyTextFile";  
    ```  
  
    ```cpp  
    printDocument1->DocumentName = "MyTextFile";  
    ```  
  
2.  İşlemek için kod yazma <xref:System.Drawing.Printing.PrintDocument.EndPrint> olay.  
  
     Aşağıdaki kod örneğinde, belge yazdırma tamamlandığını belirten bir ileti kutusu görüntülenir.  
  
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
  
     (Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Windows Forms Yazdırma Desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
