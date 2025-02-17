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
# <a name="bc30506-handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>BC30506: Handles yan tümcesi, içeren türde veya temel türlerinden birinde tanımlanan bir WithEvents değişkeni gerektirir

`WithEvents`Yan tümcesine bir değişken sağlamadınız `Handles` . `Handles`Yordam bildiriminin sonundaki anahtar sözcüğü, anahtar sözcüğü kullanılarak belirtilen bir nesne değişkeni tarafından oluşturulan olayları işlemesini sağlar `WithEvents` .

**Hata kimliği:** BC30506

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Gerekli değişkeni sağlayın `WithEvents` .

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `BC30506` örnek tanımında [WithEvents](../modifiers/withevents.md) anahtar sözcüğü kullanılmadığından Visual Basic derleyici hatası oluşturuyor <xref:System.Timers.Timer?displayProperty=nameWithType> .

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

Aşağıdaki örnek, `_timer1` değişkeni anahtar sözcüğüyle tanımlandığından başarıyla derlenir `WithEvents` :

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

## <a name="see-also"></a>Ayrıca bkz.

- [Handles](../statements/handles-clause.md)
