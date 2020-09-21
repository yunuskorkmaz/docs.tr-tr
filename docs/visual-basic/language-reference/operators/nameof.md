---
title: NameOf işleci
description: Visual Basic ' de NameOf işlecinin nasıl kullanılacağını öğrenin
ms.date: 10/27/2019
f1_keywords:
- NameOf
- vb.NameOf
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: 0e72c4cb0c10113e53067ea4a743ca5ee77bcc95
ms.sourcegitcommit: 43ed174f085840ca18a791dc89fe833174da766d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90828909"
---
# <a name="nameof-operator---visual-basic"></a>NameOf işleci-Visual Basic

`NameOf`İşleci, dize sabiti olarak bir değişkenin, türün veya üyenin adını edinir:

```vb
Console.WriteLine(NameOf(System.Collections.Generic))  ' output: Generic
Console.WriteLine(NameOf(List(Of Integer)))  ' output: List
Console.WriteLine(NameOf(List(Of Integer).Count))  ' output: Count
Console.WriteLine(NameOf(List(Of Integer).Add))  ' output: Add

Dim numbers As New List(Of Integer) From { 1, 2, 3 }
Console.WriteLine(NameOf(numbers))  ' output: numbers
Console.WriteLine(NameOf(numbers.Count))  ' output: Count
Console.WriteLine(NameOf(numbers.Add))  ' output: Add
```

Yukarıdaki örnekte gösterildiği gibi, bir tür ve ad alanı durumunda, oluşturulan ad genellikle [tam olarak nitelenir](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

`NameOf`İşleci derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkiye sahip değildir.

`NameOf`Bağımsız değişken denetleme kodunun daha sürdürülebilir olması için işlecini kullanabilirsiniz:

```vb
Private _name As String

Public Property Name As String
    Get
        Return _name
    End Get
    Set
        If value Is Nothing Then
            Throw New ArgumentNullException(NameOf(value), $"{NameOf(name)} cannot be null.")
        End If
    End Set
End Property
```

`NameOf`İşleci Visual Basic 14 ve üzeri sürümlerde kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic dil başvurusu](../index.md)
- [İşleçler (Visual Basic)](index.md)
