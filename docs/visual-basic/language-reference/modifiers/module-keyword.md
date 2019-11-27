---
title: Modül <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: cd2f762181b5a702f0b0defd5b71bb7bdf129c7b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351547"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="56597-102">Modül \<anahtar sözcüğü > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="56597-102">Module \<keyword> (Visual Basic)</span></span>
<span data-ttu-id="56597-103">Kaynak dosyanın başındaki bir özniteliğin geçerli derleme modülüne uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="56597-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56597-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56597-104">Remarks</span></span>  
 <span data-ttu-id="56597-105">Birçok öznitelik, sınıf veya özellik gibi tek bir programlama öğesiyle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="56597-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="56597-106">Bu tür bir özniteliği, bir öznitelik bloğunu, açılı ayraç (`< >`) içinde doğrudan bildirim bildirimine ekleyerek uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="56597-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="56597-107">Bir öznitelik yalnızca aşağıdaki öğeye, ancak geçerli derleme modülüne ait değilse, öznitelik bloğunu kaynak dosyanın başlangıcına yerleştirir ve özniteliği `Module` anahtar sözcüğüyle belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="56597-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="56597-108">Tüm derleme için geçerliyse, [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="56597-108">If it applies to the entire assembly, you use the [Assembly](../../../visual-basic/language-reference/modifiers/assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="56597-109">`Module` değiştiricisi [module bildirimiyle](../../../visual-basic/language-reference/statements/module-statement.md)aynı değil.</span><span class="sxs-lookup"><span data-stu-id="56597-109">The `Module` modifier is not the same as the [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56597-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="56597-110">See also</span></span>

- [<span data-ttu-id="56597-111">Derleme</span><span class="sxs-lookup"><span data-stu-id="56597-111">Assembly</span></span>](../../../visual-basic/language-reference/modifiers/assembly.md)
- [<span data-ttu-id="56597-112">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="56597-112">Module Statement</span></span>](../../../visual-basic/language-reference/statements/module-statement.md)
- [<span data-ttu-id="56597-113">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="56597-113">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
