---
title: 'Nasıl yapılır: olay Işleyicisi çağırma'
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 0c626a9ad92fe2cd0ea117a9abdd2965a09df2ea
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340423"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="388b1-102">Nasıl yapılır: Olay İşleyicisi Çağırma (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="388b1-102">How to: Call an Event Handler in Visual Basic</span></span>

<span data-ttu-id="388b1-103">Bir *olay* , bir program bileşeni tarafından tanınan ve yanıt vermek için kod yazabileceğiniz bir fare tıklaması veya kredi limiti gibi bir eylem veya oluşumdır.</span><span class="sxs-lookup"><span data-stu-id="388b1-103">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="388b1-104">*Olay işleyicisi* , bir olaya yanıt vermek için yazdığınız koddur.</span><span class="sxs-lookup"><span data-stu-id="388b1-104">An *event handler* is the code you write to respond to an event.</span></span>

 <span data-ttu-id="388b1-105">Visual Basic bir olay işleyicisi `Sub` yordamdır.</span><span class="sxs-lookup"><span data-stu-id="388b1-105">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="388b1-106">Ancak, normalde bunu diğer `Sub` yordamlarıyla aynı şekilde çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="388b1-106">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="388b1-107">Bunun yerine, yordamı olay için bir işleyici olarak belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="388b1-107">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="388b1-108">Bunu bir [Handles](../../../language-reference/statements/handles-clause.md) yan tümcesi ve [WithEvents](../../../language-reference/modifiers/withevents.md) değişkeniyle ya da bir [AddHandler ifadesiyle](../../../language-reference/statements/addhandler-statement.md)yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="388b1-108">You can do this either with a [Handles](../../../language-reference/statements/handles-clause.md) clause and a [WithEvents](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="388b1-109">`Handles` yan tümcesinin kullanılması, Visual Basic bir olay işleyicisini belirtmenin varsayılan yoludur.</span><span class="sxs-lookup"><span data-stu-id="388b1-109">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="388b1-110">Bu, tümleşik geliştirme ortamında (IDE) programlama yaparken, tasarımcı tarafından yazılan olay işleyicilerinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="388b1-110">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="388b1-111">`AddHandler` deyimleri, olayları çalışma zamanında dinamik olarak yükseltmek için uygundur.</span><span class="sxs-lookup"><span data-stu-id="388b1-111">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>

 <span data-ttu-id="388b1-112">Olay gerçekleştiğinde, Visual Basic olay işleyicisi yordamını otomatik olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="388b1-112">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="388b1-113">Olaya erişimi olan herhangi bir kod, bir [RaiseEvent ifadesiyle](../../../language-reference/statements/raiseevent-statement.md)yürütülerek oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="388b1-113">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).</span></span>

 <span data-ttu-id="388b1-114">Birden fazla olay işleyicisini aynı olayla ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="388b1-114">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="388b1-115">Bazı durumlarda, bir etkinliğin bir olaydan ilişkisini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="388b1-115">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="388b1-116">Daha fazla bilgi için bkz. [Olaylar](../events/index.md).</span><span class="sxs-lookup"><span data-stu-id="388b1-116">For more information, see [Events](../events/index.md).</span></span>

### <a name="to-call-an-event-handler-using-handles-and-withevents"></a><span data-ttu-id="388b1-117">Handles ve WithEvents kullanarak bir olay işleyicisini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="388b1-117">To call an event handler using Handles and WithEvents</span></span>

1. <span data-ttu-id="388b1-118">Olayın bir [Event ifadesiyle](../../../language-reference/statements/event-statement.md)bildiriminin bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="388b1-118">Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).</span></span>

