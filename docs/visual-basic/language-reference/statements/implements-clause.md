---
description: 'Daha fazla bilgi edinin: Implements tümcesi (Visual Basic)'
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
ms.openlocfilehash: 360d8812a7c49d6462818246b1448e171dcd597f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769006"
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="9febb-103">Implements Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9febb-103">Implements Clause (Visual Basic)</span></span>

<span data-ttu-id="9febb-104">Bir sınıf veya yapı üyesinin, arabirim içinde tanımlanmış bir üye için uygulama sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9febb-104">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9febb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9febb-105">Remarks</span></span>  

<span data-ttu-id="9febb-106">`Implements`Anahtar sözcüğü, [Implements ifadesiyle](implements-statement.md)aynı değildir.</span><span class="sxs-lookup"><span data-stu-id="9febb-106">The `Implements` keyword is not the same as the [Implements Statement](implements-statement.md).</span></span> <span data-ttu-id="9febb-107">`Implements`Bir sınıf ya da yapının bir veya daha fazla arabirim uyguladığını belirtmek için ifadesini kullanın ve ardından her üye için `Implements` hangi arabirimin ve hangi üyenin uyguladığı, anahtar sözcüğünü kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="9febb-107">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="9febb-108">Bir sınıf veya yapı bir arabirim uygularsa, `Implements` [sınıf deyimden](class-statement.md) veya [Yapı deyimden](structure-statement.md)hemen sonra ifadesini içermesi gerekir ve arabirim tarafından tanımlanan tüm üyeleri uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="9febb-108">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](class-statement.md) or [Structure Statement](structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="9febb-109">Yeniden uygulama</span><span class="sxs-lookup"><span data-stu-id="9febb-109">Reimplementation</span></span>  

<span data-ttu-id="9febb-110">Türetilmiş bir sınıfta, temel sınıfın zaten uygulanmış olduğu bir arabirim üyesini yeniden uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9febb-110">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="9febb-111">Bu, aşağıdaki gibi temel sınıf üyesini geçersiz kılmadan farklıdır:</span><span class="sxs-lookup"><span data-stu-id="9febb-111">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="9febb-112">Temel sınıf üyesinin yeniden uygulanması için [geçersiz kılınabilir](../modifiers/overridable.md) olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9febb-112">The base class member does not need to be [Overridable](../modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="9febb-113">Üyeyi farklı bir adla yeniden uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9febb-113">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="9febb-114">`Implements`Anahtar sözcüğü aşağıdaki bağlamlarda kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9febb-114">The `Implements` keyword can be used in the following contexts:</span></span>

- [<span data-ttu-id="9febb-115">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="9febb-115">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="9febb-116">Function Deyimi</span><span class="sxs-lookup"><span data-stu-id="9febb-116">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="9febb-117">Property Deyimi</span><span class="sxs-lookup"><span data-stu-id="9febb-117">Property Statement</span></span>](property-statement.md)
- [<span data-ttu-id="9febb-118">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="9febb-118">Sub Statement</span></span>](sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="9febb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9febb-119">See also</span></span>

- [<span data-ttu-id="9febb-120">Implements Deyimi</span><span class="sxs-lookup"><span data-stu-id="9febb-120">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="9febb-121">Interface Deyimi</span><span class="sxs-lookup"><span data-stu-id="9febb-121">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="9febb-122">Class Deyimi</span><span class="sxs-lookup"><span data-stu-id="9febb-122">Class Statement</span></span>](class-statement.md)
- [<span data-ttu-id="9febb-123">Structure Yapısı</span><span class="sxs-lookup"><span data-stu-id="9febb-123">Structure Statement</span></span>](structure-statement.md)
