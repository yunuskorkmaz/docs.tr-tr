---
title: "Implements Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImplementsClause
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73f66eda29e37fda15b4c838da5a0458684131da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="implements-clause-visual-basic"></a><span data-ttu-id="621da-102">Implements Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="621da-102">Implements Clause (Visual Basic)</span></span>
<span data-ttu-id="621da-103">Sınıf veya yapı üyesi bir arabiriminde tanımlanan üye uygulamasını sağladığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="621da-103">Indicates that a class or structure member is providing the implementation for a member defined in an interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="621da-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="621da-104">Remarks</span></span>  
<span data-ttu-id="621da-105">`Implements` Anahtar sözcüğü ile aynı değil [Implements deyimi](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="621da-105">The `Implements` keyword is not the same as the [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span> <span data-ttu-id="621da-106">Kullandığınız `Implements` bir sınıf veya yapı bir veya daha fazla arabirimlerini uygular ve ardından her üye için kullandığınız belirtmek için deyimi `Implements` hangi arabirimi ve hangi üye belirtmek için anahtar sözcüğü, uygular.</span><span class="sxs-lookup"><span data-stu-id="621da-106">You use the `Implements` statement to specify that a class or structure implements one or more interfaces, and then for each member you use the `Implements` keyword to specify which interface and which member it implements.</span></span>

<span data-ttu-id="621da-107">Bir sınıf veya yapı arabirim uygularsa, içermelidir `Implements` deyimi hemen sonra [Class deyimi](../../../visual-basic/language-reference/statements/class-statement.md) veya [Structure deyimi](../../../visual-basic/language-reference/statements/structure-statement.md), ve tüm üyelerin uygulamalıdır arabirim tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="621da-107">If a class or structure implements an interface, it must include the `Implements` statement immediately after the [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md) or [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md), and it must implement all the members defined by the interface.</span></span>

## <a name="reimplementation"></a><span data-ttu-id="621da-108">Yeniden uygulama</span><span class="sxs-lookup"><span data-stu-id="621da-108">Reimplementation</span></span>  
<span data-ttu-id="621da-109">Türetilen bir sınıfta temel sınıf zaten uyguladı bir arabirim üyesini yeniden uygulamalı.</span><span class="sxs-lookup"><span data-stu-id="621da-109">In a derived class, you can reimplement an interface member that the base class has already implemented.</span></span> <span data-ttu-id="621da-110">Bu, geçersiz kılmasını temel sınıf üyesi aşağıdaki bakımlardan farklıdır:</span><span class="sxs-lookup"><span data-stu-id="621da-110">This is different from overriding the base class member in the following respects:</span></span>

- <span data-ttu-id="621da-111">Taban sınıf üyesi olması gerekmez [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) reimplemented için.</span><span class="sxs-lookup"><span data-stu-id="621da-111">The base class member does not need to be [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) to be reimplemented.</span></span>
- <span data-ttu-id="621da-112">Üye farklı bir adla yeniden uygulamalı.</span><span class="sxs-lookup"><span data-stu-id="621da-112">You can reimplement the member with a different name.</span></span>

<span data-ttu-id="621da-113">`Implements` Anahtar sözcüğünü aşağıdaki bağlamlarında kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="621da-113">The `Implements` keyword can be used in the following contexts:</span></span>
- [<span data-ttu-id="621da-114">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="621da-114">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="621da-115">Function deyimi</span><span class="sxs-lookup"><span data-stu-id="621da-115">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="621da-116">Property deyimi</span><span class="sxs-lookup"><span data-stu-id="621da-116">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="621da-117">Sub deyimi</span><span class="sxs-lookup"><span data-stu-id="621da-117">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="621da-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="621da-118">See Also</span></span>  
 [<span data-ttu-id="621da-119">Implements deyimi</span><span class="sxs-lookup"><span data-stu-id="621da-119">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [<span data-ttu-id="621da-120">Interface deyimi</span><span class="sxs-lookup"><span data-stu-id="621da-120">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [<span data-ttu-id="621da-121">Class deyimi</span><span class="sxs-lookup"><span data-stu-id="621da-121">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
 [<span data-ttu-id="621da-122">Structure deyimi</span><span class="sxs-lookup"><span data-stu-id="621da-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
