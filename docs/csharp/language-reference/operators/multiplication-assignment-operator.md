---
title: '* = İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: f8604cdadeda14a5761bc923bd966186fd258a6d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245356"
---
# <a name="-operator-c-reference"></a>*= İşleci (C# Başvurusu)
İkili çarpma atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanarak `*=` atama işleci gibi  
  
```csharp  
x *= y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x * y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [* İşleci](../../../csharp/language-reference/operators/multiplication-operator.md) çarpma işlemi gerçekleştirmek sayısal türleri için önceden tanımlanmış.  
  
 `*=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [* işleci](../../../csharp/language-reference/operators/multiplication-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
