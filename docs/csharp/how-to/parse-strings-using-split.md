---
title: String. Split kullanarak dizeleri ayrıştırma (C# kılavuz)
description: String. Split, bir sınırlayıcı kümesinden bölünen dizelerin dizisini döndürür. Dizeleri ayrıştırmak için kolay bir yoldur.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973229"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>String. Split kullanarak dizeleri ayrıştırma (C# kılavuz)

<xref:System.String.Split%2A?displayProperty=nameWithType> yöntemi, giriş dizesini bir veya daha fazla sınırlayıcı temelinde bölerek bir alt dizeler dizisi oluşturur. Genellikle bir dizeyi sözcük sınırlarında ayırmanın en kolay yoludur. Ayrıca, diğer belirli karakter veya dizelerde dizeleri ayırmak için de kullanılır.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki kod, ortak bir tümceciği her sözcük için bir dizeler dizisine böler.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Bir ayırıcı karakterinin her örneği döndürülen dizide bir değer üretir. Ardışık Ayırıcı karakterler boş dizeyi döndürülen dizide bir değer olarak oluşturur.  Bu, bir ayırıcı olarak boşluk kullanan aşağıdaki örnekte görebilirsiniz:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Bu davranış, tablo verilerini temsil eden, virgülle ayrılmış değerler (CSV) dosyaları gibi biçimlerin daha kolay olmasını sağlar. Ardışık virgüller boş bir sütunu temsil eder.

Döndürülen dizide boş dizeleri hariç tutmak için isteğe bağlı bir <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parametresi geçirebilirsiniz. Döndürülen koleksiyonun daha karmaşık işlenmesi için, [LINQ](../programming-guide/concepts/linq/index.md) kullanarak sonuç sırasını değiştirebilirsiniz.

<xref:System.String.Split%2A?displayProperty=nameWithType> birden çok ayırıcı karakter kullanabilir.
Aşağıdaki örnek boşluk, virgül, nokta, iki nokta üst üste ve sekmelerini kullanır, bu karakterleri içeren bir dizide <xref:System.String.Split%2A>.
Kodun alt kısmındaki döngü döndürülen dizideki her bir sözcüğü görüntüler.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Herhangi bir ayırıcıdaki ardışık örnekler, çıkış dizisinde boş dize üretir:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> dize dizisini alabilir (tek karakterler yerine hedef dizeyi ayrıştırmak için ayırıcılar olarak davranan karakter dizileri).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz. Ya da örnekleri [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../programming-guide/index.md)
- [Dizeler](../programming-guide/strings/index.md)
- [.NET normal Ifadeleri](../../standard/base-types/regular-expressions.md)
