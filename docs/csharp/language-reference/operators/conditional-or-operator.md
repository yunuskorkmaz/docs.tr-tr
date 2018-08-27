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
ms.openlocfilehash: 58e5fd72a3748e7af0894093fc461c4efb543608
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925546"
---
# <a name="-operator-c-reference"></a>|| İşleci (C# Başvurusu)
Koşullu-OR işleci (`||`) bir mantıksal OR gerçekleştirir, `bool` işlenen. Birinci işlenenin değerlendirilirse `true`, ikinci işlenenin değerlendirilmez. Birinci işlenenin değerlendirilirse `false`, ikinci işleç veya ifadenin bir bütün olarak değerlendirdiği olup olmadığını belirler. `true` veya `false`.  
  
## <a name="remarks"></a>Açıklamalar  
 İşlemi  
  
```csharp  
x || y  
```  
  
 işlemine karşılık gelir  
  
```csharp  
x | y  
```  
  
 dışındaki olması durumunda `x` olduğu `true`, `y` veya işlemi olduğundan değerlendirilmez `true` değerinden bağımsız olarak `y`. Bu kavram, "kısa devre değerlendirmesi gibi" adı verilir.  
  
 Koşullu-OR işleci, normal mantıksal işleçler aşırı aşırı yüklenemez ve [true](../../../csharp/language-reference/keywords/true.md) ve [false](../../../csharp/language-reference/keywords/false.md) işleçleri bazı kısıtlamalar ile ayrıca değerlendirilir aşırı olması Koşullu mantıksal işleçler.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örneklerde, ifade kullanan `||` yalnızca ilk işlenen değerlendirilir. Kullanan ifade `|` her iki işlenen değerlendirilir. Her iki işlenen değerlendirilir ikinci örnekte, bir çalışma zamanı özel durum ortaya çıkar.  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [C# İşleçleri](../../../csharp/language-reference/operators/index.md)
