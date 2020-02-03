---
title: PrintDocument Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a82cc0cdcb8cfae796c9c6bf60ab73873f85a291
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728548"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="e78ad-102">PrintDocument Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e78ad-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="e78ad-103">Windows Forms [PrintDocument](printdocument-component-windows-forms.md) bileşeni, nelerin yazdırılacağını betimleyen özellikleri ve Windows tabanlı uygulamalar içinde belge yazdırma özelliğini ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e78ad-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="e78ad-104">Belge yazdırmanın tüm yönlerinin denetiminde olması için [PrintDialog](printdialog-component-windows-forms.md) bileşeniyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e78ad-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="e78ad-105">PrintDocument bileşeniyle çalışma</span><span class="sxs-lookup"><span data-stu-id="e78ad-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="e78ad-106"><xref:System.Drawing.Printing.PrintDocument> bileşeni içeren temel senaryolardan ikisi şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e78ad-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="e78ad-107">Tek bir metin dosyası yazdırma gibi basit yazdırma işleri.</span><span class="sxs-lookup"><span data-stu-id="e78ad-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="e78ad-108">Böyle bir durumda, <xref:System.Drawing.Printing.PrintDocument> bileşenini bir Windows formuna eklemeniz ve sonra <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisine bir dosya yazdıran programlama mantığını eklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e78ad-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="e78ad-109">Programlama mantığı, belgeyi yazdırmak için <xref:System.Drawing.Printing.PrintDocument.Print%2A> yöntemiyle birlikte olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e78ad-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="e78ad-110">Bu yöntem, <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğinde bulunan <xref:System.Drawing.Graphics> nesnesini yazıcıya gönderir.</span><span class="sxs-lookup"><span data-stu-id="e78ad-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="e78ad-111"><xref:System.Drawing.Printing.PrintDocument> bileşenini kullanarak bir metin belgesinin nasıl yazdırılacağını gösteren bir örnek için, bkz. [nasıl yapılır: Windows Forms Içinde çok sayfalı metin dosyası yazdırma](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e78ad-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="e78ad-112">Yazdığınız yazdırma mantığını yeniden kullanmak istediğiniz durumlar gibi daha karmaşık yazdırma işleri.</span><span class="sxs-lookup"><span data-stu-id="e78ad-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="e78ad-113">Böyle bir durumda, <xref:System.Drawing.Printing.PrintDocument> bileşeninden yeni bir bileşen türetirsiniz ve <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı geçersiz kılmalısınız (bkz. Visual Basic veya [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) Için C# [geçersiz kılmalar](../../../visual-basic/language-reference/modifiers/overrides.md) ).</span><span class="sxs-lookup"><span data-stu-id="e78ad-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="e78ad-114">Bir forma eklendiğinde <xref:System.Drawing.Printing.PrintDocument> bileşeni, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e78ad-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="e78ad-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e78ad-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="e78ad-116">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="e78ad-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="e78ad-117">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="e78ad-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
