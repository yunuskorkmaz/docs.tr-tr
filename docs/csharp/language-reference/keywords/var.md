---
title: var- C# başvuru
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712890"
---
# <a name="var-c-reference"></a>var (C# Başvurusu)

Visual C# 3,0 ' den başlayarak, yöntem kapsamında belirtilen değişkenlerin örtük bir "tür" `var`olabilir. Örtük olarak yazılmış bir yerel değişken, türü kendi kendinize bildirdiyseniz olduğu gibi kesin şekilde yazılır, ancak derleyici türü belirler. Aşağıdaki iki `i` bildirimi işlevsel olarak eşdeğerdir:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md) [örtük olarak yazılan yerel değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve tür ilişkileri.

## <a name="example"></a>Örnek

Aşağıdaki örnek iki sorgu ifadesini gösterir. İlk ifadede `var` kullanımı izin verilir ancak gerekli değildir, çünkü sorgu sonucunun türü açıkça bir `IEnumerable<string>`olarak ifade edilebilir. Ancak, ikinci ifadede `var`, sonucun anonim türlerin bir koleksiyonu olmasına izin verir ve bu türün adı derleyicinin kendisi hariç erişilebilir değildir. `var` kullanımı, sonuç için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır. Örnek #2, `foreach` yineleme değişkeni `item` de örtük olarak yazılmalıdır.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Örtülü Olarak Yazılan Yerel Değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
