---
title: 'Nasıl Yapılır: Formun İstemci Alanını Yazdırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- client area [Visual Basic], printing
ms.assetid: c06c9c0e-bc07-48cd-9596-e29a2ff96236
ms.openlocfilehash: 361db89f0880a03273aac7fc36b5c5faa825486f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583997"
---
# <a name="how-to-print-the-client-area-of-a-form-visual-basic"></a><span data-ttu-id="7a89f-102">Nasıl Yapılır: Formun İstemci Alanını Yazdırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7a89f-102">How to: Print the Client Area of a Form (Visual Basic)</span></span>
<span data-ttu-id="7a89f-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen sağlar, hızlı bir form görüntüsü kullanmadan yazdırmak bir <xref:System.Drawing.Printing.PrintDocument> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="7a89f-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="7a89f-104">Aşağıdaki yordam yalnızca başlık çubuğu, kenarlıklar ve kaydırma çubukları olmadan bir formun istemci alanını yazdırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7a89f-104">The following procedure shows how to print just the client area of a form, without the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="7a89f-105">PowerPack denetimleri artık Visual Studio'ya dahil olan, ancak bunları indirebilirsiniz [Yükleme Merkezi'nden](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="7a89f-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-client-area-of-a-form"></a><span data-ttu-id="7a89f-106">Formun istemci alanını yazdırma</span><span class="sxs-lookup"><span data-stu-id="7a89f-106">To print the client area of a form</span></span>  
  
1.  <span data-ttu-id="7a89f-107">İçinde **araç**, tıklatın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="7a89f-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="7a89f-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen için bileşen Tepsisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="7a89f-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="7a89f-109">İçinde **özellikleri** penceresindeki ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğine <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="7a89f-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="7a89f-110">Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` olay işleyicisi için bir **yazdırma**`Button`).</span><span class="sxs-lookup"><span data-stu-id="7a89f-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.ClientAreaOnly)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="7a89f-111">Bazı işletim sistemleri, metin veya tarafından çizilmiş grafik <xref:System.Drawing.Graphics> yöntemleri yazdırma doğru.</span><span class="sxs-lookup"><span data-stu-id="7a89f-111">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="7a89f-112">Bu durumda, uyumlu yazdırma yöntemi kullanın: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span><span class="sxs-lookup"><span data-stu-id="7a89f-112">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption CompatibleModeClientAreaOnly).`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a89f-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7a89f-113">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="7a89f-114">PrintForm Bileşeni</span><span class="sxs-lookup"><span data-stu-id="7a89f-114">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="7a89f-115">Nasıl Yapılır: Formun İstemci Alanlarını ve Diğerlerini Yazdırma</span><span class="sxs-lookup"><span data-stu-id="7a89f-115">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="7a89f-116">Nasıl Yapılır: Kaydırılabilir Form Yazdırma</span><span class="sxs-lookup"><span data-stu-id="7a89f-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
