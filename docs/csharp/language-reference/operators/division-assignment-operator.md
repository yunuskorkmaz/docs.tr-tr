---
title: /= İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: c31ff374e6af4c08c329a971fdd8af169e239395
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171628"
---
# <a name="-operator-c-reference"></a>/= İşleci (C# Başvurusu)
Bölme atama işleci.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir ifade kullanılarak `/=` atama işleci gibi  
  
```csharp  
x /= y  
```  
  
 eşdeğerdir  
  
```csharp  
x = x / y  
```  
  
 dışında `x` yalnızca bir kez değerlendirilir. [/ İşleci](../../../csharp/language-reference/operators/division-operator.md) bölme gerçekleştirmek sayısal türler için önceden tanımlanmış.  
  
 `/=` İşleci olamaz aşırı yüklenebilir doğrudan, ancak kullanıcı tanımlı türler aşırı yükleme [/ işleci](../../../csharp/language-reference/operators/division-operator.md) (bkz [işleci](../../../csharp/language-reference/keywords/operator.md)). Tüm bileşik atama işleçleri üzerinde örtük olarak ikili İşleç aşırı yüklemesi eşdeğer bileşik atama overloads.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
