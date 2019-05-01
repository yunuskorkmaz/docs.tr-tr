---
title: PrintDocument Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
ms.openlocfilehash: a3f08aa4bd5b63769cef35dbea2209d5d83261be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012626"
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="663bb-102">PrintDocument Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="663bb-102">PrintDocument Component Overview (Windows Forms)</span></span>
<span data-ttu-id="663bb-103">Windows Forms [PrintDocument](printdocument-component-windows-forms.md) bileşen ne tanımlayan özellikleri ve Windows tabanlı uygulamalar içinde belge yazdırma özelliğini ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="663bb-103">The Windows Forms [PrintDocument](printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="663bb-104">İle birlikte kullanılabilir [PrintDialog](printdialog-component-windows-forms.md) belge yazdırma tüm yönlerini denetiminde olmasını bileşeni.</span><span class="sxs-lookup"><span data-stu-id="663bb-104">It can be used in conjunction with the [PrintDialog](printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>  
  
## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="663bb-105">PrintDocument bileşeni ile çalışma</span><span class="sxs-lookup"><span data-stu-id="663bb-105">Working with the PrintDocument Component</span></span>  
 <span data-ttu-id="663bb-106">İki içeren ana senaryoları <xref:System.Drawing.Printing.PrintDocument> bileşeni şunlardır:</span><span class="sxs-lookup"><span data-stu-id="663bb-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>  
  
- <span data-ttu-id="663bb-107">Bireysel metin dosyası yazdırma gibi basit yazdırma işler.</span><span class="sxs-lookup"><span data-stu-id="663bb-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="663bb-108">Böyle bir durumda, eklediğiniz <xref:System.Drawing.Printing.PrintDocument> Windows Form, bileşene, ardından bir dosyaya yazdırır programlama mantığı eklemek <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="663bb-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="663bb-109">Programlama mantığı ile sizin <xref:System.Drawing.Printing.PrintDocument.Print%2A> belge yazdırma için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="663bb-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="663bb-110">Bu yöntem gönderir bir <xref:System.Drawing.Graphics> bulunan nesne <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfına yazıcı.</span><span class="sxs-lookup"><span data-stu-id="663bb-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="663bb-111">Bir metin belgesini kullanarak yazdırma gösteren bir örnek <xref:System.Drawing.Printing.PrintDocument> bileşeni Bkz [nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="663bb-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>  
  
- <span data-ttu-id="663bb-112">Daha karmaşık yazdırma işlerini yazdırma mantıksal yazdığınız yeniden istediğiniz bir durum gibi.</span><span class="sxs-lookup"><span data-stu-id="663bb-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="663bb-113">Böyle bir durumda yeni bir bileşenden türetin <xref:System.Drawing.Printing.PrintDocument> bileşeni ve geçersiz kılma (bkz [geçersiz kılmalar](~/docs/visual-basic/language-reference/modifiers/overrides.md) Visual Basic veya [geçersiz kılma](~/docs/csharp/language-reference/keywords/override.md) için C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.</span><span class="sxs-lookup"><span data-stu-id="663bb-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](~/docs/visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](~/docs/csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
 <span data-ttu-id="663bb-114">Bir forma eklendiğinde <xref:System.Drawing.Printing.PrintDocument> bileşeni Tepsi Windows Form Tasarımcısı'nın altındaki görünür.</span><span class="sxs-lookup"><span data-stu-id="663bb-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="663bb-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="663bb-115">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Printing.PrintDocument>
- [<span data-ttu-id="663bb-116">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="663bb-116">Windows Forms Print Support</span></span>](../advanced/windows-forms-print-support.md)
- [<span data-ttu-id="663bb-117">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="663bb-117">PrintDocument Component</span></span>](printdocument-component-windows-forms.md)
