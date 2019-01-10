---
title: var - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 79a3fe331107a902957158a9631f607cb431be32
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610651"
---
# <a name="var-c-reference"></a>var (C# Başvurusu)

Visual C# 3.0 içinde başlayarak, yöntem kapsamda bildirilen değişkenler örtük bir "type" olabilir `var`. Bir türü örtük olarak belirlenmiş yerel değişken alacağı yalnızca kendiniz türü bildirilen, ancak derleyicinin türü belirler kesin. Aşağıdaki iki bildirimlerini `i` işlevsel olarak eşdeğerdir:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [LINQ Sorgu işlemlerinde tür ilişkileri](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

## <a name="example"></a>Örnek

Aşağıdaki örnek, iki sorgu ifadeleri gösterir. İlk ifadede, kullanımını `var` izin verilir, ancak sorgu sonuç türü olarak açıkça belirtilebilir gerekli olmadığından bir `IEnumerable<string>`. Ancak, ikinci ifadede, `var` anonim türlerin koleksiyonunu olacak şekilde sonuç verir ve bu tür adı derleyici için dışında erişilemez. Kullanım `var` sonucu için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır. Örnek # 2'de unutmayın `foreach` yineleme değişkeni `item` de dolaylı olarak yazılmalıdır.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Örtülü Olarak Yazılan Yerel Değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)