2. <span data-ttu-id="388b1-119">[WithEvents](../../../language-reference/modifiers/withevents.md) anahtar sözcüğünü kullanarak modül veya sınıf düzeyinde bir nesne değişkeni bildirin.</span><span class="sxs-lookup"><span data-stu-id="388b1-119">Declare an object variable at module or class level, using the [WithEvents](../../../language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="388b1-120">Bu değişkenin `As` yan tümcesi, olayı oluşturan sınıfı belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="388b1-120">The `As` clause for this variable must specify the class that raises the event.</span></span>

3. <span data-ttu-id="388b1-121">Olay işleme `Sub` yordamının bildiriminde, `WithEvents` değişkenini ve olay adını belirten bir [Handles](../../../language-reference/statements/handles-clause.md) yan tümcesi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="388b1-121">In the declaration of the event-handling `Sub` procedure, add a [Handles](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>

4. <span data-ttu-id="388b1-122">Olay gerçekleştiğinde, Visual Basic `Sub` yordamını otomatik olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="388b1-122">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="388b1-123">Kodunuz, olayın gerçekleşmesini sağlamak için `RaiseEvent` bir ifade kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="388b1-123">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

     <span data-ttu-id="388b1-124">Aşağıdaki örnek, olayını oluşturan sınıfa başvuran bir olayı ve bir `WithEvents` değişkenini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="388b1-124">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="388b1-125">Olay işleme `Sub` yordamı, işleyeceği sınıfı ve olayı belirtmek için bir `Handles` yan tümcesi kullanır.</span><span class="sxs-lookup"><span data-stu-id="388b1-125">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>

     [!code-vb[VbVbcnProcedures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#4)]

### <a name="to-call-an-event-handler-using-addhandler"></a><span data-ttu-id="388b1-126">AddHandler kullanarak bir olay işleyicisini çağırmak için</span><span class="sxs-lookup"><span data-stu-id="388b1-126">To call an event handler using AddHandler</span></span>

1. <span data-ttu-id="388b1-127">Olayın bir `Event` ifadesiyle bildirildiği emin olun.</span><span class="sxs-lookup"><span data-stu-id="388b1-127">Make sure the event is declared with an `Event` statement.</span></span>

2. <span data-ttu-id="388b1-128">Olay işleme `Sub` yordamını olaya dinamik olarak bağlamak için bir [AddHandler ifadesini](../../../language-reference/statements/addhandler-statement.md) yürütün.</span><span class="sxs-lookup"><span data-stu-id="388b1-128">Execute an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>

3. <span data-ttu-id="388b1-129">Olay gerçekleştiğinde, Visual Basic `Sub` yordamını otomatik olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="388b1-129">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="388b1-130">Kodunuz, olayın gerçekleşmesini sağlamak için `RaiseEvent` bir ifade kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="388b1-130">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

     <span data-ttu-id="388b1-131">Aşağıdaki örnek, bir formun <xref:System.Windows.Forms.Form.Closing> olayını işlemek için bir `Sub` yordamı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="388b1-131">The following example defines a `Sub` procedure to handle the <xref:System.Windows.Forms.Form.Closing> event of a form.</span></span> <span data-ttu-id="388b1-132">Daha sonra, `catchClose` yordamını <xref:System.Windows.Forms.Form.Closing>bir olay işleyicisi olarak ilişkilendirmek için [AddHandler ifadesini](../../../language-reference/statements/addhandler-statement.md) kullanır.</span><span class="sxs-lookup"><span data-stu-id="388b1-132">It then uses the [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) to associate the `catchClose` procedure as an event handler for <xref:System.Windows.Forms.Form.Closing>.</span></span>

     [!code-vb[VbVbcnProcedures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#5)]

     <span data-ttu-id="388b1-133">[RemoveHandler ifadesini](../../../language-reference/statements/removehandler-statement.md)yürüterek bir olay işleyicisinin bir olaydan ilişkisini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="388b1-133">You can dissociate an event handler from an event by executing the [RemoveHandler Statement](../../../language-reference/statements/removehandler-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="388b1-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="388b1-134">See also</span></span>

- [<span data-ttu-id="388b1-135">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="388b1-135">Procedures</span></span>](index.md)
- [<span data-ttu-id="388b1-136">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="388b1-136">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="388b1-137">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="388b1-137">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="388b1-138">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="388b1-138">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="388b1-139">Nasıl yapılır: Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="388b1-139">How to: Create a Procedure</span></span>](how-to-create-a-procedure.md)
- [<span data-ttu-id="388b1-140">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="388b1-140">How to: Call a Procedure that Does Not Return a Value</span></span>](how-to-call-a-procedure-that-does-not-return-a-value.md)
