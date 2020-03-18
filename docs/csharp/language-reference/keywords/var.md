---
title: var - C# Referans
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712890"
---
# <a name="var-c-reference"></a>var (C# Başvurusu)

Visual C# 3.0'dan başlayarak, yöntem kapsamında bildirilen değişkenlerin `var`örtük bir "türü" olabilir. Örtülü olarak yazılan yerel değişken, türü kendiniz bildirmişsiniz gibi güçlü bir şekilde yazılır, ancak derleyici türü belirler. Aşağıdaki iki bildirim `i` işlevsel olarak eşdeğerdir:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Daha fazla bilgi için, [LINQ Sorgu İşlemlerinde](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md) [Örtük Olarak Yazılan Yerel Değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve Tür İlişkileri'ne bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte iki sorgu ifadesi gösterilmektedir. İlk ifadede, sorgu `var` sonucunun türü açıkça bir `IEnumerable<string>`. olarak ifade edilebildiği için, kullanıma izin verilir, ancak gerekli değildir. Ancak, ikinci ifadede, `var` sonuç anonim türleri bir koleksiyon olmasını sağlar ve bu tür adı derleyici kendisi dışında erişilebilir değildir. Kullanımı, `var` sonuç için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır. Örnek #2'da yineleme `foreach` değişkeninin `item` de örtülü olarak yazılması gerektiğini unutmayın.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Örtülü Olarak Yazılan Yerel Değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
