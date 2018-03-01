---
title: "&amp;&amp;İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16bc2fa650031d2b1f6cfaf7d128ba487963f707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp;İşleci (C# Başvurusu)
Koşullu- ve işleci (`&&`) bir mantıksal gerçekleştirir- ve kendi `bool` işlenenler, ancak yalnızca kendi ikinci işlenen gerekirse değerlendirir.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlemi  
  
```  
x && y  
```  
  
 işlemine karşılık gelir  
  
```  
x & y  
```  
  
 dışındaki olması durumunda `x` olan `false`, `y` ve işleminin sonucu olduğundan, değerlendirilmez `false` hangi değerini olsun `y` değil. Bu "değerlendirmesi"olarak bilinir.  
  
 Koşullu- ve işleci aşırı yüklenmiş, olamaz, ancak normal mantıksal işleçleri aşırı ve işleçleri [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md) bazı kısıtlamalar ile de aşırı olarak kabul edilir Koşullu mantıksal işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, koşullu ifade ikinci `if` deyimi değerlendirir yalnızca ilk işlenen işleneni döndürdüğünden `false`.  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)
