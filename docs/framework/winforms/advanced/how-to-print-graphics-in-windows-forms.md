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
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="2b9c4-102">Nasıl yapılır: Windows Forms'ta Grafik Yazdırma</span><span class="sxs-lookup"><span data-stu-id="2b9c4-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="2b9c4-103">Sık sık, Windows tabanlı uygulamanızda grafik yazdırmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="2b9c4-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="2b9c4-104">Sınıf, <xref:System.Drawing.Graphics> ekran veya yazıcı gibi bir aygıta nesne çizmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2b9c4-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="2b9c4-105">Grafik yazdırmak için</span><span class="sxs-lookup"><span data-stu-id="2b9c4-105">To print graphics</span></span>  
  
1. <span data-ttu-id="2b9c4-106">Formunuza <xref:System.Drawing.Printing.PrintDocument> bir bileşen ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2b9c4-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="2b9c4-107">Olay <xref:System.Drawing.Printing.PrintDocument.PrintPage> işleyicisinde, yazıcıya yazdırmak için ne tür grafikler yazacaklarını öğretmek için <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfın özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="2b9c4-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="2b9c4-108">Aşağıdaki kod örneği, sınırlayıcı bir dikdörtgen içinde mavi bir elips oluşturmak için kullanılan bir olay işleyicisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="2b9c4-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="2b9c4-109">Dikdörtgen aşağıdaki konuma ve boyutlara sahiptir: 100'den başlayarak, 150'den başlayarak 250 genişlik ve 250 yüksekliğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="2b9c4-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
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
  
     <span data-ttu-id="2b9c4-110">(Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="2b9c4-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2b9c4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2b9c4-111">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="2b9c4-112">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="2b9c4-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
