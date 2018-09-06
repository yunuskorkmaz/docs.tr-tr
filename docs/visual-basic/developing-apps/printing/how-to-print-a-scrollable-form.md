---
title: 'Nasıl Yapılır: Kaydırılabilir Form Yazdırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- entire form [Visual Basic], printing
- scrollable form [Visual Basic], printing
ms.assetid: 1196e1cf-b77f-4928-a3e4-85b51ba3787d
ms.openlocfilehash: 4a509b7c48f2bff705bc95e58fb88252cb8ca4b9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779425"
---
# <a name="how-to-print-a-scrollable-form-visual-basic"></a><span data-ttu-id="46cda-102">Nasıl Yapılır: Kaydırılabilir Form Yazdırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46cda-102">How to: Print a Scrollable Form (Visual Basic)</span></span>
<span data-ttu-id="46cda-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen kullanmadan bir form görüntüsü hızla yazdırmanızı sağlar bir <xref:System.Drawing.Printing.PrintDocument> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="46cda-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="46cda-104">Varsayılan olarak, yalnızca şu anda görünür bölüme biçiminde yazdırılır. Kullanıcı formu çalışma zamanında yeniden boyutlandırılmış, görüntü beklendiği gibi yazdırabilir değil.</span><span class="sxs-lookup"><span data-stu-id="46cda-104">By default, only the currently visible part of the form is printed; if a user has resized the form at run time, the image may not print as intended.</span></span> <span data-ttu-id="46cda-105">Formu yeniden boyutlandırıldı bile aşağıdaki yordamı kaydırılabilir form, tam istemci alanını yazdırma nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="46cda-105">The following procedure shows how to print the complete client area of a scrollable form, even if the form has been resized.</span></span>  
  
 <span data-ttu-id="46cda-106">PowerPack denetimleri artık Visual Studio'ya dahil, ancak bunları indirebilirsiniz [İndirme Merkezi](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="46cda-106">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](https://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-the-complete-client-area-of-a-scrollable-form"></a><span data-ttu-id="46cda-107">Kaydırılabilir form tam istemci alanını yazdırma</span><span class="sxs-lookup"><span data-stu-id="46cda-107">To print the complete client area of a scrollable form</span></span>  
  
1.  <span data-ttu-id="46cda-108">İçinde **araç kutusu**, tıklayın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="46cda-108">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="46cda-109"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşeni bileşen tepsisine eklenir.</span><span class="sxs-lookup"><span data-stu-id="46cda-109">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component will be added to the component tray.</span></span>  
  
2.  <span data-ttu-id="46cda-110">İçinde **özellikleri** penceresinde <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğini <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="46cda-110">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="46cda-111">Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` için olay işleyicisi bir **yazdırma**`Button`).</span><span class="sxs-lookup"><span data-stu-id="46cda-111">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print(Me, PowerPacks.Printing.PrintForm.PrintOption.Scrollable)  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="46cda-112">Bazı işletim sistemleri, metin veya grafikleri tarafından çizilen <xref:System.Drawing.Graphics> yöntemleri yazdırma doğru.</span><span class="sxs-lookup"><span data-stu-id="46cda-112">On some operating systems, text or graphics drawn by <xref:System.Drawing.Graphics> methods may not print correctly.</span></span> <span data-ttu-id="46cda-113">Bu durumda, yazdırmak mümkün olmayacaktır `Scrollable` parametresi.</span><span class="sxs-lookup"><span data-stu-id="46cda-113">In this case, you will not be able to print with the `Scrollable` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cda-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="46cda-114">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 [<span data-ttu-id="46cda-115">PrintForm Bileşeni</span><span class="sxs-lookup"><span data-stu-id="46cda-115">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)  
 [<span data-ttu-id="46cda-116">Nasıl Yapılır: Formun İstemci Alanını Yazdırma</span><span class="sxs-lookup"><span data-stu-id="46cda-116">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="46cda-117">Nasıl Yapılır: Formun İstemci Alanlarını ve Diğerlerini Yazdırma</span><span class="sxs-lookup"><span data-stu-id="46cda-117">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)
