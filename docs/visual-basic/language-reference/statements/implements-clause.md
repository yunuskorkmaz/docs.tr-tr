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
ms.openlocfilehash: 1e34245ac528e9e2463afbfd07dff91bf693830b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603411"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="9545b-102">Implements Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9545b-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="9545b-103">Sınıf veya yapı üyesi bir arabiriminde tanımlanan üye uygulamasını sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9545b-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9545b-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9545b-104">Remarks</span></span>  
<span data-ttu-id="9545b-105">`Implements` Anahtar sözcüğü ile aynı değil [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="9545b-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="9545b-106">Kullandığınız `Implements` bir sınıf veya yapı bir veya daha fazla arabirimlerini uygular ve ardından her üye için kullandığınız belirtmek için deyimi `Implements` hangi arabirimi ve hangi üye belirtmek için anahtar sözcüğü, uygular.</span><span class="sxs-lookup"><span data-stu-id="9545b-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="9545b-107">Bir sınıf veya yapı arabirim uygularsa, içermelidir `Implements` deyimi hemen sonra [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md) veya [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md), ve tüm üyelerin uygulamalıdır arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="9545b-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="9545b-108">Yeniden uygulama</span><span class="sxs-lookup"><span data-stu-id="9545b-108">Reimplementation</span></span>  
<span data-ttu-id="9545b-109">Türetilen bir sınıfta temel sınıf zaten uyguladı bir arabirim üyesini yeniden uygulamalı.</span><span class="sxs-lookup"><span data-stu-id="9545b-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="9545b-110">Bu, geçersiz kılmasını temel sınıf üyesi aşağıdaki bakımlardan farklıdır:</span><span class="sxs-lookup"><span data-stu-id="9545b-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="9545b-111">Taban sınıf üyesi olması gerekmez [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) reimplemented için.</span><span class="sxs-lookup"><span data-stu-id="9545b-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="9545b-112">Üye farklı bir adla yeniden uygulamalı.</span><span class="sxs-lookup"><span data-stu-id="9545b-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="9545b-113">`Implements` Anahtar sözcüğünü aşağıdaki bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9545b-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="9545b-114">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="9545b-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="9545b-115">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="9545b-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="9545b-116">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="9545b-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="9545b-117">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="9545b-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9545b-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9545b-118">See Also</span></span>  
 [<span data-ttu-id="9545b-119">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="9545b-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="9545b-120">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="9545b-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="9545b-121">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="9545b-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="9545b-122">Structure Deyimi</span><span class="sxs-lookup"><span data-stu-id="9545b-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
