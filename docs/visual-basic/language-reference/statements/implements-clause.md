---
title: Implements Yan Tümcesi
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
ms.openlocfilehash: f114aee75356e59eafd9d3ba6af9c64402cb374f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345867"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="2ec93-102">Implements Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2ec93-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="2ec93-103">Bir sınıf veya yapı üyesinin, arabirim içinde tanımlanmış bir üye için uygulama sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2ec93-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ec93-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2ec93-104">Remarks</span></span>  
<span data-ttu-id="2ec93-105">`Implements` anahtar sözcüğü, [Implements ifadesiyle](../../../visual-basic/language-reference/statements/implements-statement.md)aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="2ec93-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="2ec93-106">Bir sınıf veya yapının bir veya daha fazla arabirim uyguladığını belirtmek için `Implements` ifadesini kullanın ve ardından her üye için, hangi arabirimin ve hangi üyenin uyguladığı için `Implements` anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="2ec93-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="2ec93-107">Bir sınıf veya yapı bir arabirim uygularsa, [sınıf](../../../visual-basic/language-reference/statements/class-statement.md) veya [Yapı deyimden](../../../visual-basic/language-reference/statements/structure-statement.md)hemen sonra `Implements` ifadesini içermesi gerekir ve arabirim tarafından tanımlanan tüm üyeleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="2ec93-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="2ec93-108">Yeniden uygulama</span><span class="sxs-lookup"><span data-stu-id="2ec93-108">Reimplementation</span></span>  
<span data-ttu-id="2ec93-109">Türetilmiş bir sınıfta, temel sınıfın zaten uygulanmış olduğu bir arabirim üyesini yeniden uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ec93-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="2ec93-110">Bu, aşağıdaki gibi temel sınıf üyesini geçersiz kılmadan farklıdır:</span><span class="sxs-lookup"><span data-stu-id="2ec93-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="2ec93-111">Temel sınıf üyesinin yeniden uygulanması için [geçersiz kılınabilir](../../../visual-basic/language-reference/modifiers/overridable.md) olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="2ec93-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="2ec93-112">Üyeyi farklı bir adla yeniden uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ec93-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="2ec93-113">`Implements` anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2ec93-113">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="2ec93-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="2ec93-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="2ec93-115">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2ec93-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="2ec93-116">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="2ec93-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="2ec93-117">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2ec93-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ec93-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2ec93-118">See also</span></span>

- [<span data-ttu-id="2ec93-119">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="2ec93-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="2ec93-120">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="2ec93-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="2ec93-121">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="2ec93-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="2ec93-122">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="2ec93-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
