---
title: "|| İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b95fd162c9a89789e1970b32473c8acf16ba5cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [C# işleçleri](../../../csharp/language-reference/operators/index.md)
