---
title: var (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ab49a4f4fcbc990a1fd21139397d70fa9fbf5dd8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735643"
---
# <a name="var-c-reference"></a>var (C# Başvurusu)
Visual C# 3.0 içinde başlayarak, yöntem kapsamda bildirilen değişkenler örtük bir "type" olabilir `var`. Bir türü örtük olarak belirlenmiş yerel değişken alacağı yalnızca kendiniz türü bildirilen, ancak derleyicinin türü belirler kesin. Aşağıdaki iki bildirimlerini `i` işlevsel olarak eşdeğerdir:  
  
```csharp  
var i = 10; // Implicitly typed. 
int i = 10; // Explicitly typed. 
```  
  
 Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [LINQ Sorgu işlemlerinde tür ilişkileri](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sorgu ifadeleri gösterir. İlk ifadede, kullanımını `var` izin verilir, ancak sorgu sonuç türü olarak açıkça belirtilebilir gerekli olmadığından bir `IEnumerable<string>`. Ancak, ikinci ifadede, `var` anonim türlerin koleksiyonunu olacak şekilde sonuç verir ve bu tür adı derleyici için dışında erişilemez. Kullanım `var` sonucu için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır. Örnek # 2'de unutmayın `foreach` yineleme değişkeni `item` de dolaylı olarak yazılmalıdır.  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)  
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Örtülü Olarak Yazılan Yerel Değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
