---
title: '% İşleci (C# Başvurusu)'
ms.date: 04/04/2018
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
ms.openlocfilehash: 477f2491e6d2efe6b5c327efb371843d0bf12c26
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43723879"
---
# <a name="-operator-c-reference"></a>% İşleci (C# Başvurusu)
Kalan işleci (`%`) ilk işleneni kendi ikinci bölme işleminden kalanı hesaplar. Tüm sayısal türlerin kalan işleçleri önceden tanımlanmış. 
  
## <a name="remarks"></a>Açıklamalar  
 Formül `a % b` her zaman aralığı bir değer döndürür `(-b, b)`özel (hiçbir zaman geri dönebilirsiniz `b` veya `-b`), oturum bölünen sayının tutma. Tamsayı bölme için kalan işleci kural karşılayan `a % b = a - (a / b) * b`.
  
 Benzer bir kural belirtimini kurallı mod ile ancak floored bölme ve döndürür değerler aralığı ile karıştırılmamalıdır budur `[0, b)`. C# kurallı mod için bir işleç yok. Ancak, davranışı pozitif esin için aynıdır.
  
 Kullanıcı tanımlı türler aşırı yükleme `%` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a>Açıklamalar  
 Çift tür ile ilişkili yuvarlama hataları unutmayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
