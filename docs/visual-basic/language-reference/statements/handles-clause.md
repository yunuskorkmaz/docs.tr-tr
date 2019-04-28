---
title: Handles Tümcesi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Handles
- vb.Handles
helpviewer_keywords:
- Handles keyword [Visual Basic]
ms.assetid: 1b051c0e-f499-42f6-acb5-6f4f27824b40
ms.openlocfilehash: 50a449ea8a5131c878cf703f44695cd2e2304444
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638044"
---
# <a name="handles-clause-visual-basic"></a><span data-ttu-id="ce178-102">Handles Tümcesi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce178-102">Handles Clause (Visual Basic)</span></span>
<span data-ttu-id="ce178-103">Bir yordamın belirtilmiş bir olayı işlediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="ce178-103">Declares that a procedure handles a specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce178-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce178-104">Syntax</span></span>  
  
```  
proceduredeclaration Handles eventlist  
```  
  
## <a name="parts"></a><span data-ttu-id="ce178-105">Bölümler</span><span class="sxs-lookup"><span data-stu-id="ce178-105">Parts</span></span>  
 `proceduredeclaration`  
 <span data-ttu-id="ce178-106">`Sub` Olayı işleyecek yordam için yordam bildirimi.</span><span class="sxs-lookup"><span data-stu-id="ce178-106">The `Sub` procedure declaration for the procedure that will handle the event.</span></span>  
  
 `eventlist`  
 <span data-ttu-id="ce178-107">Olayları listesi `proceduredeclaration` işlemek için virgülle ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="ce178-107">List of the events for `proceduredeclaration` to handle, separated by commas.</span></span> <span data-ttu-id="ce178-108">Olayları için geçerli sınıfın ya da temel sınıf veya kullanılarak bildirilen bir nesne oluşturulması `WithEvents` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ce178-108">The events must be raised by either the base class for the current class, or by an object declared using the `WithEvents` keyword.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce178-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce178-109">Remarks</span></span>  
 <span data-ttu-id="ce178-110">Kullanım `Handles` sonunda bir nesne değişkeni tarafından başlatılan olayları işlemek için neden bir yordam bildirimi, anahtar sözcüğü kullanılarak bildirilen `WithEvents` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ce178-110">Use the `Handles` keyword at the end of a procedure declaration to cause it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span> <span data-ttu-id="ce178-111">`Handles` Anahtar sözcüğü de türetilen bir sınıfta bir temel sınıf olayları işlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce178-111">The `Handles` keyword can also be used in a derived class to handle events from a base class.</span></span>  
  
 <span data-ttu-id="ce178-112">`Handles` Anahtar sözcüğü ve `AddHandler` iki deyimi belirli bir yordam belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="ce178-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="ce178-113">Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="ce178-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="ce178-114">`AddHandler` Deyimi olayları yordamları çalışma zamanında bağlanır.</span><span class="sxs-lookup"><span data-stu-id="ce178-114">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="ce178-115">Daha fazla bilgi için [AddHandler deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce178-115">For more information, see [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md).</span></span>  
  
 <span data-ttu-id="ce178-116">Özel olaylar için uygulama olay çağırır `AddHandler` yordamı bir olay işleyicisi eklediğinde erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="ce178-116">For custom events, the application invokes the event's `AddHandler` accessor when it adds the procedure as an event handler.</span></span> <span data-ttu-id="ce178-117">Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce178-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce178-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce178-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#2)]  
  
 <span data-ttu-id="ce178-119">Aşağıdaki örnek, türetilmiş bir sınıf nasıl kullanabileceğinizi gösterir. `Handles` deyimi bir temel sınıftan bir olayı işlemek için.</span><span class="sxs-lookup"><span data-stu-id="ce178-119">The following example demonstrates how a derived class can use the `Handles` statement to handle an event from a base class.</span></span>  
  
 [!code-vb[VbVbalrEvents#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="ce178-120">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce178-120">Example</span></span>  
 <span data-ttu-id="ce178-121">Aşağıdaki örnek iki düğme olay işleyicilerini içeren bir **WPF uygulaması** proje.</span><span class="sxs-lookup"><span data-stu-id="ce178-121">The following example contains two button event handlers for a **WPF Application** project.</span></span>  
  
 [!code-vb[VbVbalrEvents#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#41)]  
  
## <a name="example"></a><span data-ttu-id="ce178-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce178-122">Example</span></span>  
 <span data-ttu-id="ce178-123">Aşağıdaki örnek önceki örneğe eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="ce178-123">The following example is equivalent to the previous example.</span></span> <span data-ttu-id="ce178-124">`eventlist` İçinde `Handles` yan tümcesi, iki düğme için olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="ce178-124">The `eventlist` in the `Handles` clause contains the events for both buttons.</span></span>  
  
 [!code-vb[VbVbalrEvents#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/class3.vb#42)]  
  
## <a name="see-also"></a><span data-ttu-id="ce178-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce178-125">See also</span></span>

- [<span data-ttu-id="ce178-126">WithEvents</span><span class="sxs-lookup"><span data-stu-id="ce178-126">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="ce178-127">AddHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce178-127">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="ce178-128">RemoveHandler Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce178-128">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="ce178-129">Event Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce178-129">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="ce178-130">RaiseEvent Deyimi</span><span class="sxs-lookup"><span data-stu-id="ce178-130">RaiseEvent Statement</span></span>](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
- [<span data-ttu-id="ce178-131">Olaylar</span><span class="sxs-lookup"><span data-stu-id="ce178-131">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
