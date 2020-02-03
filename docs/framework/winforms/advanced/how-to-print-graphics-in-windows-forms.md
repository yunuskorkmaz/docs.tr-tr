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
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="75ce9-102">Nasıl yapılır: Windows Forms'ta Grafik Yazdırma</span><span class="sxs-lookup"><span data-stu-id="75ce9-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="75ce9-103">Genellikle, Windows tabanlı uygulamanızda grafik yazdırmak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="75ce9-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="75ce9-104"><xref:System.Drawing.Graphics> sınıfı, nesneleri bir ekran veya yazıcı gibi bir cihaza çizmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="75ce9-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="75ce9-105">Grafik yazdırma</span><span class="sxs-lookup"><span data-stu-id="75ce9-105">To print graphics</span></span>  
  
1. <span data-ttu-id="75ce9-106">Formunuza bir <xref:System.Drawing.Printing.PrintDocument> bileşeni ekleyin.</span><span class="sxs-lookup"><span data-stu-id="75ce9-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2. <span data-ttu-id="75ce9-107"><xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde, yazıcıya hangi tür grafiklerin yazdırılacağını bildirmek için <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="75ce9-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="75ce9-108">Aşağıdaki kod örneğinde, bir sınırlayıcı dikdörtgen içinde mavi bir elips oluşturmak için kullanılan bir olay işleyicisi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="75ce9-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="75ce9-109">Dikdörtgen aşağıdaki konum ve boyutlara sahiptir: 100 ve 150 ' den başlayarak, 250 ve 250 yüksekliğiyle.</span><span class="sxs-lookup"><span data-stu-id="75ce9-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
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
  
     <span data-ttu-id="75ce9-110">(Görsel C# ve görsel C++) Olay işleyicisini kaydetmek için formun oluşturucusuna aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="75ce9-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="75ce9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="75ce9-111">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="75ce9-112">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="75ce9-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
