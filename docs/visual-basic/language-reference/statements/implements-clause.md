---
title: Implements Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: dcd20f21a989c327dcfcf27d5638d500b6e4b6da
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929312"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="2d649-102">Implements Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2d649-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="2d649-103">Bir sınıf veya yapı üyesinin, arabirim içinde tanımlanmış bir üye için uygulama sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2d649-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d649-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d649-104">Remarks</span></span>  
<span data-ttu-id="2d649-105">Anahtar sözcüğü, [Implements ifadesiyle](../../../visual-basic/language-reference/statements/implements-statement.md)aynı değildir. `Implements`</span><span class="sxs-lookup"><span data-stu-id="2d649-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="2d649-106">Bir sınıf ya `Implements` da yapının bir veya daha fazla arabirim uyguladığını belirtmek için ifadesini kullanın ve ardından her üye için hangi arabirimin ve hangi `Implements` üyenin uyguladığı, anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2d649-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="2d649-107">Bir sınıf veya yapı bir arabirim uygularsa, [sınıf deyimden](../../../visual-basic/language-reference/statements/class-statement.md) veya `Implements` [Yapı deyimden](../../../visual-basic/language-reference/statements/structure-statement.md)hemen sonra ifadesini içermesi gerekir ve arabirim tarafından tanımlanan tüm üyeleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2d649-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="2d649-108">Yeniden uygulama</span><span class="sxs-lookup"><span data-stu-id="2d649-108">Reimplementation</span></span>  
<span data-ttu-id="2d649-109">Türetilmiş bir sınıfta, temel sınıfın zaten uygulanmış olduğu bir arabirim üyesini yeniden uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d649-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="2d649-110">Bu, aşağıdaki gibi temel sınıf üyesini geçersiz kılmadan farklıdır:</span><span class="sxs-lookup"><span data-stu-id="2d649-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="2d649-111">Temel sınıf üyesinin yeniden uygulanması için [geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md) olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2d649-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="2d649-112">Üyeyi farklı bir adla yeniden uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2d649-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="2d649-113">`Implements` Anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2d649-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="2d649-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d649-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="2d649-115">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d649-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="2d649-116">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d649-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="2d649-117">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d649-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2d649-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2d649-118">See also</span></span>

- [<span data-ttu-id="2d649-119">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d649-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="2d649-120">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d649-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="2d649-121">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d649-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="2d649-122">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="2d649-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
