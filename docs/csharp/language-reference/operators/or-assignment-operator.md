---
title: '|= İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: fe56005ce94656b5e8a075cddfb91dc0da096cf7
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929920"
---
# <a name="-operator-c-reference"></a>|= İşleci (C# Başvurusu)
OR atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanarak `|=` atama işleci gibi  
  
```csharp  
x |= y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x | y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [ &#124; İşleci](../../../csharp/language-reference/operators/or-operator.md) bool işlenenlerde integral işlenen üzerinde bit düzeyinde bir mantıksal OR işlem ve mantıksal OR gerçekleştirir.  
  
 `|=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [ &#124; işleci](../../../csharp/language-reference/operators/or-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
