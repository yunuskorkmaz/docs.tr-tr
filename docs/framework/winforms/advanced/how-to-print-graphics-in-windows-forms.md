---
title: 'Nasıl yapılır: grafik yazdırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 2435b3bc14747a00d2a0fc03a9ebd21ae43c5369
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740649"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Grafik Yazdırma
Genellikle, Windows tabanlı uygulamanızda grafik yazdırmak isteyeceksiniz. <xref:System.Drawing.Graphics> sınıfı, nesneleri bir ekran veya yazıcı gibi bir cihaza çizmek için yöntemler sağlar.  
  
### <a name="to-print-graphics"></a>Grafik yazdırma  
  
1. Formunuza bir <xref:System.Drawing.Printing.PrintDocument> bileşeni ekleyin.  
  
2. <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde, yazıcıya hangi tür grafiklerin yazdırılacağını bildirmek için <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğini kullanın.  
  
     Aşağıdaki kod örneğinde, bir sınırlayıcı dikdörtgen içinde mavi bir elips oluşturmak için kullanılan bir olay işleyicisi gösterilmektedir. Dikdörtgen aşağıdaki konum ve boyutlara sahiptir: 100 ve 150 ' den başlayarak, 250 ve 250 yüksekliğiyle.  
  
    ```vb  
    Private Sub PrintDocument1_PrintPage(ByVal sender As Object, ByVal e As System.Drawing.Printing.PrintPageEventArgs) Handles PrintDocument1.PrintPage  
       e.Graphics.FillEllipse(Brushes.Blue, New Rectangle(100, 150, 250, 250))  
    End Sub  
    ```  
  
    ```csharp  
    private void printDocument1_PrintPage(object sender,   
    System.Drawing.Printing.PrintPageEventArgs e)  
    {  
       e.Graphics.FillRectangle(Brushes.Blue,   
         new Rectangle(100, 150, 250, 250));  
    }  
    ```  
  
    ```cpp  
    private:  
       void printDocument1_PrintPage(System::Object ^ sender,  
          System::Drawing::Printing::PrintPageEventArgs ^ e)  
       {  
          e->Graphics->FillRectangle(Brushes::Blue,  
             Rectangle(100, 150, 250, 250));  
       }  
    ```  
  
     (Görsel C# ve görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.  
  
    ```csharp  
    this.printDocument1.PrintPage += new  
       System.Drawing.Printing.PrintPageEventHandler  
       (this.printDocument1_PrintPage);  
    ```  
  
    ```cpp  
    this->printDocument1->PrintPage += gcnew  
       System::Drawing::Printing::PrintPageEventHandler  
       (this, &Form1::printDocument1_PrintPage);  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [Windows Forms Yazdırma Desteği](windows-forms-print-support.md)
