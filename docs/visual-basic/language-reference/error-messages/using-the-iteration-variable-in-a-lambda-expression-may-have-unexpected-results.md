---
title: Lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir
ms.date: 07/20/2015
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords:
- BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
ms.openlocfilehash: 358c7a988ae95c2326a26bc048f5436e11acb340
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54641596"
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>Lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir
Sahip bir lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden. Bunun yerine, döngü içinde yerel bir değişken oluşturun ve yineleme değişkeninin değerini atayın.  
  
 Döngünün içinde bildirilen bir lambda ifadesinde bir döngü yineleme değişkeni kullandığınızda, bu uyarı görüntülenir. Örneğin, aşağıdaki örnekte görünecek uyarısına neden olur.  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 Aşağıdaki örnek, oluşabilecek beklenmeyen sonuçları gösterilmektedir.  
  
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
  
 `For` Döngü oluşturuyor döngüsünün yineleme değişkeni değerini döndürür, her biri bir dizi lambda ifadeleri `i`. Ne zaman lambda ifadeleri değerlendirilir `For Each` döngü beklediğiniz 0, 1, 2, 3 ve 4 görüntülenen art arda gelen değerlerini görmek `i` içinde `For` döngü. Bunun yerine, son değeri gördüğünüz `i` beş kez görüntülenir:  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak değerlendirmesini hakkında daha fazla bilgi için bkz. [Visual Basic'teki uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42324  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Yineleme değişkeninin değeri yerel bir değişkene atayın ve lambda ifadesinde yerel değişkenini kullanın.  
  
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
- [Lambda İfadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
