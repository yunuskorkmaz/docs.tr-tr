---
title: "Null-conditional İşleçleri (C# ve Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95b4079cf4e71c0ef9cd436ec230337f512229a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="null-conditional-operators-c-and-visual-basic"></a>Null-conditional İşleçleri (C# ve Visual Basic)
Null üye erişimi gerçekleştirmeden önce test etmek için kullanılan (`?.`) veya dizin (`?[`) işlemi.  Bu işleçleri özellikle veri yapılara azalan düzen için null işlemek için daha az kod denetler yazmanıza yardımcı olur.  
  
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
  
 Null koşul işleçleri short-circuiting son örnek gösterilmektedir.  Koşullu üye erişimi ve dizin işlemi zinciri tek bir işlemde null değeri döndürülürse, rest zincirinin yürütme durdurur.  İfadedeki daha düşük önceliğe sahip diğer işlemleri devam edin.  Örneğin, `E` ikinci satırında aşağıdaki yürütür ve `??` ve `==` işlemlerini yürütmek.  İlk satırdaki `??` kısa devreler ve `E` null olmayan için sol tarafındaki değerlendirirken, yürütmez.
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
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
  
 Açıkça çağırmanız gerekir `Invoke` yöntemi hiçbir null-conditional temsilci çağırma sözdizimi olduğundan `PropertyChanged?(e)`.  İzin vermek için çok fazla belirsiz ayrıştırma durumlarda vardı.  
  
## <a name="language-specifications"></a>Dil belirtimleri  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 Daha fazla bilgi için bkz: [Visual Basic dil başvurusu](../../../visual-basic/language-reference/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [?? (null birleşim işleci)](null-conditional-operator.md)  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Visual Basic Dil Başvurusu](../../../visual-basic/language-reference/index.md)  
 [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
