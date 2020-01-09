---
title: NameOf işleci
description: Visual Basic ' de NameOf işlecinin nasıl kullanılacağını öğrenin
ms.date: 10/27/2019
helpviewer_keywords:
- NameOf operator [Visual Basic]
ms.openlocfilehash: e7dd55bfd98b34449b9f1a35375198598f57b46f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347015"
---
# <a name="nameof-operator---visual-basic"></a>NameOf işleci-Visual Basic

`NameOf` işleci, dize sabiti olarak bir değişkenin, türün veya üyenin adını edinir:

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

`NameOf` işleci derleme zamanında değerlendirilir ve çalışma zamanında hiçbir etkiye sahip değildir.

Bağımsız değişken denetim kodunu daha sürdürülebilir hale getirmek için `NameOf` işlecini kullanabilirsiniz:

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

`NameOf` işleci Visual Basic 14 ve üzeri sürümlerde kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Dili Başvurusu](../index.md)
- [İşleçler (Visual Basic)](index.md)
