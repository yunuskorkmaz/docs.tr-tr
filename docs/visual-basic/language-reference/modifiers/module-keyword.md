---
description: 'Daha fazla bilgi edinin: modül <keyword> (Visual Basic)'
title: Birimi <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 1bd25b00b41f5da4fca535220fe4e1694c81baca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640699"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="21a60-103">\<keyword> Modülü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21a60-103">Module \<keyword> (Visual Basic)</span></span>

<span data-ttu-id="21a60-104">Kaynak dosyanın başındaki bir özniteliğin geçerli derleme modülüne uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="21a60-104">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21a60-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21a60-105">Remarks</span></span>  

 <span data-ttu-id="21a60-106">Birçok öznitelik, sınıf veya özellik gibi tek bir programlama öğesiyle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="21a60-106">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="21a60-107">Bu tür bir özniteliği, köşeli ayraç () içinde öznitelik bloğunu `< >` doğrudan bildirim bildirimine ekleyerek uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="21a60-107">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="21a60-108">Bir öznitelik yalnızca aşağıdaki öğeye, ancak geçerli derleme modülüne ait değilse, öznitelik bloğunu kaynak dosyanın başlangıcına yerleştirmiş ve özniteliği `Module` anahtar sözcüğüyle belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="21a60-108">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="21a60-109">Tüm derleme için geçerliyse, [Assembly](assembly.md) anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="21a60-109">If it applies to the entire assembly, you use the [Assembly](assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="21a60-110">`Module`Değiştirici [module ifadesiyle](../statements/module-statement.md)aynı değil.</span><span class="sxs-lookup"><span data-stu-id="21a60-110">The `Module` modifier is not the same as the [Module Statement](../statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21a60-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="21a60-111">See also</span></span>

- [<span data-ttu-id="21a60-112">Bütünleştirilmiş Kod</span><span class="sxs-lookup"><span data-stu-id="21a60-112">Assembly</span></span>](assembly.md)
- [<span data-ttu-id="21a60-113">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="21a60-113">Module Statement</span></span>](../statements/module-statement.md)
- [<span data-ttu-id="21a60-114">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="21a60-114">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
