---
title: '% İşleci (C# Başvurusu)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 796b4a40347fc5881db27a8a8a28404c7c4e8c5b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a>% İşleci (C# Başvurusu)
Kalan işleci (`%`) ilk işlenen kendi ikinciye bölmenin sonra kalanı hesaplar. Tüm sayısal türler kalan işleçleri önceden. 
  
## <a name="remarks"></a>Açıklamalar  
 Formül `a % b` her zaman aralığı bir değer döndürür `(-b, b)`, özel (hiçbir zaman dönebilirsiniz `b` veya `-b`), bölünen oturum tutma. Tamsayı bölme için kalan işleci kural karşılayan `a % b = a - (a / b) * b`.
  
 Benzer bir kural karşılayan kurallı mod ile ancak aralıkta floored bölme ve döndürür değerleri karıştırılmamalıdır budur `[0, b)`. C# kurallı modül için bir işleç yok. Ancak, davranışı pozitif yararınıza olur; aynıdır.
  
 Kullanıcı tanımlı türler aşırı yükleme `%` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a>Açıklamalar  
 Çift türüyle ilişkili yuvarlama hataları not alın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
