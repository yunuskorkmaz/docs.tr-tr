---
title: Bütünleştirilmiş Kod
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
ms.openlocfilehash: 7d313dee1015362bd0215ed98ab7e898312cfbcd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373166"
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="b0d38-102">Derleme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0d38-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="b0d38-103">Kaynak dosyanın başındaki bir özniteliğin tüm derleme için geçerli olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b0d38-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0d38-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0d38-104">Remarks</span></span>  
 <span data-ttu-id="b0d38-105">Birçok öznitelik, sınıf veya özellik gibi tek bir programlama öğesiyle ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="b0d38-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="b0d38-106">Bu tür bir özniteliği, köşeli ayraç () içinde öznitelik bloğunu `< >` doğrudan bildirim bildirimine ekleyerek uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="b0d38-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="b0d38-107">Bir öznitelik yalnızca aşağıdaki öğeye, ancak tüm derlemeye ait değilse, öznitelik bloğunu kaynak dosyanın başlangıcına yerleştirmiş ve özniteliği `Assembly` anahtar sözcüğüyle belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="b0d38-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="b0d38-108">Geçerli derleme modülü için geçerliyse [Modül](module-keyword.md) anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b0d38-108">If it applies to the current assembly module, you use the [Module](module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="b0d38-109">Ayrıca, AssemblyInfo. vb dosyasındaki bir derlemeye bir özniteliği uygulayabilirsiniz, bu durumda ana kaynak kodu dosyanızda bir öznitelik bloğunu kullanmak zorunda değilsiniz.</span><span class="sxs-lookup"><span data-stu-id="b0d38-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0d38-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0d38-110">See also</span></span>

- [<span data-ttu-id="b0d38-111">Birimi\<keyword></span><span class="sxs-lookup"><span data-stu-id="b0d38-111">Module \<keyword></span></span>](module-keyword.md)
- [<span data-ttu-id="b0d38-112">Özniteliklere genel bakış</span><span class="sxs-lookup"><span data-stu-id="b0d38-112">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
