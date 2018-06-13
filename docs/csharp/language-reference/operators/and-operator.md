---
title: '&amp; İşleci (C# Başvurusu)'
ms.date: 04/04/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 59813b4bc5781776c9f9741c3e49e660c684bff9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267886"
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
