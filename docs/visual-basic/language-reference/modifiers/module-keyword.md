---
title: Modül &lt;anahtar sözcüğü&gt; (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 3b4b09469a3f22b5e5c7faa98d5db7b3522ed236
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586481"
---
# <a name="module-ltkeywordgt-visual-basic"></a><span data-ttu-id="b314b-102">Modül &lt;anahtar sözcüğü&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b314b-102">Module &lt;keyword&gt; (Visual Basic)</span></span>
<span data-ttu-id="b314b-103">Bir kaynak dosyasının başında bir öznitelik için geçerli derleme modülü geçerli olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b314b-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b314b-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b314b-104">Remarks</span></span>  
 <span data-ttu-id="b314b-105">Tek programlama öğesine, bir sınıf ya da özellik gibi birçok öznitelikleri ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="b314b-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="b314b-106">Açılı ayraçlar içinde öznitelik bloğuna ekleyerek bu tür bir öznitelik uygulamak (`< >`), doğrudan bildirim deyiminin için.</span><span class="sxs-lookup"><span data-stu-id="b314b-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="b314b-107">Bir öznitelik yalnızca şu öğe ancak geçerli derleme modülü ilgiliyse, öznitelik bloğuna kaynak dosyasının başında yerleştirin ve özniteliğiyle tanımlamak `Module` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b314b-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="b314b-108">Tüm derleme için geçerliyse, kullandığınız [derleme](../../../visual-basic/language-reference/modifiers/assembly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="b314b-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="b314b-109">`Module` Değiştiricisi ile aynı değil [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b314b-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b314b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b314b-110">See also</span></span>
- [<span data-ttu-id="b314b-111">Assembly</span><span class="sxs-lookup"><span data-stu-id="b314b-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="b314b-112">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="b314b-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="b314b-113">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="b314b-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

