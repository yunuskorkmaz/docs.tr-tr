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
ms.openlocfilehash: b257c7d41618464e26ab3b54bcfb1f1e2c2e420e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467380"
---
# <a name="amp-operator-c-reference"></a>&amp; İşleci (C# Başvurusu)
`&` İşleci bir birli veya ikili işleç olarak işlev görebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Birli `&` işleci, işlenenin adresini verir (gerektirir [güvenli](../../../csharp/language-reference/keywords/unsafe.md) bağlamı).  
  
 İkili `&` işleçleri tamsayı türleri için önceden tanımlanmış ve `bool`. İçin tam sayı türleri & mantıksal bit seviyesinde ve işlenenleri hesaplar. İçin `bool` işlenenler & mantıksal hesaplar ve işlenenleri; diğer bir deyişle, sonuç `true` , her iki işlenen ve yalnızca, `true`.  
  
 İkili `&` işleci, birinci bağımsız olarak her iki işlenen değerlendirilir değerini, buna için [koşullu AND işleci](../../../csharp/language-reference/operators/conditional-and-operator.md) `&&`. Örneğin:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Kullanıcı tanımlı türler ikili aşırı yükleme `&` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Tamsayı türlerinde işlemler genellikle numaralandırma üzerinde izin verilir. İkili İşleç aşırı karşılık gelen atama işleci, varsa, aynı zamanda örtük olarak aşırı yüklenmiş olur.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
