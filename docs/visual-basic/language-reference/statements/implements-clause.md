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
ms.openlocfilehash: cb0ea5ce52effad4df541e6a9196b1faf279262e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522521"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="2acc0-102">Implements Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2acc0-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="2acc0-103">Bir sınıf veya yapı üyesine bir arabirim içinde tanımlanmış bir üye için uygulama sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2acc0-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2acc0-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2acc0-104">Remarks</span></span>  
<span data-ttu-id="2acc0-105">`Implements` Anahtar sözcüğü ile aynı değil [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2acc0-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="2acc0-106">Kullandığınız `Implements` bir sınıf veya yapı, bir veya daha fazla arabirimlerini uygular ve sonra her üyesi için kullanırsınız belirtmek için deyimini `Implements` hangi arabirimi ve hangi belirtmek için anahtar sözcüğü uygular.</span><span class="sxs-lookup"><span data-stu-id="2acc0-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="2acc0-107">Bir sınıf veya yapı bir arabirim uygularsa, içermelidir `Implements` deyimi hemen sonra [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md) veya [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md), ve tüm üyelerini uygulamalıdır arabirim tarafından tanımlanan.</span><span class="sxs-lookup"><span data-stu-id="2acc0-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="2acc0-108">Reimplementation</span><span class="sxs-lookup"><span data-stu-id="2acc0-108">Reimplementation</span></span>  
<span data-ttu-id="2acc0-109">Türetilen bir sınıfta temel sınıf zaten uygulamıştır bir arabirim üyesi yeniden uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2acc0-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="2acc0-110">Bu aşağıdaki bakımdan bir temel sınıf üyesinin geçersiz kılan kaynaklardan farklı.</span><span class="sxs-lookup"><span data-stu-id="2acc0-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="2acc0-111">Temel sınıf üyesi olması gerekmez. [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) reimplemented için.</span><span class="sxs-lookup"><span data-stu-id="2acc0-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="2acc0-112">Üyesi farklı bir adla yeniden uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2acc0-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="2acc0-113">`Implements` Anahtar sözcüğü aşağıdaki bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="2acc0-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="2acc0-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="2acc0-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="2acc0-115">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="2acc0-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="2acc0-116">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="2acc0-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="2acc0-117">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="2acc0-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="2acc0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2acc0-118">See also</span></span>
- [<span data-ttu-id="2acc0-119">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="2acc0-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
- [<span data-ttu-id="2acc0-120">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="2acc0-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)
- [<span data-ttu-id="2acc0-121">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="2acc0-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)
- [<span data-ttu-id="2acc0-122">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="2acc0-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
