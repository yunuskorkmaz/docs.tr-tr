---
title: 'Nasıl Yapılsın: Grafik Yazdırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: 15f3a507839430ce058302e7f5abd317ef84626f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182531"
---
# <a name="how-to-print-graphics-in-windows-forms"></a>Nasıl yapılır: Windows Forms'ta Grafik Yazdırma
Sık sık, Windows tabanlı uygulamanızda grafik yazdırmak isteyeceksiniz. Sınıf, <xref:System.Drawing.Graphics> ekran veya yazıcı gibi bir aygıta nesne çizmek için yöntemler sağlar.  
  
### <a name="to-print-graphics"></a>Grafik yazdırmak için  
  
1. Formunuza <xref:System.Drawing.Printing.PrintDocument> bir bileşen ekleyin.  
  
2. Olay <xref:System.Drawing.Printing.PrintDocument.PrintPage> işleyicisinde, yazıcıya yazdırmak için ne tür grafikler yazacaklarını öğretmek için <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfın özelliğini kullanın.  
  
     Aşağıdaki kod örneği, sınırlayıcı bir dikdörtgen içinde mavi bir elips oluşturmak için kullanılan bir olay işleyicisi gösterir. Dikdörtgen aşağıdaki konuma ve boyutlara sahiptir: 100'den başlayarak, 150'den başlayarak 250 genişlik ve 250 yüksekliğe sahiptir.  
  
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
  
     (Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.  
  
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
