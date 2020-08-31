---
title: var-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: d944cde932b5c1f5ef1439ee46a1447e107e6ac9
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053081"
---
# <a name="var-c-reference"></a>var (C# Başvurusu)

Visual C# 3,0 ' den başlayarak, yöntem kapsamında belirtilen değişkenlerin örtük bir "tür" türü olabilir `var` . Örtük olarak yazılmış bir yerel değişken, türü kendi kendinize bildirdiyseniz olduğu gibi kesin şekilde yazılır, ancak derleyici türü belirler. Aşağıdaki iki bildirimi `i` işlevsel olarak eşdeğerdir:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Daha fazla bilgi için bkz. [LINQ sorgu Işlemlerinde](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md) [örtük olarak yazılan yerel değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve tür ilişkileri.

> [!IMPORTANT]
> `var`Null yapılabilir başvuru türleri etkinken kullanıldığında, ifade türü null yapılabilir olmasa bile her zaman null yapılabilir bir başvuru türü anlamına gelir.

## <a name="example"></a>Örnek

Aşağıdaki örnek iki sorgu ifadesini gösterir. İlk ifadede öğesinin kullanımına `var` izin verilir, ancak sorgu sonucunun türü açıkça bir olarak belirtilemediğinden gerekli değildir `IEnumerable<string>` . Ancak, ikinci ifadede, `var` sonucun anonim türlerin bir koleksiyonu olmasına izin verir ve bu türün adı derleyicinin kendisi hariç erişilebilir değildir. Kullanımı, `var` sonuç için yeni bir sınıf oluşturma gereksinimini ortadan kaldırır. Örneğin #2, `foreach` yineleme değişkeninin `item` de örtük olarak yazılmış olması gerektiğini unutmayın.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Örtülü Olarak Yazılan Yerel Değişkenler](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
