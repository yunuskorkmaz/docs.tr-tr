---
title: '%= İşleci (C# Başvurusu)'
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: 009c162b13fab05ba349d0535fe8dfae206502f3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507943"
---
# <a name="-operator-c-reference"></a>%= İşleci (C# Başvurusu)
Kalan atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanarak `%=` atama işleci gibi  
  
```csharp  
x %= y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x % y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [% İşleci](../../../csharp/language-reference/operators/remainder-operator.md) bölme işleminden kalanı hesaplamak sayısal türleri için önceden tanımlanmış.  
  
 `%=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [% işleci](../../../csharp/language-reference/operators/remainder-operator.md) (bkz [işleci (C# Başvurusu)](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
