---
title: 'Nasıl Yapılır: Formun İstemci Alanlarını ve Diğerlerini Yazdırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- title bar [Visual Basic], printing
- printing
- borders [Visual Basic], printing
- entire form
- non-client area [Visual Basic], printing
ms.assetid: 856bb0e4-dbc3-47e2-81cd-4b376cf07757
ms.openlocfilehash: 5109993146a8d53d5cbeebcc52c018a6f0f57ed5
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723282"
---
# <a name="how-to-print-client-and-non-client-areas-of-a-form-visual-basic"></a><span data-ttu-id="f6ed1-102">Nasıl Yapılır: Formun İstemci Alanlarını ve Diğerlerini Yazdırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f6ed1-102">How to: Print Client and Non-Client Areas of a Form (Visual Basic)</span></span>
<span data-ttu-id="f6ed1-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşeni ekranda kullanmadan göründüğü gibi hızlı bir şekilde bir form görüntüsü baskı sağlar bir <xref:System.Drawing.Printing.PrintDocument> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="f6ed1-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="f6ed1-104">Aşağıdaki yordam, hem istemci hem de istemci dışı alan dahil olmak üzere, bir form yazdırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f6ed1-104">The following procedure shows how to print a form, including both the client area and the non-client area.</span></span> <span data-ttu-id="f6ed1-105">İstemci olmayan alanın başlık çubuğunun kenarlık ve kaydırma içerir çubukları.</span><span class="sxs-lookup"><span data-stu-id="f6ed1-105">The non-client area includes the title bar, borders, and scroll bars.</span></span>  
  
 <span data-ttu-id="f6ed1-106">PowerPack denetimleri artık Visual Studio'ya dahil, ancak bunları indirebilirsiniz [İndirme Merkezi](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="f6ed1-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-both-the-client-and-the-non-client-areas-of-a-form"></a><span data-ttu-id="f6ed1-107">Hem istemci hem de istemci dışı alanlar formun yazdırmak için</span><span class="sxs-lookup"><span data-stu-id="f6ed1-107">To print both the client and the non-client areas of a form</span></span>  
  
1.  <span data-ttu-id="f6ed1-108">İçinde **araç kutusu**, tıklayın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="f6ed1-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="f6ed1-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen, bileşen tepsisine eklenir.</span><span class="sxs-lookup"><span data-stu-id="f6ed1-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="f6ed1-110">İçinde **özellikleri** penceresinde <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğini <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="f6ed1-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="f6ed1-111">Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` yazdırma için olay işleyicisi `Button`).</span><span class="sxs-lookup"><span data-stu-id="f6ed1-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a Print `Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.FullWindow)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="f6ed1-112">Bazı işletim sistemleri, metin veya grafikleri tarafından çizilen <xref:System.Drawing.Graphics> yöntemleri yazdırma doğru.</span><span class="sxs-lookup"><span data-stu-id="f6ed1-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="f6ed1-113">İn this Case, uyumlu yazdırma yöntemi kullanın: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span><span class="sxs-lookup"><span data-stu-id="f6ed1-113">In this case, use the compatible printing method: `PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.CompatibleModeFullWindow`).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ed1-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f6ed1-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="f6ed1-115">PrintForm Bileşeni</span><span class="sxs-lookup"><span data-stu-id="f6ed1-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="f6ed1-116">Nasıl Yapılır: Kaydırılabilir Form Yazdırma</span><span class="sxs-lookup"><span data-stu-id="f6ed1-116">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
