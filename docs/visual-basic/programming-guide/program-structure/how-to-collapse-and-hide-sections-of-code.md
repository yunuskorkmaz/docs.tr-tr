---
title: "Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56a31f0c8af9b84e87ebe1e5191d72d19be8340f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="fc046-102">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc046-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="fc046-103">`#Region` Yönergesi daraltma ve kod bölümlerini gizleme olanak tanır [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] dosyaları.</span><span class="sxs-lookup"><span data-stu-id="fc046-103">The `#Region` directive enables you to collapse and hide sections of code in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] files.</span></span> <span data-ttu-id="fc046-104">`#Region` Yönergesi belirlemenizi sağlar, genişletebilirsiniz kodu veya daralt bloğunu kullanırken [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] Kod Düzenleyicisi.</span><span class="sxs-lookup"><span data-stu-id="fc046-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] code editor.</span></span> <span data-ttu-id="fc046-105">Seçime bağlı olarak kod gizleme olanağı dosyalarınızı daha yönetilebilir ve okuması daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="fc046-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="fc046-106">Daha fazla bilgi için bkz: [anahat](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="fc046-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="fc046-107">`#Region`yönergeleri kod bloğu semantiği gibi destek `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="fc046-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="fc046-108">Bu, tek bir blok olarak başlar ve başka bir programda bitiş anlamına gelir; Başlangıç ve bitiş aynı bloğunda olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc046-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="fc046-109">`#Region`yönergeleri içinde işlevleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="fc046-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="fc046-110">Daraltma ve kod bir bölümünü gizlemek için</span><span class="sxs-lookup"><span data-stu-id="fc046-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="fc046-111">Kod arasında bölümünü yerleştirin `#Region` ve `#End Region` aşağıdaki örnekteki gibi deyimleri:</span><span class="sxs-lookup"><span data-stu-id="fc046-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/how-to-collapse-and-hide-sections-of-code_1.vb)]  
  
     <span data-ttu-id="fc046-112">`#Region` Blok kullanılan kod dosyasında birden çok kez; bu nedenle, kullanıcılar kendi bloklarını yordamları ve sırasıyla daraltılabilen sınıflar tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="fc046-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="fc046-113">`#Region`blokları de iç içe geçirilemez diğer içinde `#Region` engeller.</span><span class="sxs-lookup"><span data-stu-id="fc046-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc046-114">Kod gizleme derlenmiş gelen engellemez ve etkilemez `#If...#End If` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="fc046-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc046-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fc046-115">See Also</span></span>  
 [<span data-ttu-id="fc046-116">Koşullu derleme</span><span class="sxs-lookup"><span data-stu-id="fc046-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [<span data-ttu-id="fc046-117">#Region yönergesi</span><span class="sxs-lookup"><span data-stu-id="fc046-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)  
 [<span data-ttu-id="fc046-118">#If... Then... #Else yönergeleri</span><span class="sxs-lookup"><span data-stu-id="fc046-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [<span data-ttu-id="fc046-119">Anahat oluşturma</span><span class="sxs-lookup"><span data-stu-id="fc046-119">Outlining</span></span>](/visualstudio/ide/outlining)
