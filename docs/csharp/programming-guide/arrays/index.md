---
title: Diziler- C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715051"
---
# <a name="arrays-c-programming-guide"></a>Diziler (C# Programlama Kılavuzu)

Aynı türde birden çok değişkeni bir dizi veri yapısına saklayabilirsiniz. Öğelerinin türünü belirterek bir dizi bildirirsiniz. Dizinin herhangi bir türdeki öğeleri depolamasını istiyorsanız, türü olarak `object` belirtebilirsiniz. Birleşik tür sisteminde C#, tüm türler, önceden tanımlanmış ve Kullanıcı tanımlı, başvuru türleri ve değer türleri, <xref:System.Object>doğrudan veya dolaylı olarak devralınır.

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
- Sivri dizi dizi dizilerdir ve bu nedenle öğeleri başvuru türleridir ve `null`olarak başlatılır.
- Diziler sıfır dizinli: `n` öğeler içeren bir dizi `0` `n-1`olarak dizinlenir.
- Dizi öğeleri, bir dizi türü de dahil olmak üzere herhangi bir türde olabilir.
- Dizi türleri, <xref:System.Array>soyut temel türünden türetilmiş [başvuru türleridir](../../language-reference/keywords/reference-types.md) . Bu tür <xref:System.Collections.IEnumerable> ve <xref:System.Collections.Generic.IEnumerable%601>uyguladığından, içindeki C#tüm dizilerde [foreach](../../language-reference/keywords/foreach-in.md) yineleme kullanabilirsiniz.

## <a name="related-sections"></a>İlgili bölümler

- [Nesne Olarak Diziler](arrays-as-objects.md)
- [Dizilerle foreach kullanma](using-foreach-with-arrays.md)
- [Dizileri Bağımsız Değişkenler Olarak Geçirme](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Koleksiyonlar](../concepts/collections.md)
