---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: kodun bölümlerini daraltma ve gizleme (Visual Basic)'
title: 'Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, code collapsing
- Visual Basic, code hiding
- Visual Basic code, collapsing and hiding
ms.assetid: b770e8f5-e07d-491a-ab4b-a977980f9ba2
ms.openlocfilehash: b93a2190bd6266c6f9fa5cb06eb249ca174c8067
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475974"
---
# <a name="how-to-collapse-and-hide-sections-of-code-visual-basic"></a><span data-ttu-id="0a8e9-103">Nasıl yapılır: Kodun Bölümlerini Daraltma ve Gizleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a8e9-103">How to: Collapse and Hide Sections of Code (Visual Basic)</span></span>

<span data-ttu-id="0a8e9-104">`#Region`Yönergesi Visual Basic dosyalarındaki kodun bölümlerini daraltmanıza ve gizlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-104">The `#Region` directive enables you to collapse and hide sections of code in Visual Basic files.</span></span> <span data-ttu-id="0a8e9-105">`#Region`Yönergesi, Visual Studio Code düzenleyicisini kullanırken genişletebileceğiniz veya daraltabileceğiniz bir kod bloğu belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-105">The `#Region` directive lets you specify a block of code that you can expand or collapse when using the Visual Studio code editor.</span></span> <span data-ttu-id="0a8e9-106">Kodu seçici olarak gizleyebilme, dosyalarınızı daha yönetilebilir ve okumayı daha kolay hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-106">The ability to hide code selectively makes your files more manageable and easier to read.</span></span> <span data-ttu-id="0a8e9-107">Daha fazla bilgi için bkz. [anahat oluşturma](/visualstudio/ide/outlining).</span><span class="sxs-lookup"><span data-stu-id="0a8e9-107">For more information, see [Outlining](/visualstudio/ide/outlining).</span></span>

<span data-ttu-id="0a8e9-108">`#Region` yönergeleri gibi kod bloğu semantiğini destekler `#If...#End If` .</span><span class="sxs-lookup"><span data-stu-id="0a8e9-108">`#Region` directives support code block semantics such as `#If...#End If`.</span></span> <span data-ttu-id="0a8e9-109">Bu, bir blokta başlayamayacağı ve başka bir blokta bitemeyeceği anlamına gelir; başlangıç ve bitiş aynı blokta olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-109">This means they cannot begin in one block and end in another; the start and end must be in the same block.</span></span> <span data-ttu-id="0a8e9-110">`#Region` işlevler içinde yönergeler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-110">`#Region` directives are not supported within functions.</span></span>

## <a name="to-collapse-and-hide-a-section-of-code"></a><span data-ttu-id="0a8e9-111">Kodun bir bölümünü daraltmak ve gizlemek için</span><span class="sxs-lookup"><span data-stu-id="0a8e9-111">To collapse and hide a section of code</span></span>

<span data-ttu-id="0a8e9-112">`#Region`Aşağıdaki örnekte olduğu gibi, kod bölümünü ve `#End Region` deyimleri arasına yerleştirin:</span><span class="sxs-lookup"><span data-stu-id="0a8e9-112">Place the section of code between the `#Region` and `#End Region` statements, as in the following example:</span></span>

[!code-vb[VbVbalrConditionalComp#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConditionalComp/VB/Class1.vb#6)]

<span data-ttu-id="0a8e9-113">`#Region`Blok, bir kod dosyasında birden çok kez kullanılabilir; Bu nedenle, kullanıcılar, daraltılması için daraltılabilen kendi yordam ve sınıf bloklarını tanımlayabilir.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-113">The `#Region` block can be used multiple times in a code file; thus, users can define their own blocks of procedures and classes that can, in turn, be collapsed.</span></span> <span data-ttu-id="0a8e9-114">`#Region` bloklar Ayrıca diğer blokların içinde de yer alabilir `#Region` .</span><span class="sxs-lookup"><span data-stu-id="0a8e9-114">`#Region` blocks can also be nested within other `#Region` blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="0a8e9-115">Kodu gizleme, derleme yapılmasını engellemez ve `#If...#End If` deyimlerini etkilemez.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-115">Hiding code does not prevent it from being compiled and does not affect `#If...#End If` statements.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a8e9-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0a8e9-116">See also</span></span>

- [<span data-ttu-id="0a8e9-117">Koşullu Derleme</span><span class="sxs-lookup"><span data-stu-id="0a8e9-117">Conditional Compilation</span></span>](conditional-compilation.md)
- [<span data-ttu-id="0a8e9-118">#Region yönergesi</span><span class="sxs-lookup"><span data-stu-id="0a8e9-118">#Region Directive</span></span>](../../language-reference/directives/region-directive.md)
- [<span data-ttu-id="0a8e9-119">#If... Sonra... #Else yönergeler</span><span class="sxs-lookup"><span data-stu-id="0a8e9-119">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="0a8e9-120">Anahat Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0a8e9-120">Outlining</span></span>](/visualstudio/ide/outlining)
