---
description: 'Hakkında daha fazla bilgi edinin: Visual Basic bir olay işleyicisini çağırma'
title: Olay işleyicisini çağırma
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- event handlers [Visual Basic], calling
- event handlers
- procedures [Visual Basic], event handlers
- procedures [Visual Basic], calling
no-loc:
- WithEvents
ms.assetid: 72e18ef8-144e-40df-a1f4-066a57271e28
ms.openlocfilehash: 7e65b36d392211be533bb4881658b1cdb8057d5d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476260"
---
# <a name="how-to-call-an-event-handler-in-visual-basic"></a><span data-ttu-id="324d7-103">Visual Basic bir olay işleyicisini çağırma</span><span class="sxs-lookup"><span data-stu-id="324d7-103">How to call an event handler in Visual Basic</span></span>

<span data-ttu-id="324d7-104">Bir *olay* , bir program bileşeni tarafından tanınan ve yanıt vermek için kod yazabileceğiniz bir fare tıklaması veya kredi limiti gibi bir eylem veya oluşumdır.</span><span class="sxs-lookup"><span data-stu-id="324d7-104">An *event* is an action or occurrence — such as a mouse click or a credit limit exceeded — that is recognized by some program component, and for which you can write code to respond.</span></span> <span data-ttu-id="324d7-105">*Olay işleyicisi* , bir olaya yanıt vermek için yazdığınız koddur.</span><span class="sxs-lookup"><span data-stu-id="324d7-105">An *event handler* is the code you write to respond to an event.</span></span>

<span data-ttu-id="324d7-106">Visual Basic bir olay işleyicisi bir `Sub` yordamdır.</span><span class="sxs-lookup"><span data-stu-id="324d7-106">An event handler in Visual Basic is a `Sub` procedure.</span></span> <span data-ttu-id="324d7-107">Ancak, normalde bunu diğer yordamlarla aynı şekilde çağırmayın `Sub` .</span><span class="sxs-lookup"><span data-stu-id="324d7-107">However, you do not normally call it the same way as other `Sub` procedures.</span></span> <span data-ttu-id="324d7-108">Bunun yerine, yordamı olay için bir işleyici olarak belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="324d7-108">Instead, you identify the procedure as a handler for the event.</span></span> <span data-ttu-id="324d7-109">Bunu bir [`Handles`](../../../language-reference/statements/handles-clause.md) yan tümce ve bir değişkenle ya da bir [`WithEvents`](../../../language-reference/modifiers/withevents.md) [AddHandler ifadesiyle](../../../language-reference/statements/addhandler-statement.md)yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="324d7-109">You can do this either with a [`Handles`](../../../language-reference/statements/handles-clause.md) clause and a [`WithEvents`](../../../language-reference/modifiers/withevents.md) variable, or with an [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md).</span></span> <span data-ttu-id="324d7-110">`Handles`Yan tümcesinin kullanılması, Visual Basic bir olay işleyicisini bildirmek için varsayılan yoldur.</span><span class="sxs-lookup"><span data-stu-id="324d7-110">Using a `Handles` clause is the default way to declare an event handler in Visual Basic.</span></span> <span data-ttu-id="324d7-111">Bu, tümleşik geliştirme ortamında (IDE) programlama yaparken, tasarımcı tarafından yazılan olay işleyicilerinin yoludur.</span><span class="sxs-lookup"><span data-stu-id="324d7-111">This is the way the event handlers are written by the designers when you program in the integrated development environment (IDE).</span></span> <span data-ttu-id="324d7-112">`AddHandler`İfade, olayları çalışma zamanında dinamik olarak yükseltmek için uygundur.</span><span class="sxs-lookup"><span data-stu-id="324d7-112">The `AddHandler` statement is suitable for raising events dynamically at run time.</span></span>

