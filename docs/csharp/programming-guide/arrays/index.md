---
title: Diziler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "75715051"
---
# <a name="arrays-c-programming-guide"></a>Diziler (C# Programlama Kılavuzu)

Aynı türdeki birden çok değişkeni bir dizi veri yapısında depolayabilirsiniz. Öğelerinin türünü belirterek bir dizi bildirirsiniz. Dizinin herhangi bir türdeki öğeleri depolamasını istiyorsanız, dizinin türü olarak belirtebilirsiniz. `object` C#'ın birleşik tip sisteminde, önceden tanımlanmış ve kullanıcı tarafından tanımlanan tüm türler, referans <xref:System.Object>türleri ve değer türleri, doğrudan veya dolaylı olarak .

```csharp
type[] arrayName;
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, tek boyutlu, çok boyutlu ve pürüzlü diziler oluşturur:

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>Diziye genel bakış

Bir dizi aşağıdaki özelliklere sahiptir:

- Bir dizi [Tek Boyutlu,](single-dimensional-arrays.md) [Çok Boyutlu](multidimensional-arrays.md) veya [Pürüzlü](jagged-arrays.md)olabilir.
- Dizi örneği oluşturulduğunda boyut sayısı ve her boyutun uzunluğu oluşturulur. Bu değerler, örneğin ömrü boyunca değiştirilemez.
- Sayısal dizi öğelerinin varsayılan değerleri sıfıra, başvuru öğeleri null olarak ayarlanır.
- Pürüzlü bir dizi dizi dizidir ve bu nedenle öğeleri başvuru `null`türleridir ve '' için başharfler.
- Diziler sıfır dizilimi vardır: öğeleri `n` olan `0` `n-1`bir dizi ' den .
- Dizi öğeleri, bir dizi türü de dahil olmak üzere herhangi bir türde olabilir.
- Dizi türleri soyut temel türünden <xref:System.Array>türetilen başvuru [türleridir.](../../language-reference/keywords/reference-types.md) Bu tür uygular <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>ve , C# tüm dizileri [foreach](../../language-reference/keywords/foreach-in.md) yineleme kullanabilirsiniz.

## <a name="related-sections"></a>İlgili bölümler

- [Nesne Olarak Diziler](arrays-as-objects.md)
- [Dizilerle foreach kullanma](using-foreach-with-arrays.md)
- [Dizileri Bağımsız Değişkenler Olarak Geçirme](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Koleksiyonlar](../concepts/collections.md)
