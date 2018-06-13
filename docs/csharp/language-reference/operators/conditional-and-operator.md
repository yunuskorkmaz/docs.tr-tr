---
title: '&amp;&amp; İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 15bb3e9702f04cc805af63767c7ecbfc68160368
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171921"
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; İşleci (C# Başvurusu)
Koşullu- ve işleci (`&&`) bir mantıksal gerçekleştirir- ve kendi `bool` işlenenler, ancak yalnızca kendi ikinci işlenen gerekirse değerlendirir.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlemi  
  
```csharp  
x && y  
```  
  
 işlemine karşılık gelir  
  
```csharp  
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
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
