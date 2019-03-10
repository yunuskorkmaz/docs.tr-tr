---
title: "Nasıl yapılır: Windows Forms'ta grafik yazdırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- graphics [Windows Forms], printing
- printing [Windows Forms], graphics
ms.assetid: 32b891e6-52ff-4fea-a9ff-2ce5db20a4c6
ms.openlocfilehash: cb8c9f291103915c82fb31af5c6668fbd0648f66
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721326"
---
# <a name="how-to-print-graphics-in-windows-forms"></a><span data-ttu-id="d84f6-102">Nasıl yapılır: Windows Forms'ta grafik yazdırma</span><span class="sxs-lookup"><span data-stu-id="d84f6-102">How to: Print Graphics in Windows Forms</span></span>
<span data-ttu-id="d84f6-103">Genellikle, Windows tabanlı uygulamanızdaki grafik yazdırma isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="d84f6-103">Frequently, you will want to print graphics in your Windows-based application.</span></span> <span data-ttu-id="d84f6-104"><xref:System.Drawing.Graphics> Sınıfı bir aygıta bir ekran veya yazıcı gibi çizim nesneleri için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d84f6-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects to a device, such as a screen or printer.</span></span>  
  
### <a name="to-print-graphics"></a><span data-ttu-id="d84f6-105">Grafik yazdırma</span><span class="sxs-lookup"><span data-stu-id="d84f6-105">To print graphics</span></span>  
  
1.  <span data-ttu-id="d84f6-106">Ekleme bir <xref:System.Drawing.Printing.PrintDocument> formunuza bileşen.</span><span class="sxs-lookup"><span data-stu-id="d84f6-106">Add a <xref:System.Drawing.Printing.PrintDocument> component to your form.</span></span>  
  
2.  <span data-ttu-id="d84f6-107">İçinde <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi, kullanım <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> yazdırmak için grafik türüne yazıcıda istemek için sınıf.</span><span class="sxs-lookup"><span data-stu-id="d84f6-107">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class to instruct the printer on what kind of graphics to print.</span></span>  
  
     <span data-ttu-id="d84f6-108">Aşağıdaki kod örneği, sınırlayıcı bir dikdörtgen içinde mavi bir elips oluşturmak için kullanılan bir olay işleyicisi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d84f6-108">The following code example shows an event handler used to create a blue ellipse within a bounding rectangle.</span></span> <span data-ttu-id="d84f6-109">Aşağıdaki konum ve boyut dikdörtgen vardır: 100 ile başlayan 250 genişliği ve yüksekliği 250 ile 150.</span><span class="sxs-lookup"><span data-stu-id="d84f6-109">The rectangle has the following location and dimensions: beginning at 100, 150 with a width of 250 and a height of 250.</span></span>  
  
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
  
     <span data-ttu-id="d84f6-110">(Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d84f6-110">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d84f6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d84f6-111">See also</span></span>
- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="d84f6-112">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="d84f6-112">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
