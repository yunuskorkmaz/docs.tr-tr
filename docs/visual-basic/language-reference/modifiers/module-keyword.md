---
title: <keyword> Modülü (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: f6ded1184aedf1702f4b6e5eebb85709cf8e39f4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814282"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="94086-102">Modül \<anahtar sözcüğü > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94086-102">Module \<keyword> (Visual Basic)</span></span>
<span data-ttu-id="94086-103">Bir kaynak dosyasının başında bir öznitelik için geçerli derleme modülü geçerli olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="94086-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94086-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="94086-104">Remarks</span></span>  
 <span data-ttu-id="94086-105">Tek programlama öğesine, bir sınıf ya da özellik gibi birçok öznitelikleri ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="94086-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="94086-106">Açılı ayraçlar içinde öznitelik bloğuna ekleyerek bu tür bir öznitelik uygulamak (`< >`), doğrudan bildirim deyiminin için.</span><span class="sxs-lookup"><span data-stu-id="94086-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="94086-107">Bir öznitelik yalnızca şu öğe ancak geçerli derleme modülü ilgiliyse, öznitelik bloğuna kaynak dosyasının başında yerleştirin ve özniteliğiyle tanımlamak `Module` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="94086-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="94086-108">Tüm derleme için geçerliyse, kullandığınız [derleme](../../../visual-basic/language-reference/modifiers/assembly.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="94086-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="94086-109">`Module` Değiştiricisi ile aynı değil [Module deyimi](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="94086-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94086-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94086-110">See also</span></span>

- [<span data-ttu-id="94086-111">Assembly</span><span class="sxs-lookup"><span data-stu-id="94086-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="94086-112">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="94086-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="94086-113">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="94086-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
