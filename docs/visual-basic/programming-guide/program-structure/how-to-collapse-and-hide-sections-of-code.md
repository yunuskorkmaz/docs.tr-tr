---
title: 'Nasıl yapılır: Kodun bölümlerini daraltma ve gizleme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: 4f11982cc0aa7654c1e456fb15d918a68bc4791b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054114"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="98991-102">Nasıl yapılır: Kodun bölümlerini daraltma ve gizleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="98991-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="98991-103">`#Region` Yönergesi Visual Basic dosyalarındaki kodun bölümlerini daraltmanıza ve gizlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="98991-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="98991-104">`#Region` Yönergesi, Visual Studio Code düzenleyicisini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="98991-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="98991-105">Kodu seçici olarak gizleyebilme, dosyalarınızı daha yönetilebilir ve okumayı daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="98991-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="98991-106">Daha fazla bilgi için bkz. [anahat oluşturma](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="98991-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="98991-107">`#Region`yönergeleri gibi `#If...#End If`kod bloğu semantiğini destekler.</span><span class="sxs-lookup"><span data-stu-id="98991-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="98991-108">Bu, bir blokta başlayamayacağı ve başka bir blokta bitemeyeceği anlamına gelir; başlangıç ve bitiş aynı blokta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98991-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="98991-109">`#Region`işlevler içinde yönergeler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="98991-109">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="98991-110">Kodun bir bölümünü daraltmak ve gizlemek için</span><span class="sxs-lookup"><span data-stu-id="98991-110">To collapse and hide a section of code</span></span>

<span data-ttu-id="98991-111">Aşağıdaki örnekte olduğu gibi, kod bölümünü `#Region` ve `#End Region` deyimleri arasına yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="98991-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="98991-112">`#Region` Blok, bir kod dosyasında birden çok kez kullanılabilir; Bu nedenle, kullanıcılar, daraltılması için daraltılabilen kendi yordam ve sınıf bloklarını tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="98991-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="98991-113">`#Region`bloklar Ayrıca diğer `#Region` blokların içinde de yer alabilir.</span><span class="sxs-lookup"><span data-stu-id="98991-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="98991-114">Kodu gizleme, derleme yapılmasını engellemez ve deyimlerini etkilemez `#If...#End If` .</span><span class="sxs-lookup"><span data-stu-id="98991-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="98991-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98991-115">See also</span></span>

- [<span data-ttu-id="98991-116">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="98991-116">Conditional Compilation</span></span>](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
- [<span data-ttu-id="98991-117">#Region Yönergesi</span><span class="sxs-lookup"><span data-stu-id="98991-117">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
- [<span data-ttu-id="98991-118">#If...Then...#Else Yönergesi</span><span class="sxs-lookup"><span data-stu-id="98991-118">#If...Then...#Else Directives</span></span>](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="98991-119">Anahat Oluşturma</span><span class="sxs-lookup"><span data-stu-id="98991-119">Outlining</span></span>](/visualstudio/ide/outlining)
