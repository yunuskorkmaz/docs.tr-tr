---
title: Handles Yan Tümcesi
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 347f521267d4fd954ac359ab25ed5810cfd71d34
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873251"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="fad61-102">Handles Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fad61-102">Handles Clause (Visual Basic)</span></span>

<span data-ttu-id="fad61-103">Bir yordamın belirtilen bir olayı işlediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="fad61-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fad61-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fad61-104">Syntax</span></span>  
  
```vb  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="fad61-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="fad61-105">Parts</span></span>  

 `proceduredeclaration`  
 <span data-ttu-id="fad61-106">`Sub`Olayı işleyecek yordamın yordam bildirimi.</span><span class="sxs-lookup"><span data-stu-id="fad61-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="fad61-107">İşlenecek olayların listesi `proceduredeclaration` , virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="fad61-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="fad61-108">Olaylar, geçerli sınıfın temel sınıfı ya da anahtar sözcüğü kullanılarak belirtilen bir nesne tarafından oluşturulmalıdır `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="fad61-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fad61-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fad61-109">Remarks</span></span>  

 <span data-ttu-id="fad61-110">`Handles`Anahtar sözcüğü kullanılarak belirtilen bir nesne değişkeni tarafından oluşturulan olayları işlemesini sağlamak için yordam bildiriminin sonundaki anahtar sözcüğünü kullanın `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="fad61-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="fad61-111">`Handles`Anahtar sözcüğü, bir temel sınıftan olayları işlemek için türetilmiş bir sınıfta de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fad61-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="fad61-112">`Handles`Anahtar sözcüğü ve `AddHandler` deyimleri her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="fad61-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="fad61-113">`Handles`Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken anahtar sözcüğünü kullanın.</span><span class="sxs-lookup"><span data-stu-id="fad61-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="fad61-114">`AddHandler`İfade, çalışma zamanında yordamları olaylara bağlar.</span><span class="sxs-lookup"><span data-stu-id="fad61-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="fad61-115">Daha fazla bilgi için bkz. [AddHandler bildirisi](addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fad61-115">For more information, see [AddHandler Statement](addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="fad61-116">Özel olaylar için uygulama, `AddHandler` yordamı bir olay işleyicisi olarak eklediğinde olayın erişimcisini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fad61-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="fad61-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="fad61-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fad61-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="fad61-118">Example</span></span>  

 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="fad61-119">Aşağıdaki örnek, bir türetilen sınıfın bir `Handles` temel sınıftan bir olayı işlemek için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fad61-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="fad61-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="fad61-120">Example</span></span>  

 <span data-ttu-id="fad61-121">Aşağıdaki örnek, bir **WPF uygulama** projesi için iki düğme olay işleyicisi içerir.</span><span class="sxs-lookup"><span data-stu-id="fad61-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="fad61-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="fad61-122">Example</span></span>  

 <span data-ttu-id="fad61-123">Aşağıdaki örnek, önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="fad61-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="fad61-124">`eventlist`İçindeki `Handles` yan tümce her iki düğme için de olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="fad61-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="fad61-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fad61-125">See also</span></span>

- [<span data-ttu-id="fad61-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="fad61-126">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="fad61-127">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="fad61-127">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="fad61-128">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="fad61-128">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="fad61-129">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="fad61-129">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="fad61-130">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="fad61-130">RaiseEvent Statement</span></span>](raiseevent-statement.md)
- [<span data-ttu-id="fad61-131">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="fad61-131">Events</span></span>](../../programming-guide/language-features/events/index.md)
