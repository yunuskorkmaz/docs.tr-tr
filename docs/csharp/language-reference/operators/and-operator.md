---
title: "&amp;İşleci (C# Başvurusu)"
ms.date: 07/20/2015
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
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eceee8e01ba46f65c6b182a40d14e62aaba5dd53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a>&amp;İşleci (C# Başvurusu)
& İşleci bir birli ya da bir ikili işleç olarak işlev görebilir.  
  
## <a name="remarks"></a>Açıklamalar  
 Birli & işleci, işlenen adresini döndürür (gerektirir [güvensiz](../../../csharp/language-reference/keywords/unsafe.md) bağlam).  
  
 İkili & işleçleri tam sayı türleri için önceden tanımlanmış ve `bool`. İntegral için türleri & işlenenleri mantıksal bit düzeyinde AND hesaplar. İçin `bool` işlenenler & mantıksal hesaplar ve onun işlenenleri; diğer bir deyişle, sonuç `true` , her iki işlenen ve yalnızca, `true`.  
  
 `&` İşleci değerlendirir ilk bağımsız olarak her iki işleçler kılavuzuna değeri. Örneğin:  
  
 [!code-csharp[csRefOperators#37](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_1.cs)]  
  
 Kullanıcı tanımlı türler ikili aşırı yükleme `&` işleci (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Tam sayı türleri üzerinde işlemler genellikle numaralandırma üzerinde izin verilir. İkili İşleç aşırı, karşılık gelen atama işleci varsa, aynı zamanda örtük olarak aşırı yüklü değildir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#38](../../../csharp/language-reference/operators/codesnippet/CSharp/and-operator_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)
