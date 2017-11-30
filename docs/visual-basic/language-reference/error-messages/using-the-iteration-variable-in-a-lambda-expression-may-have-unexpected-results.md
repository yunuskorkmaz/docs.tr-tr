---
title: "Lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42324
- bc42324
helpviewer_keywords: BC42324
ms.assetid: b5c2c4bd-3b2a-4a73-aaeb-55728eb03b68
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fb707cd4e09a149d21b70bb0f998a40c7ed58b49
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-iteration-variable-in-a-lambda-expression-may-have-unexpected-results"></a>Lambda ifadesinde yineleme değişkeni kullanılması beklenmeyen sonuçlara neden olabilir
Lambda ifadesinde yineleme değişkeni kullanılması olabilir beklenmeyen sonuçlar. Bunun yerine, döngü içinde yerel bir değişken oluşturun ve yineleme değişkenin değerini atayın.  
  
 Döngünün içinde bildirilen bir lambda ifadesinde bir döngü yineleme değişkeni kullandığınızda, bu uyarı görüntülenir. Örneğin, aşağıdaki örnekte, görüntülenecek uyarı neden olur.  
  
```vb  
For i As Integer = 1 To 10  
    ' The warning is given for the use of i.  
    Dim exampleFunc As Func(Of Integer) = Function() i  
Next  
```  
  
 Aşağıdaki örnek, ortaya çıkabilecek beklenmeyen sonuçları gösterir.  
  
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
  
 `For` Döngü oluşturuyor döngü yineleme değişkenin değerini döndürür, her biri bir dizi lambda ifadeleri `i`. Ne zaman lambda ifadeleri değerlendirilir içinde `For Each` döngüsü 0, 1, 2, 3 ve 4 görüntülenen, art arda değerlerini görmeyi beklediğiniz `i` içinde `For` döngü. Bunun yerine, son değerini görmek `i` beş kez görüntülenir:  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 `5`  
  
 Varsayılan olarak, bu iletiyi bir uyarıdır. Uyarıları gizleme veya uyarıları hata olarak davranma hakkında daha fazla bilgi için bkz: [yapılandırma uyarılarını Visual Basic'te](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **Hata Kimliği:** BC42324  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
-   Yineleme değişkeninin değeri yerel bir değişkene atayın ve yerel değişken lambda ifadesinde kullanın.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Lambda ifadeleri](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
