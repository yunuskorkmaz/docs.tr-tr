---
title: Null koşullu işleçleri (C# Başvurusu)
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 823b9dc886bf2448ca9da4ac640bfe56f90d3ff3
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194858"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. ve? [] null koşullu işleçleri (C# ve Visual Basic)
Üye erişimi gerçekleştirmeden önce sol işleneni null değerini test eder (`?.`) ya da dizin (`?[]`) döndürür; işlem `null` sol işlenen değerlendirilirse `null`. 

Bu işleçler null işlemek için daha az kod denetler, özellikle azalan düzende veri yapılarda yazmanıza yardımcı olur.  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
 Null koşullu işleçleri short-circuiting.  Null koşullu üye erişimi ve dizin işlemlerini zincirinin tek bir işlemde döndürürse, rest zincirinin yürütme durdurur.  Aşağıdaki örnekte, `E` değilse yürütülmez `A`, `B`, veya `C` null olarak değerlendirir.
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

 Null koşullu üye erişimi için başka bir kullanım temsilciler çok daha az kod ile iş parçacığı güvenli bir şekilde çalıştırır.  Kod aşağıdaki gibi eski yöntem gerektirir:  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
  
 Yeni yolu çok daha kolaydır:  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

 Derleyici değerlendirmek için kod oluşturur çünkü iş parçacığı açısından güvenli yeni yoludur `PropertyChanged` sonucu geçici bir değişkende tutma yalnızca bir kez. Açıkça çağırmak ihtiyacınız `Invoke` yöntemi hiçbir null koşullu temsilci çağırma söz dizimi olduğundan `PropertyChanged?(e)`.  
  
## <a name="language-specifications"></a>Dil özellikleri  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [?? (null birleşim işleci)](null-coalescing-operator.md)  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