<span data-ttu-id="324d7-113">Olay gerçekleştiğinde, Visual Basic olay işleyicisi yordamını otomatik olarak çağırır.</span><span class="sxs-lookup"><span data-stu-id="324d7-113">When the event occurs, Visual Basic automatically calls the event handler procedure.</span></span> <span data-ttu-id="324d7-114">Olaya erişimi olan herhangi bir kod, bir [RaiseEvent ifadesiyle](../../../language-reference/statements/raiseevent-statement.md)yürütülerek oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="324d7-114">Any code that has access to the event can cause it to occur by executing a [RaiseEvent Statement](../../../language-reference/statements/raiseevent-statement.md).</span></span>

<span data-ttu-id="324d7-115">Birden fazla olay işleyicisini aynı olayla ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="324d7-115">You can associate more than one event handler with the same event.</span></span> <span data-ttu-id="324d7-116">Bazı durumlarda, bir etkinliğin bir olaydan ilişkisini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="324d7-116">In some cases you can dissociate a handler from an event.</span></span> <span data-ttu-id="324d7-117">Daha fazla bilgi için bkz. [Olaylar](../events/index.md).</span><span class="sxs-lookup"><span data-stu-id="324d7-117">For more information, see [Events](../events/index.md).</span></span>

## <a name="call-an-event-handler-using-no-loc-texthandles-and-withevents"></a><span data-ttu-id="324d7-118">Ve kullanarak bir olay işleyicisi çağırma :::no-loc text="Handles":::WithEvents</span><span class="sxs-lookup"><span data-stu-id="324d7-118">Call an event handler using :::no-loc text="Handles"::: and WithEvents</span></span>

1. <span data-ttu-id="324d7-119">Olayın bir [Event ifadesiyle](../../../language-reference/statements/event-statement.md)bildiriminin bulunduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="324d7-119">Make sure the event is declared with an [Event Statement](../../../language-reference/statements/event-statement.md).</span></span>

2. <span data-ttu-id="324d7-120">Anahtar sözcüğünü kullanarak modül veya sınıf düzeyinde bir nesne değişkeni bildirin [`WithEvents`](../../../language-reference/modifiers/withevents.md) .</span><span class="sxs-lookup"><span data-stu-id="324d7-120">Declare an object variable at module or class level, using the [`WithEvents`](../../../language-reference/modifiers/withevents.md) keyword.</span></span> <span data-ttu-id="324d7-121">`As`Bu değişkenin yan tümcesi, olayı oluşturan sınıfı belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="324d7-121">The `As` clause for this variable must specify the class that raises the event.</span></span>

3. <span data-ttu-id="324d7-122">Olay işleme `Sub` yordamının bildiriminde, [`Handles`](../../../language-reference/statements/handles-clause.md) `WithEvents` değişkeni ve olay adını belirten bir yan tümce ekleyin.</span><span class="sxs-lookup"><span data-stu-id="324d7-122">In the declaration of the event-handling `Sub` procedure, add a [`Handles`](../../../language-reference/statements/handles-clause.md) clause that specifies the `WithEvents` variable and the event name.</span></span>

4. <span data-ttu-id="324d7-123">Olay gerçekleştiğinde, Visual Basic yordamı otomatik olarak çağırır `Sub` .</span><span class="sxs-lookup"><span data-stu-id="324d7-123">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="324d7-124">Kodunuz `RaiseEvent` olay oluşmasını sağlamak için bir ifade kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="324d7-124">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="324d7-125">Aşağıdaki örnek, olayını oluşturan sınıfa başvuran bir olayı ve `WithEvents` değişkeni tanımlar.</span><span class="sxs-lookup"><span data-stu-id="324d7-125">The following example defines an event and a `WithEvents` variable that refers to the class that raises the event.</span></span> <span data-ttu-id="324d7-126">Olay işleme yordamı, `Sub` `Handles` işleyen sınıfı ve olayı belirtmek için bir yan tümce kullanır.</span><span class="sxs-lookup"><span data-stu-id="324d7-126">The event-handling `Sub` procedure uses a `Handles` clause to specify the class and event it handles.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="4":::

