---
title: "&amp;= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bea90651faaafe7b754ce1cf16bddbab997d5f5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-c-reference"></a>&amp;= İşleci (C# Başvurusu)
AND atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanılarak `&=` atama işleci gibi  
  
```  
x &= y  
```  
  
 eşdeğerdir  
  
```  
x = x & y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [& İşleci](../../../csharp/language-reference/operators/and-operator.md) tam sayı işlenenler ve mantıksal ve bit düzeyinde mantıksal AND işlemini gerçekleştirir. `bool` işlenen.  
  
 `&=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler ikili aşırı yükleme [& işleci](../../../csharp/language-reference/operators/and-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#34](../../../csharp/language-reference/operators/codesnippet/CSharp/and-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)
