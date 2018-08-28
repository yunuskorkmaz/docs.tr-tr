---
title: '&amp;&amp; İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 459b791fde3e4d3940dbd3d916f940e81f365da6
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999736"
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; İşleci (C# Başvurusu)
Koşullu- ve işleci (`&&`) gerçekleştiren bir mantıksal- ve kendi `bool` işlenenler, ancak yalnızca gerekli olduğunda ikinci işleneni değerlendirir.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlemi  
  
```csharp  
x && y  
```  
  
 işlemine karşılık gelir  
  
```csharp  
x & y  
```  
  
 dışındaki olması durumunda `x` olduğu `false`, `y` ve işlemin sonucu olduğundan, değerlendirilmez `false` hangi değeri ne olursa olsun `y` olduğu. Bu, "kısa devre değerlendirmesi gibi" adı verilir.  
  
 Koşullu- ve işleci aşırı yüklenmiş, olamaz, ancak normal mantıksal işleçler aşırı yüklemeleri ve işleçleri [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md) belirli kısıtlamalar ile de aşırı yüklemeleri olarak kabul edilir Koşullu mantıksal işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, ikinci bir koşullu ifade `if` deyimi değerlendirir yalnızca ilk işlenen işlenen döndürüldüğünden `false`.  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
