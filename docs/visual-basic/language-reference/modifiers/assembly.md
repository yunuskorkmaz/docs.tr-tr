---
title: Derleme (Visual Basic)
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
ms.openlocfilehash: 819fa9cf1bd25e9426fb1e75925a269fcf7a71cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802001"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="27133-102">Derleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27133-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="27133-103">Bir kaynak dosyasının başında bir öznitelik tüm derleme için geçerli olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="27133-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27133-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="27133-104">Remarks</span></span>  
 <span data-ttu-id="27133-105">Tek programlama öğesine, bir sınıf ya da özellik gibi birçok öznitelikleri ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="27133-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="27133-106">Açılı ayraçlar içinde öznitelik bloğuna ekleyerek bu tür bir öznitelik uygulamak (`< >`), doğrudan bildirim deyiminin için.</span><span class="sxs-lookup"><span data-stu-id="27133-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="27133-107">Bir öznitelik yalnızca şu öğe ancak tüm derleme ilgiliyse, öznitelik bloğuna kaynak dosyasının başında yerleştirin ve özniteliğiyle tanımlamak `Assembly` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="27133-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="27133-108">Geçerli derleme modülü için geçerliyse, kullandığınız [Modülü](../../../visual-basic/language-reference/modifiers/module-keyword.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="27133-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="27133-109">Öznitelik bir derlemeye AssemblyInfo.vb dosyasında, bu durumda öznitelik bloğuna ana kaynak kodu dosyanızda kullanın gerekmez de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="27133-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27133-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27133-110">See also</span></span>

- [<span data-ttu-id="27133-111">Modül \<anahtar sözcüğü ></span><span class="sxs-lookup"><span data-stu-id="27133-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)
- [<span data-ttu-id="27133-112">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="27133-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
