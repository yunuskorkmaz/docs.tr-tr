---
title: '&gt;&gt;= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: f2bac6a4320980d80a9b6c2597dcf8dc6f08ac70
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748732"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= İşleci (C# Başvurusu)
Sağa kaydırma atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade formu  
  
```csharp  
x >>= y  
```  
  
 olarak değerlendirilir  
  
```csharp  
x = x >> y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [>> İşleci](../../../csharp/language-reference/operators/right-shift-operator.md) kaydırır `x` sağ tarafından belirtilen bir miktara göre `y`.  
  
 >> = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [>> işleci](../../../csharp/language-reference/operators/right-shift-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
