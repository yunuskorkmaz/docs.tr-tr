---
title: '&amp; İşleci (C# Başvurusu)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f26305bfa1e8c9ba45493ad2ab4937d554590911
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="amp-operator-c-reference"></a>&amp; İşleci (C# Başvurusu)
`&` İşleci bir birli ya da bir ikili işleç olarak işlev görebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Birli `&` işleci, kendi işleneni adresini döndürür (gerektirir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlam).  
  
 İkili `&` işleçleri tam sayı türleri için önceden tanımlanmış ve `bool`. İntegral için türleri & işlenenleri mantıksal bit düzeyinde AND hesaplar. İçin `bool` işlenenler & mantıksal hesaplar ve onun işlenenleri; diğer bir deyişle, sonuç `true` , her iki işlenen ve yalnızca, `true`.  
  
 İkili `&` işleci değerlendirir ilk bağımsız olarak her iki işleçler kılavuzuna değerini, buna karşılık [koşullu AND işleci](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`. Örneğin:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Kullanıcı tanımlı türler ikili aşırı yükleme `&` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir. İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
