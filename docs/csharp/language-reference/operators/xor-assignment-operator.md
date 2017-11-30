---
title: "^= İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: ^=_CSharpKeyword
helpviewer_keywords: ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>^= İşleci (C# Başvurusu)
Dışlayan OR atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Formun bir ifade  
  
```  
x ^= y  
```  
  
 olarak değerlendirilir  
  
```  
x = x ^ y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [^ İşleci](../../../csharp/language-reference/operators/xor-operator.md) bir bit düzeyinde özel OR işlemi tam sayı işlenenler ve mantıksal hariç veya üzerinde gerçekleştirir [bool](../../../csharp/language-reference/keywords/bool.md) işlenen.  
  
 ^ = İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [^ işleci](../../../csharp/language-reference/operators/xor-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)
