---
title: 'Nasıl yapılır: Daraltma ve gizleme (Visual Basic) kod bölümlerini'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: bbce0e4a2427843ed9d9d51b25684db8c54ba69a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980132"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="353d5-102">Nasıl yapılır: Daraltma ve gizleme (Visual Basic) kod bölümlerini</span><span class="sxs-lookup"><span data-stu-id="353d5-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>
<span data-ttu-id="353d5-103">`#Region` Yönergesi daraltma ve gizleme Visual Basic dosyalarında kod bölümlerini olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="353d5-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="353d5-104">`#Region` Yönergesi Visual Studio Kod Düzenleyicisi'ni kullanırken genişletebileceğiniz kodu veya daralt bloğunu belirtmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="353d5-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="353d5-105">Kod seçmeli olarak gizleyebilme yeteneği dosyalarınızı daha yönetilebilir ve okunması kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="353d5-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="353d5-106">Daha fazla bilgi için [anahat](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="353d5-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>  
  
 <span data-ttu-id="353d5-107">`#Region` kod bloğu semantiği gibi destek yönergeleri `#If...#End If`.</span><span class="sxs-lookup"><span data-stu-id="353d5-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="353d5-108">Bu, bir blok içinde başlar ve diğerinde anlamına gelir; Başlangıç ve bitiş aynı blok içinde olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="353d5-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="353d5-109">`#Region` yönergeleri içindeki işlevleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="353d5-109">`#Region` directives are not supported within functions.</span></span>  
  
### <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="353d5-110">Daralt ve kodun bir bölümünü gizlemek için</span><span class="sxs-lookup"><span data-stu-id="353d5-110">To collapse and hide a section of code</span></span>  
  
-   <span data-ttu-id="353d5-111">Arasında kod bölümünün yerleştirin `#Region` ve `#End Region` ifadeleri, aşağıdaki örnekte olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="353d5-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>  
  
     [!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]  
  
     <span data-ttu-id="353d5-112">`#Region` Blok kullanılan bir kod dosyasında birden çok kez; bu nedenle, kullanıcılar kendi blokları yordamlar ve sırasıyla daratılmadan sınıfları tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="353d5-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="353d5-113">`#Region` Bloklar da iç içe geçirilemez birbirine `#Region` engeller.</span><span class="sxs-lookup"><span data-stu-id="353d5-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="353d5-114">Kod gizleme Eylemi'ni engellemez ve etkilemez `#If...#End If` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="353d5-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="353d5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="353d5-115">See also</span></span>
- [<span data-ttu-id="353d5-116">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="353d5-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="353d5-117">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="353d5-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="353d5-118">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="353d5-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="353d5-119">Anahat Oluşturma</span><span class="sxs-lookup"><span data-stu-id="353d5-119">Outlining</span></span>](/visualstudio/ide/outlining)
