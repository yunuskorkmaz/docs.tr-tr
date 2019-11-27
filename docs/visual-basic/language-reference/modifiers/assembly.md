---
title: Derleme
ms.date: 07/20/2015
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
ms.openlocfilehash: 1385919a1205a60104125fff1bdd24f409a091df
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351643"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="fa647-102">Derleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa647-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="fa647-103">Kaynak dosyanın başındaki bir özniteliğin tüm derleme için geçerli olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fa647-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa647-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa647-104">Remarks</span></span>  
 <span data-ttu-id="fa647-105">Birçok öznitelik, sınıf veya özellik gibi tek bir programlama öğesiyle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="fa647-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="fa647-106">Bu tür bir özniteliği, bir öznitelik bloğunu, açılı ayraç (`< >`) içinde doğrudan bildirim bildirimine ekleyerek uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="fa647-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="fa647-107">Bir öznitelik yalnızca aşağıdaki öğeye, ancak tüm derlemeye ait değilse, öznitelik bloğunu kaynak dosyanın başlangıcına yerleştirmiş ve özniteliği `Assembly` anahtar sözcüğüyle belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="fa647-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="fa647-108">Geçerli derleme modülü için geçerliyse [Modül](../../../visual-basic/language-reference/modifiers/module-keyword.md) anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="fa647-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="fa647-109">Ayrıca, AssemblyInfo. vb dosyasındaki bir derlemeye bir özniteliği uygulayabilirsiniz, bu durumda ana kaynak kodu dosyanızda bir öznitelik bloğunu kullanmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="fa647-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa647-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa647-110">See also</span></span>

- [<span data-ttu-id="fa647-111">Modül \<anahtar sözcüğü ></span><span class="sxs-lookup"><span data-stu-id="fa647-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="fa647-112">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="fa647-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
