---
title: Birimi <keyword>
ms.date: 07/20/2015
f1_keywords:
- vb.ModuleAttribute
helpviewer_keywords:
- Module keyword [Visual Basic]
- Module modifier
- attribute blocks, Module keyword
ms.assetid: d971b940-05ab-4d56-8485-e3b8a661906b
ms.openlocfilehash: 6c4f24ad161302835be683e9d324ce32b16c4087
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867981"
---
# <a name="module-keyword-visual-basic"></a><span data-ttu-id="88320-102">\<keyword> Modülü (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="88320-102">Module \<keyword> (Visual Basic)</span></span>

<span data-ttu-id="88320-103">Kaynak dosyanın başındaki bir özniteliğin geçerli derleme modülüne uygulanacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="88320-103">Specifies that an attribute at the beginning of a source file applies to the current assembly module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88320-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88320-104">Remarks</span></span>  

 <span data-ttu-id="88320-105">Birçok öznitelik, sınıf veya özellik gibi tek bir programlama öğesiyle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="88320-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="88320-106">Bu tür bir özniteliği, köşeli ayraç () içinde öznitelik bloğunu `< >` doğrudan bildirim bildirimine ekleyerek uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="88320-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="88320-107">Bir öznitelik yalnızca aşağıdaki öğeye, ancak geçerli derleme modülüne ait değilse, öznitelik bloğunu kaynak dosyanın başlangıcına yerleştirmiş ve özniteliği `Module` anahtar sözcüğüyle belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="88320-107">If an attribute pertains not only to the following element but to the current assembly module, you place the attribute block at the beginning of the source file and identify the attribute with the `Module` keyword.</span></span> <span data-ttu-id="88320-108">Tüm derleme için geçerliyse, [Assembly](assembly.md) anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="88320-108">If it applies to the entire assembly, you use the [Assembly](assembly.md) keyword.</span></span>  
  
 <span data-ttu-id="88320-109">`Module`Değiştirici [module ifadesiyle](../statements/module-statement.md)aynı değil.</span><span class="sxs-lookup"><span data-stu-id="88320-109">The `Module` modifier is not the same as the [Module Statement](../statements/module-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88320-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88320-110">See also</span></span>

- [<span data-ttu-id="88320-111">Bütünleştirilmiş Kod</span><span class="sxs-lookup"><span data-stu-id="88320-111">Assembly</span></span>](assembly.md)
- [<span data-ttu-id="88320-112">Module Deyimi</span><span class="sxs-lookup"><span data-stu-id="88320-112">Module Statement</span></span>](../statements/module-statement.md)
- [<span data-ttu-id="88320-113">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="88320-113">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
