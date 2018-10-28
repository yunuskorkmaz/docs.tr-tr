---
title: Null koşullu işleçleri (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: c29362a1e335e18b66821919e266b1ce57774692
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195981"
---
# <a name="-and--null-conditional-operators-visual-basic"></a>?. ve? () null koşullu işleçleri (Visual Basic)

Sol işlenen null değerini test eder (`Nothing`) üye erişimi gerçekleştirmeden önce (`?.`) ya da dizin (`?()`) döndürür; işlem `Nothing` sol işlenen değerlendirilirse `Nothing`. Değer türleri normalde döndürecekti ifadelerinde null koşullu işleci döndürdüğünü unutmayın bir <xref:System.Nullable%601>.

Bu işleçler null denetimleri, özellikle veri yapılarda azalan zaman işlemek için daha az kod yazmanıza yardımcı olur. Örneğin:

```vb
Dim length As Integer? = customers?.Length  ' Nothing if customers is Nothing  
Dim first As Customer = customers?(0)  ' Nothing if customers is Nothing  
Dim count As Integer? = customers?(0)?.Orders?.Count()  ' Nothing if customers, the first customer, or Orders is Nothing  
```

Karşılaştırma için ilk kez bir null koşullu işleci olmadan bu ifadelerin alternatif koddur:

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

Null koşullu işleçleri short-circuiting.  Koşullu üye erişimi ve dizin işlemlerini zincirinin tek bir işlemde bir şey döndürürse, rest zincirinin yürütme durdurur.  Aşağıdaki örnekte, C(E) değilse değerlendirilmez `A`, `B`, veya `C` Nothing olarak değerlendirilir.

```vb
A?.B?.C?(E);
```

Başka bir null koşullu üye erişimi için temsilciler çok daha az kod ile iş parçacığı güvenli bir şekilde çağırmak için kullanılır.  Kod aşağıdaki gibi eski yöntem gerektirir:  

```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```

Yeni yolu çok daha kolaydır:  

```vb
PropertyChanged?.Invoke(…)
```

Derleyici değerlendirmek için kod oluşturur çünkü iş parçacığı açısından güvenli yeni yoludur `PropertyChanged` sonucu geçici bir değişkende tutma yalnızca bir kez. Açıkça çağırmak ihtiyacınız `Invoke` yöntemi hiçbir null koşullu temsilci çağırma söz dizimi olduğundan `PropertyChanged?(e)`.  

## <a name="see-also"></a>Ayrıca bkz.

- [İşleçler (Visual Basic)](index.md)
- [Visual Basic programlama kılavuzu](../../../visual-basic/programming-guide/index.md)
- [Visual Basic Dili Başvurusu](../../../visual-basic/language-reference/index.md)  
