---
title: 'Nasıl Yapılır: PrintForm Bileşenini Kullanarak Form Yazdırma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Form [Visual Basic], printing
ms.assetid: df963bf6-3ee1-49f4-8b2e-1d95d1beb0be
ms.openlocfilehash: 5f8e620fce2b85d3f3cdb66bf80967f8eb281361
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590019"
---
# <a name="how-to-print-a-form-by-using-the-printform-component-visual-basic"></a><span data-ttu-id="4ff9c-102">Nasıl Yapılır: PrintForm Bileşenini Kullanarak Form Yazdırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4ff9c-102">How to: Print a Form by Using the PrintForm Component (Visual Basic)</span></span>
<span data-ttu-id="4ff9c-103"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen sağlar, ekranda kullanmadan göründüğü gibi hızlı bir form görüntüsü yazdırmak bir <xref:System.Drawing.Printing.PrintDocument> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-103">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component enables you to quickly print an image of a form exactly as it appears on screen without using a <xref:System.Drawing.Printing.PrintDocument> component.</span></span> <span data-ttu-id="4ff9c-104">Aşağıdaki yordamlar, bir yazıcı, Baskı Önizleme penceresinden ve kapsüllenmiş PostScript'i dosya form yazdırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-104">The following procedures show how to print a form to a printer, to a print preview window, and to an Encapsulated PostScript file.</span></span>  
  
 <span data-ttu-id="4ff9c-105">PowerPack denetimleri artık Visual Studio'ya dahil olan, ancak bunları indirebilirsiniz [Yükleme Merkezi'nden](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span><span class="sxs-lookup"><span data-stu-id="4ff9c-105">The PowerPack controls are no longer included in Visual Studio, but you can download them from the [Download Center](http://www.microsoft.com/en-us/download/details.aspx?id=25169).</span></span>  
  
### <a name="to-print-a-form-to-the-default-printer"></a><span data-ttu-id="4ff9c-106">Varsayılan yazıcı için bir form yazdırma</span><span class="sxs-lookup"><span data-stu-id="4ff9c-106">To print a form to the default printer</span></span>  
  
1.  <span data-ttu-id="4ff9c-107">İçinde **araç**, tıklatın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-107">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="4ff9c-108"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen için bileşen Tepsisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-108">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="4ff9c-109">İçinde **özellikleri** penceresindeki ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğine <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-109">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPrinter>.</span></span>  
  
3.  <span data-ttu-id="4ff9c-110">Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` olay işleyicisi için bir **yazdırma**`Button`).</span><span class="sxs-lookup"><span data-stu-id="4ff9c-110">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-display-a-form-in-a-print-preview-window"></a><span data-ttu-id="4ff9c-111">Baskı Önizleme penceresinde bir form görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="4ff9c-111">To display a form in a print preview window</span></span>  
  
1.  <span data-ttu-id="4ff9c-112">İçinde **araç**, tıklatın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-112">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="4ff9c-113"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen için bileşen Tepsisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-113">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="4ff9c-114">İçinde **özellikleri** penceresindeki ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğine <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-114">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToPreview>.</span></span>  
  
3.  <span data-ttu-id="4ff9c-115">Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` olay işleyicisi için bir **yazdırma**`Button`).</span><span class="sxs-lookup"><span data-stu-id="4ff9c-115">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
### <a name="to-print-a-form-to-a-file"></a><span data-ttu-id="4ff9c-116">Bir dosya için bir form yazdırma</span><span class="sxs-lookup"><span data-stu-id="4ff9c-116">To print a form to a file</span></span>  
  
1.  <span data-ttu-id="4ff9c-117">İçinde **araç**, tıklatın **Visual Basic PowerPacks** sekmesini ve ardından sürükleyin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> forma bileşen.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-117">In the **Toolbox**, click the **Visual Basic PowerPacks** tab and then drag the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component onto the form.</span></span>  
  
     <span data-ttu-id="4ff9c-118"><xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Bileşen için bileşen Tepsisi eklenir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-118">The <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> component is added to the component tray.</span></span>  
  
2.  <span data-ttu-id="4ff9c-119">İçinde **özellikleri** penceresindeki ayarlayın <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> özelliğine <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-119">In the **Properties** window, set the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> property to <xref:System.Drawing.Printing.PrintAction.PrintToFile>.</span></span>  
  
3.  <span data-ttu-id="4ff9c-120">İsteğe bağlı olarak, seçin <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> özelliği ve türü tam yolunu ve dosya için hedef dosya adı.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-120">Optionally, select the <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> property and type the full path and file name for the destination file.</span></span>  
  
     <span data-ttu-id="4ff9c-121">Bu adımı atlarsanız, kullanıcı çalışma zamanında için bir dosya adı istenir.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-121">If you skip this step, the user will be prompted for a file name at run time.</span></span>  
  
4.  <span data-ttu-id="4ff9c-122">Uygun olay işleyicisine aşağıdaki kodu ekleyin (örneğin, `Click` olay işleyicisi için bir **yazdırma**`Button`).</span><span class="sxs-lookup"><span data-stu-id="4ff9c-122">Add the following code in the appropriate event handler (for example, in the `Click` event handler for a **Print**`Button`).</span></span>  
  
    ```  
    PrintForm1.Print()  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="4ff9c-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ff9c-123">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>  
 [<span data-ttu-id="4ff9c-124">Nasıl Yapılır: Formun İstemci Alanını Yazdırma</span><span class="sxs-lookup"><span data-stu-id="4ff9c-124">How to: Print the Client Area of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [<span data-ttu-id="4ff9c-125">Nasıl Yapılır: Formun İstemci Alanlarını ve Diğerlerini Yazdırma</span><span class="sxs-lookup"><span data-stu-id="4ff9c-125">How to: Print Client and Non-Client Areas of a Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [<span data-ttu-id="4ff9c-126">Nasıl Yapılır: Kaydırılabilir Form Yazdırma</span><span class="sxs-lookup"><span data-stu-id="4ff9c-126">How to: Print a Scrollable Form</span></span>](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)  
 [<span data-ttu-id="4ff9c-127">PrintForm Bileşeni</span><span class="sxs-lookup"><span data-stu-id="4ff9c-127">PrintForm Component</span></span>](../../../visual-basic/developing-apps/printing/printform-component.md)
