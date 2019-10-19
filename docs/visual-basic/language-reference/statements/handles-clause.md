---
title: Handles Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: ae05e77515e4e2b50cdf5f9a1908375fa311c3a3
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581806"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="0c16e-102">Handles Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c16e-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="0c16e-103">Bir yordamın belirtilen bir olayı işlediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="0c16e-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c16e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0c16e-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="0c16e-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="0c16e-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="0c16e-106">Olayı işleyecek yordamın `Sub` yordam bildirimi.</span><span class="sxs-lookup"><span data-stu-id="0c16e-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="0c16e-107">İşlenecek `proceduredeclaration`, virgülle ayırarak olayların listesi.</span><span class="sxs-lookup"><span data-stu-id="0c16e-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="0c16e-108">Olaylar, geçerli sınıfın temel sınıfı veya `WithEvents` anahtar sözcüğü kullanılarak belirtilen bir nesne tarafından oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0c16e-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c16e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0c16e-109">Remarks</span></span>  
 <span data-ttu-id="0c16e-110">Bir yordam bildiriminin sonundaki `Handles` anahtar sözcüğünü kullanarak, `WithEvents` anahtar sözcüğü kullanılarak belirtilen bir nesne değişkeni tarafından oluşturulan olayların işlemesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0c16e-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="0c16e-111">@No__t_0 anahtar sözcüğü, bir temel sınıftan olayları işlemek için türetilmiş bir sınıfta de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0c16e-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="0c16e-112">@No__t_0 anahtar sözcüğü ve `AddHandler` deyimin her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="0c16e-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="0c16e-113">Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken `Handles` anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c16e-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="0c16e-114">@No__t_0 ifade, çalışma zamanında yordamları olaylara bağlar.</span><span class="sxs-lookup"><span data-stu-id="0c16e-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="0c16e-115">Daha fazla bilgi için bkz. [AddHandler bildirisi](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0c16e-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="0c16e-116">Özel olaylar için uygulama, yordamı bir olay işleyicisi olarak eklediğinde olayın `AddHandler` erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="0c16e-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="0c16e-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0c16e-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c16e-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c16e-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="0c16e-119">Aşağıdaki örnek, bir türetilen sınıfın bir temel sınıftan bir olayı işlemek için `Handles` deyiminizi nasıl kullanabileceğinizi gösterir.</span><span class="sxs-lookup"><span data-stu-id="0c16e-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="0c16e-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c16e-120">Example</span></span>  
 <span data-ttu-id="0c16e-121">Aşağıdaki örnek, bir **WPF uygulama** projesi için iki düğme olay işleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="0c16e-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="0c16e-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="0c16e-122">Example</span></span>  
 <span data-ttu-id="0c16e-123">Aşağıdaki örnek, önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="0c16e-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="0c16e-124">@No__t_1 yan tümcesindeki `eventlist` her iki düğme için de olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="0c16e-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="0c16e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c16e-125">See also</span></span>

- [<span data-ttu-id="0c16e-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="0c16e-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="0c16e-127">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="0c16e-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="0c16e-128">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="0c16e-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="0c16e-129">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="0c16e-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="0c16e-130">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="0c16e-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="0c16e-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="0c16e-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
