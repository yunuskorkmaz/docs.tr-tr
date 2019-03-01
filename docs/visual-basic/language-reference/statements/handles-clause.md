---
title: Handles Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 3be28ee718675b1f6bebfaff03baaf561a6fff43
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974074"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="ce36b-102">Handles Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce36b-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="ce36b-103">Bir yordamın belirtilmiş bir olayı işlediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="ce36b-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce36b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce36b-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="ce36b-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ce36b-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="ce36b-106">`Sub` Olayı işleyecek yordam için yordam bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ce36b-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="ce36b-107">Olayları listesi `proceduredeclaration` işlemek için virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="ce36b-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="ce36b-108">Olayları için geçerli sınıfın ya da temel sınıf veya kullanılarak bildirilen bir nesne oluşturulması `WithEvents` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ce36b-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce36b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce36b-109">Remarks</span></span>  
 <span data-ttu-id="ce36b-110">Kullanım `Handles` sonunda bir nesne değişkeni tarafından başlatılan olayları işlemek için neden bir yordam bildirimi, anahtar sözcüğü kullanılarak bildirilen `WithEvents` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ce36b-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="ce36b-111">`Handles` Anahtar sözcüğü de türetilen bir sınıfta bir temel sınıf olayları işlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce36b-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="ce36b-112">`Handles` Anahtar sözcüğü ve `AddHandler` iki deyimi belirli bir yordam belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ce36b-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="ce36b-113">Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ce36b-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="ce36b-114">`AddHandler` Deyimi olayları yordamları çalışma zamanında bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ce36b-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="ce36b-115">Daha fazla bilgi için [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce36b-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="ce36b-116">Özel olaylar için uygulama olay çağırır `AddHandler` yordamı bir olay işleyicisi eklediğinde erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="ce36b-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="ce36b-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce36b-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce36b-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce36b-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="ce36b-119">Aşağıdaki örnek, türetilmiş bir sınıf nasıl kullanabileceğinizi gösterir. `Handles` deyimi bir temel sınıftan bir olayı işlemek için.</span><span class="sxs-lookup"><span data-stu-id="ce36b-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="ce36b-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce36b-120">Example</span></span>  
 <span data-ttu-id="ce36b-121">Aşağıdaki örnek iki düğme olay işleyicilerini içeren bir **WPF uygulaması** proje.</span><span class="sxs-lookup"><span data-stu-id="ce36b-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="ce36b-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce36b-122">Example</span></span>  
 <span data-ttu-id="ce36b-123">Aşağıdaki örnek önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ce36b-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="ce36b-124">`eventlist` İçinde `Handles` yan tümcesi, iki düğme için olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="ce36b-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="ce36b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce36b-125">See also</span></span>
- [<span data-ttu-id="ce36b-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="ce36b-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="ce36b-127">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce36b-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="ce36b-128">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce36b-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="ce36b-129">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce36b-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="ce36b-130">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce36b-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="ce36b-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ce36b-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
