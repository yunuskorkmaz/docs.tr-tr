---
title: Diziler-C# Programlama Kılavuzu
description: C# ' de bir dizi veri yapısında aynı türde birden çok değişken depolayın. Bir tür belirterek veya herhangi bir türü depolamak için nesne belirttikten sonra bir dizi bildirin.
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 203d8b86da4e74d8c5397132a0ba68618eedf348
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794762"
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

### <a name="arrays-as-objects"></a>Nesne Olarak Diziler

C# ' de, diziler aslında nesneler ve yalnızca C ve C++ ' da olduğu gibi bitişik belleğin adreslenebilir bölgelerini değildir. <xref:System.Array> tüm dizi türlerinin soyut temel türüdür. Özellikleri ve olan diğer sınıf üyelerini kullanabilirsiniz <xref:System.Array> . Bunun bir örneği, <xref:System.Array.Length%2A> bir dizinin uzunluğunu almak için özelliğini kullanmaktır. Aşağıdaki kod, dizi uzunluğunu, `numbers` yani `5` adlı bir değişkene atar `lengthOfNumbers` :

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<xref:System.Array>Sınıfı, dizileri sıralamak, aramak ve kopyalamak için diğer birçok yararlı yöntem ve özellik sağlar. Aşağıdaki örnek, <xref:System.Array.Rank%2A> bir dizinin boyut sayısını göstermek için özelliğini kullanır.

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tek boyutlu dizileri kullanma](single-dimensional-arrays.md)
- [Çok boyutlu dizileri kullanma](multidimensional-arrays.md)
- [Pürüzlü dizileri kullanma](jagged-arrays.md)
- [Dizilerle foreach kullanma](using-foreach-with-arrays.md)
- [Dizileri bağımsız değişkenler olarak geçirme](passing-arrays-as-arguments.md)
- [Örtük olarak yazılan diziler](implicitly-typed-arrays.md)
- [C# Programlama Kılavuzu](../index.md)
- [Koleksiyonlar](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
