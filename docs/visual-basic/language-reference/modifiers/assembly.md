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
ms.openlocfilehash: 7ee6cddefd5955ee76510ffeb23335f05460657b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595296"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="5ee8a-102">Derleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5ee8a-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="5ee8a-103">Bir kaynak dosyasının başında bir öznitelik tüm derlemeye uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5ee8a-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5ee8a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ee8a-104">Remarks</span></span>  
 <span data-ttu-id="5ee8a-105">Çok sayıda özniteliği bir sınıf veya özellik gibi tek bir programlama öğe ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="5ee8a-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="5ee8a-106">Köşeli parantez içinde öznitelik blok ekleyerek bu tür bir öznitelik geçerli (`< >`), bildirim deyiminin için doğrudan.</span><span class="sxs-lookup"><span data-stu-id="5ee8a-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="5ee8a-107">Bir öznitelik değil yalnızca aşağıdaki öğesine, ancak tüm derleme ilgiliyse, öznitelik blok kaynak dosyasının başında yerleştirin ve öznitelik tanımlamak `Assembly` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5ee8a-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="5ee8a-108">Geçerli derleme modülü geçerliyse, kullandığınız [Modülü](../../../visual-basic/language-reference/modifiers/module-keyword.md) anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="5ee8a-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="5ee8a-109">Bir öznitelik AssemblyInfo.vb dosyasındaki bir derlemenin, bu durumda, bir öznitelik blok ana kaynak kodu dosyanızda kullanmak zorunda değil de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ee8a-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee8a-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5ee8a-110">See Also</span></span>  
 [<span data-ttu-id="5ee8a-111">Modül \<anahtar sözcüğü ></span><span class="sxs-lookup"><span data-stu-id="5ee8a-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="5ee8a-112">Öznitelikler genel bakış</span><span class="sxs-lookup"><span data-stu-id="5ee8a-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

