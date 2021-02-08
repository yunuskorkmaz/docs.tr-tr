---
description: 'Hakkında daha fazla bilgi edinin: BC30506: Handles yan tümcesi, içeren türde veya temel türlerinden birinde tanımlanan bir WithEvents değişkeni gerektirir'
title: Handles tümcesi, içeren türde veya temel türlerinden birinde tanımlanan bir WithEvents değişkeni gerektirir.
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 7253a4766b2015ccbe0ae62f64bc10aaca073dc3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796125"
---
# <a name="bc30506-handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a><span data-ttu-id="48d5e-103">BC30506: Handles yan tümcesi, içeren türde veya temel türlerinden birinde tanımlanan bir WithEvents değişkeni gerektirir</span><span class="sxs-lookup"><span data-stu-id="48d5e-103">BC30506: Handles clause requires a WithEvents variable defined in the containing type or one of its base types</span></span>

<span data-ttu-id="48d5e-104">`WithEvents`Yan tümcesine bir değişken sağlamadınız `Handles` .</span><span class="sxs-lookup"><span data-stu-id="48d5e-104">You did not supply a `WithEvents` variable in your `Handles` clause.</span></span> <span data-ttu-id="48d5e-105">`Handles`Yordam bildiriminin sonundaki anahtar sözcüğü, anahtar sözcüğü kullanılarak belirtilen bir nesne değişkeni tarafından oluşturulan olayları işlemesini sağlar `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="48d5e-105">The `Handles` keyword at the end of a procedure declaration causes it to handle events raised by an object variable declared using the `WithEvents` keyword.</span></span>

<span data-ttu-id="48d5e-106">**Hata kimliği:** BC30506</span><span class="sxs-lookup"><span data-stu-id="48d5e-106">**Error ID:** BC30506</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="48d5e-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="48d5e-107">To correct this error</span></span>

<span data-ttu-id="48d5e-108">Gerekli değişkeni sağlayın `WithEvents` .</span><span class="sxs-lookup"><span data-stu-id="48d5e-108">Supply the necessary `WithEvents` variable.</span></span>

## <a name="example"></a><span data-ttu-id="48d5e-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="48d5e-109">Example</span></span>

<span data-ttu-id="48d5e-110">Aşağıdaki örnekte, `BC30506` örnek tanımında [WithEvents](../modifiers/withevents.md) anahtar sözcüğü kullanılmadığından Visual Basic derleyici hatası oluşturuyor <xref:System.Timers.Timer?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="48d5e-110">In the following example, Visual Basic generates compiler error `BC30506` because the [WithEvents](../modifiers/withevents.md) keyword is not used in the definition of the <xref:System.Timers.Timer?displayProperty=nameWithType> instance.</span></span>

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

<span data-ttu-id="48d5e-111">Aşağıdaki örnek, `_timer1` değişkeni anahtar sözcüğüyle tanımlandığından başarıyla derlenir `WithEvents` :</span><span class="sxs-lookup"><span data-stu-id="48d5e-111">The following example compiles successfully because the `_timer1` variable is defined with the `WithEvents` keyword:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="48d5e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48d5e-112">See also</span></span>

- [<span data-ttu-id="48d5e-113">Handles</span><span class="sxs-lookup"><span data-stu-id="48d5e-113">Handles</span></span>](../statements/handles-clause.md)
