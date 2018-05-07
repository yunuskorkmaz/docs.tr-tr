---
title: '|| İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: ce0834874f9c5b4c5154a798492600d6ac45a4c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>|| İşleci (C# Başvurusu)
Koşullu-OR işleci (`||`) bir mantıksal-OR, gerçekleştirir, `bool` işlenen. İlk işlenen değerlendirilirse `true`, ikinci işlenen hesaplanan değil. İlk işlenen değerlendirilirse `false`, ikinci işleci veya ifadesi bir bütün olarak değerlendiren olup olmadığını belirler `true` veya `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlemi  
  
```  
x || y  
```  
  
 işlemine karşılık gelir  
  
```  
x | y  
```  
  
 dışındaki olması durumunda `x` olan `true`, `y` veya işlemi olduğundan değerlendirilmez `true` değerini bakılmaksızın `y`. Bu kavram "değerlendirmesi"olarak bilinir.  
  
 Koşullu-OR işleci, normal mantıksal işleçleri aşırı aşırı yüklenemez ve [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md) işleçleri bazı kısıtlamalar ile de değerlendirilir aşırı olmalıdır Koşullu mantıksal işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, ifade kullanan `||` yalnızca ilk işlenen değerlendirir. Kullanan deyimi `|` her iki işlenen değerlendirir. Her iki işlenen değerlendirildiğinde ikinci örnekte, bir çalışma zamanı özel durumu oluşur.  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
