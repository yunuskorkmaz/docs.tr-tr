---
title: Diziler-C# Programlama Kılavuzu
description: C# ' de bir dizi veri yapısında aynı türde birden çok değişken depolayın. Bir tür belirterek veya herhangi bir türü depolamak için nesne belirttikten sonra bir dizi bildirin.
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e302ff2e4c2488c4899c4eb99a666d2d322119ce
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474741"
---
# <a name="arrays-c-programming-guide"></a>Diziler (C# Programlama Kılavuzu)

Aynı türde birden çok değişkeni bir dizi veri yapısına saklayabilirsiniz. Öğelerinin türünü belirterek bir dizi bildirirsiniz. Dizinin herhangi bir türdeki öğeleri depolamasını istiyorsanız, `object` türü olarak belirtebilirsiniz. C# Birleşik tür sisteminde, tüm türler, önceden tanımlanmış ve Kullanıcı tanımlı, başvuru türleri ve değer türleri, doğrudan veya dolaylı olarak öğesinden devralınır <xref:System.Object> .

```csharp
type[] arrayName;
```

## <a name="example"></a>Örnek

Aşağıdaki örnek, tek boyutlu, çok boyutlu ve pürüzlü Diziler oluşturur:

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a>Diziye genel bakış

Bir dizi aşağıdaki özelliklere sahiptir:

- Bir dizi [tek boyutlu](single-dimensional-arrays.md), [çok boyutlu](multidimensional-arrays.md) veya [pürüzlü](jagged-arrays.md)olabilir.
- Boyut sayısı ve her boyutun uzunluğu, dizi örneği oluşturulduğunda oluşturulur. Bu değerler, örneğin kullanım ömrü boyunca değiştirilemez.
- Sayısal dizi öğelerinin varsayılan değerleri sıfır olarak ayarlanır ve başvuru öğeleri null olarak ayarlanır.
- Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve olarak başlatılır `null` .
- Diziler sıfır dizinli: öğeleri olan bir dizi ' dan ' a `n` dizinlenir `0` `n-1` .
- Dizi öğeleri, bir dizi türü de dahil olmak üzere herhangi bir türde olabilir.
- Dizi türleri, soyut temel türden türetilmiş [başvuru türleridir](../../language-reference/keywords/reference-types.md) <xref:System.Array> . Bu tür ve uyguladığından <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> , C# ' deki tüm dizilerde [foreach](../../language-reference/keywords/foreach-in.md) yineleme kullanabilirsiniz.

## <a name="related-sections"></a>İlgili bölümler

- [Nesne Olarak Diziler](arrays-as-objects.md)
- [Dizilerle foreach kullanma](using-foreach-with-arrays.md)
- [Dizileri Bağımsız Değişkenler Olarak Geçirme](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Koleksiyonlar](../concepts/collections.md)
