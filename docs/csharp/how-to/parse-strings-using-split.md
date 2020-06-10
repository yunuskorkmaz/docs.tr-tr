---
title: String. Split kullanarak dizeleri ayrıştırma (C# Kılavuzu)
description: String. Split, bir sınırlayıcı kümesinden bölünen dizelerin dizisini döndürür. Dizeleri ayrıştırmak için kolay bir yoldur.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 4f0056426fb29ec3d76093e57fa45e2046f27a4f
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662998"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a>C 'de dize. Split kullanarak dizeleri ayrıştırma\#

<xref:System.String.Split%2A?displayProperty=nameWithType>Yöntemi, giriş dizesini bir veya daha fazla sınırlayıcı temelinde bölerek bir alt dizeler dizisi oluşturur. Genellikle bir dizeyi sözcük sınırlarında ayırmanın en kolay yoludur. Ayrıca, diğer belirli karakter veya dizelerde dizeleri ayırmak için de kullanılır.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki kod, ortak bir tümceciği her sözcük için bir dizeler dizisine böler.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

Bir ayırıcı karakterinin her örneği döndürülen dizide bir değer üretir. Ardışık Ayırıcı karakterler boş dizeyi döndürülen dizide bir değer olarak oluşturur. Bir ayırıcı olarak boşluk karakterini kullanan aşağıdaki örnekte boş bir dizenin nasıl oluşturulduğunu görebilirsiniz.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

Bu davranış, tablo verilerini temsil eden, virgülle ayrılmış değerler (CSV) dosyaları gibi biçimlerin daha kolay olmasını sağlar. Ardışık virgüller boş bir sütunu temsil eder.

<xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType>Döndürülen dizide boş dizeleri hariç tutmak için isteğe bağlı bir parametre geçirebilirsiniz. Döndürülen koleksiyonun daha karmaşık işlenmesi için, [LINQ](../programming-guide/concepts/linq/index.md) kullanarak sonuç sırasını değiştirebilirsiniz.

<xref:System.String.Split%2A?displayProperty=nameWithType>birden çok ayırıcı karakter kullanabilir.
Aşağıdaki örnek boşluk, virgül, nokta, iki nokta üst üste ve sekmelerini kullanır ve bu karakterleri içeren bir dizide öğesine <xref:System.String.Split%2A> .
Kodun alt kısmındaki döngü döndürülen dizideki her bir sözcüğü görüntüler.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

Herhangi bir ayırıcıdaki ardışık örnekler, çıkış dizisinde boş dize üretir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<xref:System.String.Split%2A?displayProperty=nameWithType>bir dizi dizeyi alabilir (tek karakterler yerine hedef dizeyi ayrıştırmak için ayırıcı olarak davranan karakter dizileri).

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a>Ayrıca bkz.

- [C# programlama kılavuzu](../programming-guide/index.md)
- [Dizeler](../programming-guide/strings/index.md)
- [.NET normal ifadeleri](../../standard/base-types/regular-expressions.md)
