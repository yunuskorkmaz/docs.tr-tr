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
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Handles tümcesi, içeren türde veya temel türlerinden birinde tanımlanan bir WithEvents değişkeni gerektirir.

@No__t_1 yan tümcesinde bir `WithEvents` değişkeni sağlamadınız. Yordam bildiriminin sonundaki `Handles` anahtar sözcüğü, `WithEvents` anahtar sözcüğü kullanılarak belirtilen bir nesne değişkeni tarafından oluşturulan olayları işlemesini sağlar.

**Hata kimliği:** BC30506

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Gerekli `WithEvents` değişkenini sağlayın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, <xref:System.Timers.Timer?displayProperty=nameWithType> örneğinin tanımında [WithEvents](../modifiers/withevents.md) anahtar sözcüğünün kullanılmadığından Visual Basic derleyici hatası `BC30506` oluşturur.

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

@No__t_0 değişkeni `WithEvents` anahtar sözcüğüyle tanımlandığından aşağıdaki örnek başarıyla derlenir:

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

- [İşlendiğini](../../../visual-basic/language-reference/statements/handles-clause.md)
