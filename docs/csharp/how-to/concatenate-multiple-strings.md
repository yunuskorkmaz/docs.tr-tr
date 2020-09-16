---
title: Birden çok dizeyi birleştirme (C# Kılavuzu)
description: C# dilinde dizeleri birleştirmek için birden çok yol vardır. Seçenekleri ve farklı seçimlerin arkasındaki nedenleri öğrenin.
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: f2aae14deac967a833fb3510acdb32e0971485b5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537489"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a>Birden çok dizeyi birleştirme (C# Kılavuzu)

*Birleştirme* , bir dizeyi başka bir dizenin sonuna ekleme işlemidir. İşlecini kullanarak dizeleri birleştirebilirsiniz `+` . Dize sabit değerleri ve dize sabitleri için birleştirme, derleme zamanında oluşur; çalışma zamanı birleştirme gerçekleşmez. Dize değişkenleri için, birleştirme yalnızca çalışma zamanında gerçekleşir.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki örnek, kaynak kodda okunabilirliğini geliştirmek için bir uzun dize sabit değerini daha küçük dizelere bölmek için birleştirme kullanır. Bu parçalar, derleme zamanında tek bir dizeye birleştirilir. Dahil edilen dizelerin sayısından bağımsız olarak, çalışma zamanı performans maliyeti yoktur.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet1":::

Dize değişkenlerini birleştirmek için, `+` veya `+=` işleçlerini, [dize ilişkilendirmeyi](../language-reference/tokens/interpolated.md) veya <xref:System.String.Format%2A?displayProperty=nameWithType> , <xref:System.String.Concat%2A?displayProperty=nameWithType> ya da yöntemlerini kullanabilirsiniz <xref:System.String.Join%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> . `+`İşleci kullanımı kolaydır ve sezgisel kod sunar. `+`Tek bir ifadede birkaç işleç kullansanız bile, dize içeriği yalnızca bir kez kopyalanır. Aşağıdaki kod `+` `+=` dizeleri birleştirmek için ve işleçlerini kullanma örneklerini gösterir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet2":::

Bazı ifadelerde, aşağıdaki kodda gösterildiği gibi dize ilişkilendirmeyi kullanarak dizeleri birleştirmek daha kolay olur:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet3":::

> [!NOTE]
> Dize birleştirme işlemlerinde, C# derleyicisi boş bir dizeyi boş bir dizeyle aynı şekilde değerlendirir.

Dizeleri birleştirme yöntemi <xref:System.String.Format%2A?displayProperty=nameWithType> . Bu yöntem, az sayıda bileşen dizesinden bir dize oluştururken iyi sonuç verir.

Diğer durumlarda, dizeleri birleşik olarak kaç tane kaynak dizesi birleştirmiş olduğunuzu ve kaynak dizelerinin gerçek sayısını bildiğiniz bir döngüde birleştiriyorsunuz olabilirsiniz. <xref:System.Text.StringBuilder>Sınıfı bu senaryolar için tasarlanmıştır. Aşağıdaki kod, <xref:System.Text.StringBuilder.Append%2A> <xref:System.Text.StringBuilder> dizeleri birleştirmek için sınıfının yöntemini kullanır.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet4":::

[Dize birleştirme veya `StringBuilder` sınıf seçme nedenleri](/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types)hakkında daha fazla bilgi edinebilirsiniz.

Bir koleksiyondaki dizeleri birleştirmek için başka bir seçenek <xref:System.String.Concat%2A?displayProperty=nameWithType> yöntemi kullanmaktır. <xref:System.String.Join%2A?displayProperty=nameWithType>Kaynak dizelerin bir sınırlayıcı ile ayrılması gerekiyorsa yöntemi kullanın. Aşağıdaki kod her iki yöntemi kullanarak bir sözcük dizisini birleştirir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet5":::

Son olarak, [LINQ](../programming-guide/concepts/linq/index.md) ve <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> yöntemini bir koleksiyondaki dizeleri birleştirmek için kullanabilirsiniz. Bu yöntem, kaynak dizelerini bir lambda ifadesi kullanarak birleştirir. Lambda ifadesi, her bir dizeyi var olan birikme ekleme işini yapar. Aşağıdaki örnek, dizideki her sözcük arasına bir boşluk ekleyerek bir sözcük dizisini birleştirir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet6":::

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [C# programlama kılavuzu](../programming-guide/index.md)
- [Dizeler](../programming-guide/strings/index.md)
