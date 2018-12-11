---
title: ^ = İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: cf39c8e8586e9d4f537fe38d8b28f55542db6ab8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237161"
---
# <a name="-operator-c-reference"></a>^= İşleci (C# Başvurusu)
Düzeyinde dışlamalı OR ataması işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade formu  
  
```csharp  
x ^= y  
```  
  
 olarak değerlendirilir  
  
```csharp  
x = x ^ y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [^ İşleci](../../../csharp/language-reference/operators/xor-operator.md) bir bit düzeyinde dışlamalı OR işlemi integral işlenenlerde ve mantıksal hariç veya üzerinde gerçekleştirir [bool](../../../csharp/language-reference/keywords/bool.md) işlenen.  
  
 ^ = İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [^ işleci](../../../csharp/language-reference/operators/xor-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
