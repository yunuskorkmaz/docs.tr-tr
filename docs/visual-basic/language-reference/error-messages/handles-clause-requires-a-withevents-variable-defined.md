---
title: Handles tümcesi, içeren türde veya temel türlerinden birinde tanımlanan bir WithEvents değişkeni gerektirir.
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 04c94d3d32660d1a186a9bb377c49a53e1451be6
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512739"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Handles tümcesi, içeren türde veya temel türlerinden birinde tanımlanan bir WithEvents değişkeni gerektirir.
`Handles` Yan tümcesine bir `WithEvents` değişken sağlamadınız. Yordam bildiriminin sonundaki `WithEvents` anahtar sözcüğü, anahtar sözcüğü kullanılarak belirtilen bir nesne değişkeni tarafından oluşturulan olayları işlemesini sağlar. `Handles`
  
 **Hata KIMLIĞI:** BC30506

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için
  
- Gerekli `WithEvents` değişkeni sağlayın.
  
## <a name="example"></a>Örnek

Aşağıdaki örnekte, <xref:System.Timers.Timer?displayProperty=nameWithType> örnek tanımında [WithEvents](../modifiers/withevents.md) anahtar sözcüğü kullanılmadığından `BC30506` Visual Basic derleyici hatası oluşturuyor.

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

Aşağıdaki örnek, `_timer1` değişkeni `WithEvents` anahtar sözcüğüyle tanımlandığından başarıyla derlenir:

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
