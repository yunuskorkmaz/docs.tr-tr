---
title: PrintDocument Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: 16a7f3a34ccb280f7bf91c52e29b20edc22130b9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928985"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="24714-102">PrintDocument Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="24714-102">PrintDocument Component Overview (Windows Forms)</span></span>

<span data-ttu-id="24714-103">Windows Forms [PrintDocument](printdocument-component-windows-forms.md) bileşeni, nelerin yazdırılacağını betimleyen özellikleri ve Windows tabanlı uygulamalar içinde belge yazdırma özelliğini ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="24714-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="24714-104">Belge yazdırmanın tüm yönlerinin denetiminde olması için [PrintDialog](printdialog-component-windows-forms.md) bileşeniyle birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="24714-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>

## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="24714-105">PrintDocument bileşeniyle çalışma</span><span class="sxs-lookup"><span data-stu-id="24714-105">Working with the PrintDocument Component</span></span>

<span data-ttu-id="24714-106"><xref:System.Drawing.Printing.PrintDocument> Bileşeni içeren temel senaryolardan ikisi şunlardır:</span><span class="sxs-lookup"><span data-stu-id="24714-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>

- <span data-ttu-id="24714-107">Tek bir metin dosyası yazdırma gibi basit yazdırma işleri.</span><span class="sxs-lookup"><span data-stu-id="24714-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="24714-108">Böyle bir durumda, <xref:System.Drawing.Printing.PrintDocument> bileşeni bir Windows formuna eklemeli ve ardından <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisine bir dosya yazdıran programlama mantığını eklersiniz.</span><span class="sxs-lookup"><span data-stu-id="24714-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="24714-109">Programlama mantığı, belgeyi yazdırma <xref:System.Drawing.Printing.PrintDocument.Print%2A> yöntemiyle birlikte olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="24714-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="24714-110">Bu yöntem, <xref:System.Drawing.Graphics> <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğinde yer alan bir nesneyi yazıcıya gönderir.</span><span class="sxs-lookup"><span data-stu-id="24714-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="24714-111"><xref:System.Drawing.Printing.PrintDocument> Bileşeni kullanarak nasıl metin belgesi yazdırılacağını gösteren bir örnek için bkz [. nasıl yapılır: Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)bir çok sayfalı metin dosyası yazdırın.</span><span class="sxs-lookup"><span data-stu-id="24714-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>

- <span data-ttu-id="24714-112">Yazdığınız yazdırma mantığını yeniden kullanmak istediğiniz durumlar gibi daha karmaşık yazdırma işleri.</span><span class="sxs-lookup"><span data-stu-id="24714-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="24714-113">Böyle bir durumda <xref:System.Drawing.Printing.PrintDocument> , bileşenden yeni bir bileşen türetirsiniz ve <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı geçersiz kılarsınız (için C#bkz. Visual Basic veya [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) için [geçersiz kılmalar](../../../visual-basic/language-reference/modifiers/overrides.md) ).</span><span class="sxs-lookup"><span data-stu-id="24714-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](../../../csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>

<span data-ttu-id="24714-114">Bir forma <xref:System.Drawing.Printing.PrintDocument> eklendiğinde bileşen, Visual Studio 'daki Windows Form Tasarımcısı alt kısmındaki tepside görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="24714-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="24714-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24714-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="24714-116">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="24714-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="24714-117">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="24714-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
