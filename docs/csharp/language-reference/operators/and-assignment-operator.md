---
title: '&amp;= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: f3a6fe20ca89a90b5a64118d73fb39e9a364d1e9
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933958"
---
# <a name="amp-operator-c-reference"></a>&amp;= İşleci (C# Başvurusu)
AND atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanarak `&=` atama işleci gibi  
  
```csharp  
x &= y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x & y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [& İşleci](../../../csharp/language-reference/operators/and-operator.md) integral işlenen ve mantıksal AND bit düzeyinde bir mantıksal ve işlem gerçekleştiren `bool` işlenen.  
  
 `&=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler ikili aşırı yükleme [& işleci](../../../csharp/language-reference/operators/and-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
