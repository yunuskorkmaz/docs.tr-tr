---
title: Handles tümcesi, içeren türde veya temel türlerinden birinde tanımlanan bir WithEvents değişkeni gerektirir.
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 191415408f607d0ff768e50c41fa9b3c4405a688
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582820"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="bd9d4-102">Handles tümcesi, içeren türde veya temel türlerinden birinde tanımlanan bir WithEvents değişkeni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="bd9d4-102">Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>

<span data-ttu-id="bd9d4-103">@No__t_1 yan tümcesinde bir `WithEvents` değişkeni sağlamadınız.</span><span class="sxs-lookup"><span data-stu-id="bd9d4-103">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="bd9d4-104">Yordam bildiriminin sonundaki `Handles` anahtar sözcüğü, `WithEvents` anahtar sözcüğü kullanılarak belirtilen bir nesne değişkeni tarafından oluşturulan olayları işlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd9d4-104">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>

<span data-ttu-id="bd9d4-105">**Hata kimliği:** BC30506</span><span class="sxs-lookup"><span data-stu-id="bd9d4-105">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="bd9d4-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="bd9d4-106">To correct this error</span></span>

<span data-ttu-id="bd9d4-107">Gerekli `WithEvents` değişkenini sağlayın.</span><span class="sxs-lookup"><span data-stu-id="bd9d4-107">Supply the necessary `WithEvents` variable.</span></span>

## <a name="example"></a><span data-ttu-id="bd9d4-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd9d4-108">Example</span></span>

<span data-ttu-id="bd9d4-109">Aşağıdaki örnekte, <xref:System.Timers.Timer?displayProperty=nameWithType> örneğinin tanımında [WithEvents](../modifiers/withevents.md) anahtar sözcüğünün kullanılmadığından Visual Basic derleyici hatası `BC30506` oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bd9d4-109">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

```vb
Imports System.Timers

Module Module1
    Private _timer1 As New Timer() With {.Interval = 1000, .Enabled = True}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub
End Module
```

<span data-ttu-id="bd9d4-110">@No__t_0 değişkeni `WithEvents` anahtar sözcüğüyle tanımlandığından aşağıdaki örnek başarıyla derlenir:</span><span class="sxs-lookup"><span data-stu-id="bd9d4-110">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

```vb
Imports System.Timers

Module Module1
    Private WithEvents _timer1 As New Timer() With {.Interval = 1000}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub

End Module
```

## <a name="see-also"></a><span data-ttu-id="bd9d4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bd9d4-111">See also</span></span>

- [<span data-ttu-id="bd9d4-112">İşlendiğini</span><span class="sxs-lookup"><span data-stu-id="bd9d4-112">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
