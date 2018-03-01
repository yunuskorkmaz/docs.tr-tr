---
title: "PrintDocument Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintDocument
helpviewer_keywords:
- PrintDocument component [Windows Forms], about PrintDocument component
- printing [Windows Forms], PrintDocument component
ms.assetid: b59b4b60-dce5-42ca-8421-3a54a2f7bab0
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 414a7972550558b40403b7f4cbfd9a49194666be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="printdocument-component-overview-windows-forms"></a><span data-ttu-id="ffc60-102">PrintDocument Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ffc60-102">PrintDocument Component Overview (Windows Forms)</span></span>
<span data-ttu-id="ffc60-103">Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) bileşen ne yazdırma açıklayın özellikleri ve Windows tabanlı uygulamalar içinde belge yazdırma olanağı ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ffc60-103">The Windows Forms [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) component is used to set the properties that describe what to print and the ability to print the document within Windows-based applications.</span></span> <span data-ttu-id="ffc60-104">İle birlikte kullanılabilir [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) belge yazdırma tüm yönlerini denetiminde olmasını bileşeni.</span><span class="sxs-lookup"><span data-stu-id="ffc60-104">It can be used in conjunction with the [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) component to be in control of all aspects of document printing.</span></span>  
  
## <a name="working-with-the-printdocument-component"></a><span data-ttu-id="ffc60-105">PrintDocument bileşeni ile çalışma</span><span class="sxs-lookup"><span data-stu-id="ffc60-105">Working with the PrintDocument Component</span></span>  
 <span data-ttu-id="ffc60-106">İki içeren ana senaryo <xref:System.Drawing.Printing.PrintDocument> bileşen şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ffc60-106">Two of the main scenarios that involve the <xref:System.Drawing.Printing.PrintDocument> component are:</span></span>  
  
-   <span data-ttu-id="ffc60-107">Bir tek tek metin dosyası yazdırma gibi basit yazdırma işlerini.</span><span class="sxs-lookup"><span data-stu-id="ffc60-107">Simple print jobs, such as printing an individual text file.</span></span> <span data-ttu-id="ffc60-108">Böyle bir durumda, eklediğiniz <xref:System.Drawing.Printing.PrintDocument> bir Windows formu bileşene sonra bir dosyada yazdırır programlama mantığı eklemek <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ffc60-108">In such a case you would add the <xref:System.Drawing.Printing.PrintDocument> component to a Windows Form, then add programming logic that prints a file in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler.</span></span> <span data-ttu-id="ffc60-109">Programlama mantığı ile culminate <xref:System.Drawing.Printing.PrintDocument.Print%2A> belgeyi yazdırmayı yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ffc60-109">The programming logic should culminate with the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to print the document.</span></span> <span data-ttu-id="ffc60-110">Bu yöntem gönderir bir <xref:System.Drawing.Graphics> içinde yer alan nesne <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> yazıcıya sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ffc60-110">This method sends a <xref:System.Drawing.Graphics> object, contained in the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class, to the printer.</span></span> <span data-ttu-id="ffc60-111">Bir metin belgesini kullanarak yazdırma gösteren bir örnek <xref:System.Drawing.Printing.PrintDocument> bileşeni Bkz [nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="ffc60-111">For an example that shows how to print a text document using the <xref:System.Drawing.Printing.PrintDocument> component, see [How to: Print a Multi-Page Text File in Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md).</span></span>  
  
-   <span data-ttu-id="ffc60-112">Daha karmaşık yazdırma işlerini yazdırma mantığı yazdığınız yeniden istediğiniz bir durum gibi.</span><span class="sxs-lookup"><span data-stu-id="ffc60-112">More complex print jobs, such as a situation where you will want to reuse printing logic you have written.</span></span> <span data-ttu-id="ffc60-113">Böyle bir durumda yeni bir bileşenden türetin <xref:System.Drawing.Printing.PrintDocument> bileşeni ve geçersiz kılma (bkz [geçersiz kılmaları](~/docs/visual-basic/language-reference/modifiers/overrides.md) Visual Basic veya [geçersiz kılma](~/docs/csharp/language-reference/keywords/override.md) için C#) <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.</span><span class="sxs-lookup"><span data-stu-id="ffc60-113">In such a case you would derive a new component from the <xref:System.Drawing.Printing.PrintDocument> component and override (see [Overrides](~/docs/visual-basic/language-reference/modifiers/overrides.md) for Visual Basic or [override](~/docs/csharp/language-reference/keywords/override.md) for C#) the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
 <span data-ttu-id="ffc60-114">Bir form için eklendiğinde <xref:System.Drawing.Printing.PrintDocument> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.</span><span class="sxs-lookup"><span data-stu-id="ffc60-114">When it is added to a form, the <xref:System.Drawing.Printing.PrintDocument> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffc60-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ffc60-115">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Printing.PrintDocument>  
 [<span data-ttu-id="ffc60-116">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="ffc60-116">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="ffc60-117">PrintDocument Bileşeni</span><span class="sxs-lookup"><span data-stu-id="ffc60-117">PrintDocument Component</span></span>](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)
