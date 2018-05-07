---
title: Null-conditional İşleçleri (C# ve Visual Basic)
ms.date: 04/03/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 8dde37c41ccd0b172bc9cd08abebec7777861f1c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. ve? [] null-conditional işleçleri (C# ve Visual Basic)
Null üye erişimi gerçekleştirmeden önce test etmek için kullanılan (`?.`) veya dizin (`?[]`) işlemi.  Bu işleçleri özellikle veri yapılara azalan düzen için null işlemek için daha az kod denetler yazmanıza yardımcı olur.  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 Null koşul işleçleri short-circuiting.  Koşullu üye erişimi ve dizin işlemi zinciri tek bir işlemde null değeri döndürülürse, rest zincirinin yürütme durdurur.  Aşağıdaki örnekte, `E` varsa yürütmez `A`, `B`, veya `C` null olarak değerlendirir.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 Null koşul üyesi erişim için başka bir kullanım temsilciler çok daha az kod ile iş parçacığı açısından güvenli şekilde çalıştırır.  Eski şekilde aşağıdaki gibi bir kod gerektirir:  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 Yeni yol çok daha kolaydır:  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 Derleyici değerlendirmek için kod oluşturur çünkü iş parçacığı yeni yoludur `PropertyChanged` sonucu geçici bir değişkende tutma yalnızca bir kez.  
  
 Açıkça çağırmanız gerekir `Invoke` yöntemi hiçbir null-conditional temsilci çağırma sözdizimi olduğundan `PropertyChanged?(e)`.  
  
## <a name="language-specifications"></a>Dil belirtimleri  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Daha fazla bilgi için bkz: [Visual Basic dil başvurusu](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [?? (null birleşim işleci)](null-conditional-operator.md)  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Visual Basic Dil Başvurusu](../../../visual-basic/language-reference/index.md)  
 [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
