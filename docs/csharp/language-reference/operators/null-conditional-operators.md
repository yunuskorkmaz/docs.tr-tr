---
title: Null koşullu işleçleri - C# başvurusu
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 4189b07fd280192a4cb39400e4e77cef702c9d08
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239559"
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

Daha fazla bilgi için [Null koşullu işleci](~/_csharplang/spec/expressions.md#null-conditional-operator) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca Bkz.

- [?? (null birleşim işleci)](null-coalescing-operator.md)  
- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