## <a name="call-an-event-handler-using-addhandler"></a><span data-ttu-id="324d7-127">AddHandler kullanarak olay işleyicisini çağırma</span><span class="sxs-lookup"><span data-stu-id="324d7-127">Call an event handler using AddHandler</span></span>

1. <span data-ttu-id="324d7-128">Olayın bir ifadesiyle bildirildiği emin olun `Event` .</span><span class="sxs-lookup"><span data-stu-id="324d7-128">Make sure the event is declared with an `Event` statement.</span></span>

2. <span data-ttu-id="324d7-129">Olay işleme yordamını olaya dinamik olarak bağlamak için bir [AddHandler ekstresi](../../../language-reference/statements/addhandler-statement.md) yürütün `Sub` .</span><span class="sxs-lookup"><span data-stu-id="324d7-129">Execute an [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) to dynamically connect the event-handling `Sub` procedure with the event.</span></span>

3. <span data-ttu-id="324d7-130">Olay gerçekleştiğinde, Visual Basic yordamı otomatik olarak çağırır `Sub` .</span><span class="sxs-lookup"><span data-stu-id="324d7-130">When the event occurs, Visual Basic automatically calls the `Sub` procedure.</span></span> <span data-ttu-id="324d7-131">Kodunuz `RaiseEvent` olay oluşmasını sağlamak için bir ifade kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="324d7-131">Your code can use a `RaiseEvent` statement to make the event occur.</span></span>

    <span data-ttu-id="324d7-132">Aşağıdaki örnek, yordamını bir olay işleyicisi olarak ilişkilendirmek için oluşturucuda [AddHandler ifadesini](../../../language-reference/statements/addhandler-statement.md) kullanır `OnFormClosing` <xref:System.Windows.Forms.Form.FormClosing> .</span><span class="sxs-lookup"><span data-stu-id="324d7-132">The following example uses the [AddHandler statement](../../../language-reference/statements/addhandler-statement.md) in the constructor to associate the `OnFormClosing` procedure as an event handler for <xref:System.Windows.Forms.Form.FormClosing>.</span></span>

    :::code language="vb" source="snippets/how-to-call-an-event-handler/SpecialForm.vb" id="5":::

    <span data-ttu-id="324d7-133">[RemoveHandler ifadesini](../../../language-reference/statements/removehandler-statement.md)yürüterek bir olay işleyicisinin bir olaydan ilişkisini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="324d7-133">You can dissociate an event handler from an event by executing the [RemoveHandler statement](../../../language-reference/statements/removehandler-statement.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="324d7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="324d7-134">See also</span></span>

- [<span data-ttu-id="324d7-135">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="324d7-135">Procedures</span></span>](index.md)
- [<span data-ttu-id="324d7-136">Alt Yordamlar</span><span class="sxs-lookup"><span data-stu-id="324d7-136">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="324d7-137">Sub Deyimi</span><span class="sxs-lookup"><span data-stu-id="324d7-137">Sub Statement</span></span>](../../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="324d7-138">AddressOf İşleci</span><span class="sxs-lookup"><span data-stu-id="324d7-138">AddressOf Operator</span></span>](../../../language-reference/operators/addressof-operator.md)
- [<span data-ttu-id="324d7-139">Nasıl yapılır: Yordam Oluşturma</span><span class="sxs-lookup"><span data-stu-id="324d7-139">How to: Create a Procedure</span></span>](how-to-create-a-procedure.md)
- [<span data-ttu-id="324d7-140">Nasıl yapılır: Değer Döndürmeyen Bir Yordam Çağırma</span><span class="sxs-lookup"><span data-stu-id="324d7-140">How to: Call a Procedure that Does Not Return a Value</span></span>](how-to-call-a-procedure-that-does-not-return-a-value.md)
