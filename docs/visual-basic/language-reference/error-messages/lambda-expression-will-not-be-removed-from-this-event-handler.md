---
description: 'Hakkında daha fazla bilgi edinin: BC42326: lambda ifadesi bu olay işleyicisinden kaldırılmayacak'
title: Lambda ifadesi bu olay işleyiciden kaldırılmayacak
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 6feb8733a6413caa564d2c930b4d35dc5697b4fe
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795956"
---
# <a name="bc42326-lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="35fe1-103">BC42326: lambda ifadesi bu olay işleyicisinden kaldırılmayacak</span><span class="sxs-lookup"><span data-stu-id="35fe1-103">BC42326: Lambda expression will not be removed from this event handler</span></span>

<span data-ttu-id="35fe1-104">Lambda ifadesi bu olay işleyicisinden kaldırılmayacak.</span><span class="sxs-lookup"><span data-stu-id="35fe1-104">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="35fe1-105">Lambda ifadesini bir değişkene atayın ve olayı eklemek ve kaldırmak için değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="35fe1-105">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>

<span data-ttu-id="35fe1-106">Lambda ifadeleri olay işleyicileriyle kullanıldığında, bekleeceğiniz davranışı göremeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="35fe1-106">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="35fe1-107">Derleyici, aynı olsalar bile her bir lambda ifadesi tanımı için yeni bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="35fe1-107">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="35fe1-108">Bu nedenle, aşağıdaki kod görüntülenir `False` .</span><span class="sxs-lookup"><span data-stu-id="35fe1-108">Therefore, the following code displays `False`.</span></span>

```vb
Module Module1

    Sub Main()
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1
        Console.WriteLine(fun1 = fun2)
    End Sub

    Delegate Function ChangeInteger(ByVal x As Integer) As Integer

End Module
```

<span data-ttu-id="35fe1-109">Lambda ifadeleri olay işleyicileriyle kullanıldığında, bu beklenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="35fe1-109">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="35fe1-110">Aşağıdaki örnekte, tarafından eklenen lambda ifadesi `AddHandler` deyimi tarafından kaldırılmaz `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="35fe1-110">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Sub Main()

        ' The following line adds one listener to the event.
        AddHandler ProcessInteger, Function(m As Integer) m

        ' The following statement searches the current listeners
        ' for a match to remove. However, this lambda is not the same
        ' as the previous one, so nothing is removed.
        RemoveHandler ProcessInteger, Function(m As Integer) m

    End Sub
End Module
```

<span data-ttu-id="35fe1-111">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="35fe1-111">By default, this message is a warning.</span></span> <span data-ttu-id="35fe1-112">Uyarıları gizleme veya uyarıları hata olarak işleme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="35fe1-112">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="35fe1-113">**Hata kimliği:** BC42326</span><span class="sxs-lookup"><span data-stu-id="35fe1-113">**Error ID:** BC42326</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="35fe1-114">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="35fe1-114">To correct this error</span></span>

<span data-ttu-id="35fe1-115">Uyarıyı önlemek ve lambda ifadesini kaldırmak için lambda ifadesini bir değişkene atayın ve `AddHandler` `RemoveHandler` Aşağıdaki örnekte gösterildiği gibi değişkeni hem hem de deyimlerde kullanın.</span><span class="sxs-lookup"><span data-stu-id="35fe1-115">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Dim PrintHandler As ProcessIntegerEventHandler

    Sub Main()

        ' Assign the lambda expression to a variable.
        PrintHandler = Function(m As Integer) m

        ' Use the variable to add the listener.
        AddHandler ProcessInteger, PrintHandler

        ' Use the variable again when you want to remove the listener.
        RemoveHandler ProcessInteger, PrintHandler

    End Sub
End Module
```

## <a name="see-also"></a><span data-ttu-id="35fe1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35fe1-116">See also</span></span>

- [<span data-ttu-id="35fe1-117">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="35fe1-117">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="35fe1-118">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="35fe1-118">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="35fe1-119">Ekinlikler</span><span class="sxs-lookup"><span data-stu-id="35fe1-119">Events</span></span>](../../programming-guide/language-features/events/index.md)
