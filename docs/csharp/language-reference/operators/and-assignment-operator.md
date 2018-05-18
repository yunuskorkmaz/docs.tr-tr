---
title: '&amp;= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 092f46ddd8ca52e2d705200768c93a3473f1520f
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="amp-operator-c-reference"></a>&amp;= İşleci (C# Başvurusu)
AND atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanılarak `&=` atama işleci gibi  
  
```csharp  
x &= y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x & y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [& İşleci](../../../csharp/language-reference/operators/and-operator.md) tam sayı işlenenler ve mantıksal ve bit düzeyinde mantıksal AND işlemini gerçekleştirir. `bool` işlenen.  
  
 `&=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler ikili aşırı yükleme [& işleci](../../../csharp/language-reference/operators/and-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
