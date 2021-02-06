---
description: 'Hakkında daha fazla bilgi edinin: BC42324: bir lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir'
title: Lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: a21e33c9a8737642d4d0764e92b1fbb2213f9602
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99640881"
---
# <a name="bc42324-using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>BC42324: bir lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir

Lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir. Bunun yerine, döngü içinde bir yerel değişken oluşturun ve bunu yineleme değişkeninin değerine atayın.

 Bu uyarı, döngü içinde belirtilen bir lambda ifadesinde bir döngü yineleme değişkeni kullandığınızda görüntülenir. Örneğin, aşağıdaki örnek uyarının görünmesine neden olur.

```vb
For i As Integer = 1 To 10
    ' The warning is given for the use of i.
    Dim exampleFunc As Func(Of Integer) = Function() i
Next
```

 Aşağıdaki örnek, gerçekleşebilecek beklenmeyen sonuçları gösterir.

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            array1(i) = Function() i
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

 `For`Döngü, her biri döngü yineleme değişkeninin değerini döndüren bir lambda ifadeleri dizisi oluşturur `i` . Lambda ifadeleri `For Each` döngüde değerlendirildiğinde, döngüde art arda gelen değerleri 0, 1, 2, 3 ve 4 ' ü görmeyi bekleyebilir `i` `For` . Bunun yerine, en son `i` beş kez görüntülenmiş değeri görürsünüz:

 `5`

 `5`

 `5`

 `5`

 `5`

 Bu ileti, varsayılan olarak bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirme hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).

 **Hata kimliği:** BC42324

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

- Yineleme değişkeninin değerini yerel bir değişkene atayın ve yerel değişkeni lambda ifadesinde kullanın.

```vb
Module Module1
    Sub Main()
        Dim array1 As Func(Of Integer)() = New Func(Of Integer)(4) {}

        For i As Integer = 0 To 4
            Dim j = i
            array1(i) = Function() j
        Next

        For Each funcElement In array1
            System.Console.WriteLine(funcElement())
        Next

    End Sub
End Module
```

## <a name="see-also"></a>Ayrıca bkz.

- [Lambda Ifadeleri](../../programming-guide/language-features/procedures/lambda-expressions.md)
