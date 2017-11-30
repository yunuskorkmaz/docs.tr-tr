---
title: "Handles Tümcesi (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords: Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a23b3d96052ad179ea25150bb570461a9e764977
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="6287a-102">Handles Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6287a-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="6287a-103">Bir yordam belirtilen bir olay işleme bildirir.</span><span class="sxs-lookup"><span data-stu-id="6287a-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6287a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6287a-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="6287a-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="6287a-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="6287a-106">`Sub` Yordamı bildirimi olayı işleyecek bir yordam.</span><span class="sxs-lookup"><span data-stu-id="6287a-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="6287a-107">Olayları listesi `proceduredeclaration` işlemek için virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="6287a-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="6287a-108">Olayları ya da taban sınıfı için geçerli sınıf veya kullanılarak bildirilen bir nesne tarafından oluşturulması `WithEvents` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6287a-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6287a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6287a-109">Remarks</span></span>  
 <span data-ttu-id="6287a-110">Kullanım `Handles` anahtar sözcüğü bir nesne değişkeni tarafından başlatılan olayları işlemek için neden bir yordam bildiriminin sonundaki kullanarak bildirilen `WithEvents` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6287a-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="6287a-111">`Handles` Anahtar sözcüğü de türetilen bir sınıfta bir temel sınıf olayları işlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6287a-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="6287a-112">`Handles` Anahtar sözcüğü ve `AddHandler` deyimi hem belirli yordamları belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="6287a-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="6287a-113">Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6287a-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="6287a-114">`AddHandler` Deyimi olaylarına yordamlar çalışma zamanında bağlanır.</span><span class="sxs-lookup"><span data-stu-id="6287a-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="6287a-115">Daha fazla bilgi için bkz: [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6287a-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="6287a-116">Özel olaylar için uygulama olay çağırır `AddHandler` olay işleyici yordamı eklediğinde erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="6287a-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="6287a-117">Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6287a-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6287a-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="6287a-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_1.vb)]  
  
 <span data-ttu-id="6287a-119">Aşağıdaki örnek, türetilmiş bir sınıf nasıl kullanabileceğinizi gösterir `Handles` temel sınıfından bir olayını işlemek için deyimi.</span><span class="sxs-lookup"><span data-stu-id="6287a-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="6287a-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="6287a-120">Example</span></span>  
 <span data-ttu-id="6287a-121">Aşağıdaki örnekte iki düğmesi olay işleyicilerini içeren bir **WPF uygulaması** projesi.</span><span class="sxs-lookup"><span data-stu-id="6287a-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="6287a-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="6287a-122">Example</span></span>  
 <span data-ttu-id="6287a-123">Aşağıdaki örnek önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="6287a-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="6287a-124">`eventlist` İçinde `Handles` yan tümcesi hem düğmelerinin olaylarını içerir.</span><span class="sxs-lookup"><span data-stu-id="6287a-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/handles-clause_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6287a-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6287a-125">See Also</span></span>  
 [<span data-ttu-id="6287a-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="6287a-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="6287a-127">AddHandler deyimi</span><span class="sxs-lookup"><span data-stu-id="6287a-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="6287a-128">RemoveHandler deyimi</span><span class="sxs-lookup"><span data-stu-id="6287a-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="6287a-129">Event deyimi</span><span class="sxs-lookup"><span data-stu-id="6287a-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="6287a-130">RaiseEvent deyimi</span><span class="sxs-lookup"><span data-stu-id="6287a-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)  
 [<span data-ttu-id="6287a-131">Olayları</span><span class="sxs-lookup"><span data-stu-id="6287a-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
