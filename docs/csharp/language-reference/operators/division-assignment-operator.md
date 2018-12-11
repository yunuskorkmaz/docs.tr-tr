---
title: / = İşleci - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 0487088fa5420f2d15541aa3f7b1d4ec604195bb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241252"
---
# <a name="-operator-c-reference"></a>/= İşleci (C# Başvurusu)
Bölme atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanarak `/=` atama işleci gibi  
  
```csharp  
x /= y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x / y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [/ İşleci](../../../csharp/language-reference/operators/division-operator.md) bölme gerçekleştirmek sayısal türleri için önceden tanımlanmış.  
  
 `/=` İşleci aşırı yüklenemez doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [/ işleci](../../../csharp/language-reference/operators/division-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Tüm bileşik atama işleçlerini, örtük olarak ikili İşleç aşırı yüklemesi, eşdeğer bileşik atama aşırı.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
