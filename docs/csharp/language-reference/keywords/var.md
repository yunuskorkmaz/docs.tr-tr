---
title: var (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e0df25eb46bb769214412646d0ac3a7a576b3b73
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2018
---
# <a name="var-c-reference"></a>var (C# Başvurusu)
Visual C# 3. 0'den itibaren yöntemi kapsamda bildirilen değişkenler örtük bir "tür" olabilir `var`. Türü örtük olarak belirlenmiş yerel değişken yalnızca kendiniz türü bildirilmedi, ancak türü derleyici belirler gibi kesin türü belirtilmiş. Aşağıdaki iki bildirimlerini `i` işlevsel olarak eşdeğerdir:  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [LINQ Sorgu işlemlerinde tür ilişkileri](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, iki sorgu ifadeleri gösterir. Kullanımını ilk ifadesinde `var` izin verilir, ancak sorgu sonuç türü olarak açıkça belirtilebilir gerekli olmadığı bir `IEnumerable<string>`. Ancak, ikinci ifade içinde `var` anonim türler koleksiyonu bulunmasını sağlar ve bu tür adı derleyiciye dışında erişilemez. Kullanımı `var` sonucu için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır. Örnek # 2'de unutmayın `foreach` yineleme değişkeni `item` da örtük olarak yazılmalıdır.  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Örtülü Olarak Yazılan Yerel Değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
