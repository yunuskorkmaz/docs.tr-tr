---
title: 'Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: c11affe9c4dd4251ba8ff4b87029d314970b5fcb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404855"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="a59b3-102">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a59b3-102">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="a59b3-103">`#Region`Yönergesi Visual Basic dosyalarındaki kodun bölümlerini daraltmanıza ve gizlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a59b3-103">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="a59b3-104">`#Region`Yönergesi, Visual Studio Code düzenleyicisini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="a59b3-104">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="a59b3-105">Kodu seçici olarak gizleyebilme, dosyalarınızı daha yönetilebilir ve okumayı daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a59b3-105">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="a59b3-106">Daha fazla bilgi için bkz. [anahat oluşturma](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="a59b3-106">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="a59b3-107">`#Region`yönergeleri gibi kod bloğu semantiğini destekler `#If...#End If` .</span><span class="sxs-lookup"><span data-stu-id="a59b3-107">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="a59b3-108">Bu, bir blokta başlayamayacağı ve başka bir blokta bitemeyeceği anlamına gelir; başlangıç ve bitiş aynı blokta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="a59b3-108">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="a59b3-109">`#Region`işlevler içinde yönergeler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="a59b3-109">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="a59b3-110">Kodun bir bölümünü daraltmak ve gizlemek için</span><span class="sxs-lookup"><span data-stu-id="a59b3-110">To collapse and hide a section of code</span></span>

<span data-ttu-id="a59b3-111">`#Region`Aşağıdaki örnekte olduğu gibi, kod bölümünü ve `#End Region` deyimleri arasına yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="a59b3-111">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="a59b3-112">`#Region`Blok, bir kod dosyasında birden çok kez kullanılabilir; Bu nedenle, kullanıcılar, daraltılması için daraltılabilen kendi yordam ve sınıf bloklarını tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="a59b3-112">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="a59b3-113">`#Region`bloklar Ayrıca diğer blokların içinde de yer alabilir `#Region` .</span><span class="sxs-lookup"><span data-stu-id="a59b3-113">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="a59b3-114">Kodu gizleme, derleme yapılmasını engellemez ve `#If...#End If` deyimlerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="a59b3-114">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="a59b3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a59b3-115">See also</span></span>

- [<span data-ttu-id="a59b3-116">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="a59b3-116">Conditional Compilation</span></span>](conditional-compilation.md)
- [<span data-ttu-id="a59b3-117">#Region yönergesi</span><span class="sxs-lookup"><span data-stu-id="a59b3-117">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="a59b3-118">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="a59b3-118">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="a59b3-119">Anahat Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a59b3-119">Outlining</span></span>](/visualstudio/ide/outlining)
