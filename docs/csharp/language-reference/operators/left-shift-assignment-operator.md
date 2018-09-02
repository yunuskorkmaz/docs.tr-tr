---
title: '&lt;&lt;= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: c689aeccdf3ad6cc6c672cc101a4f0aa92f19791
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406980"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt;= İşleci (C# Başvurusu)
Sola kaydırma atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade formu  
  
```csharp  
x <<= y  
```  
  
 olarak değerlendirilir  
  
```csharp  
x = x << y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [<< İşleci](../../../csharp/language-reference/operators/left-shift-operator.md) kaydırır `x` tarafından belirtilen bit sayısı kadar sola `y`.  
  
 `<<=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [<< işleci](../../../csharp/language-reference/operators/left-shift-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
