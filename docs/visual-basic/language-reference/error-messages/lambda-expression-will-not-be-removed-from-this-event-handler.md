---
title: Lambda ifadesi bu olay işleyiciden kaldırılmayacak
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 07ace3f1b9c5e512227dc1f718ef768b631c8303
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397382"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a><span data-ttu-id="fc398-102">Lambda ifadesi bu olay işleyiciden kaldırılmayacak</span><span class="sxs-lookup"><span data-stu-id="fc398-102">Lambda expression will not be removed from this event handler</span></span>

<span data-ttu-id="fc398-103">Lambda ifadesi bu olay işleyicisinden kaldırılmayacak.</span><span class="sxs-lookup"><span data-stu-id="fc398-103">Lambda expression will not be removed from this event handler.</span></span> <span data-ttu-id="fc398-104">Lambda ifadesini bir değişkene atayın ve olayı eklemek ve kaldırmak için değişkeni kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc398-104">Assign the lambda expression to a variable and use the variable to add and remove the event.</span></span>

<span data-ttu-id="fc398-105">Lambda ifadeleri olay işleyicileriyle kullanıldığında, bekleeceğiniz davranışı göremeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fc398-105">When lambda expressions are used with event handlers, you may not see the behavior you expect.</span></span> <span data-ttu-id="fc398-106">Derleyici, aynı olsalar bile her bir lambda ifadesi tanımı için yeni bir yöntem oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fc398-106">The compiler generates a new method for each lambda expression definition, even if they are identical.</span></span> <span data-ttu-id="fc398-107">Bu nedenle, aşağıdaki kod görüntülenir `False` .</span><span class="sxs-lookup"><span data-stu-id="fc398-107">Therefore, the following code displays `False`.</span></span>

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

<span data-ttu-id="fc398-108">Lambda ifadeleri olay işleyicileriyle kullanıldığında, bu beklenmeyen sonuçlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="fc398-108">When lambda expressions are used with event handlers, this may cause unexpected results.</span></span> <span data-ttu-id="fc398-109">Aşağıdaki örnekte, tarafından eklenen lambda ifadesi `AddHandler` deyimi tarafından kaldırılmaz `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="fc398-109">In the following example, the lambda expression added by `AddHandler` is not removed by the `RemoveHandler` statement.</span></span>

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

<span data-ttu-id="fc398-110">Bu ileti, varsayılan olarak bir uyarıdır.</span><span class="sxs-lookup"><span data-stu-id="fc398-110">By default, this message is a warning.</span></span> <span data-ttu-id="fc398-111">Uyarıları gizleme veya uyarıları hata olarak işleme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fc398-111">For more information about how to hide warnings or treat warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

<span data-ttu-id="fc398-112">**Hata kimliği:** BC42326</span><span class="sxs-lookup"><span data-stu-id="fc398-112">**Error ID:** BC42326</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="fc398-113">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="fc398-113">To correct this error</span></span>

<span data-ttu-id="fc398-114">Uyarıyı önlemek ve lambda ifadesini kaldırmak için lambda ifadesini bir değişkene atayın ve `AddHandler` `RemoveHandler` Aşağıdaki örnekte gösterildiği gibi değişkeni hem hem de deyimlerde kullanın.</span><span class="sxs-lookup"><span data-stu-id="fc398-114">To avoid the warning and remove the lambda expression, assign the lambda expression to a variable and use the variable in both the `AddHandler` and `RemoveHandler` statements, as shown in the following example.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fc398-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc398-115">See also</span></span>

- [<span data-ttu-id="fc398-116">Lambda Ifadeleri</span><span class="sxs-lookup"><span data-stu-id="fc398-116">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="fc398-117">Gevşek Temsilci Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="fc398-117">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="fc398-118">Olaylar</span><span class="sxs-lookup"><span data-stu-id="fc398-118">Events</span></span>](../../programming-guide/language-features/events/index.md)
