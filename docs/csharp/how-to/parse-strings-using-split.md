---
title: String.Split (C# Guide) kullanarak dizeleri ayrıştırma
description: String.Split, bir dizi sınırlayıcıdan bölünmüş dizeler dizisini döndürür. İpleri ayrışdırmanın kolay bir yolu.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: b46429f3b55658e1f2a7d21eed714c1d02236c57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73973229"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>String.Split (C# Guide) kullanarak dizeleri ayrıştırma

Yöntem, <xref:System.String.Split%2A?displayProperty=nameWithType> giriş dizesini bir veya daha fazla sınırlayıcıyı temel alarak bölerek bir dizi alt dizeleri oluşturur. Genellikle sözcük sınırları üzerinde bir dize ayırmak için en kolay yoludur. Ayrıca, diğer belirli karakterler veya dizeleri dizeleri bölmek için kullanılır.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki kod, ortak bir tümceciği her sözcük için bir dizi dize ye böler.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Ayırıcı karakterin her örneği döndürülen dizide bir değer üretir. Ardışık ayırıcı karakterler, boş dizeyi döndürülen dizide bir değer olarak üretir.  Bunu ayırıcı olarak alanı kullanan aşağıdaki örnekte görebilirsiniz:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Bu davranış, tabular verileri temsil eden virgülayrılmış değerler (CSV) dosyaları gibi biçimler için kolaylaştırır. Ardışık virgüller boş bir sütunu temsil ediyor.

Döndürülen dizideki <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> boş dizeleri hariç tutmak için isteğe bağlı bir parametre geçirebilirsiniz. Döndürülen koleksiyonun daha karmaşık işlenmesi için, sonuç sırasını işlemek için [LINQ'yi](../programming-guide/concepts/linq/index.md) kullanabilirsiniz.

<xref:System.String.Split%2A?displayProperty=nameWithType>birden çok ayırıcı karakter kullanabilirsiniz.
Aşağıdaki örnek, bu ayıran karakterleri içeren bir dizi geçirilen boşluklar, virgüller, dönemler, üst <xref:System.String.Split%2A>üste ve sekmeler kullanır.
Kodun altındaki döngü, döndürülen dizideki sözcüklerin her birini görüntüler.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Herhangi bir ayırıcının ardışık örnekleri, çıktı dizisindeki boş dizeyi üretir:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType>bir dizi dize alabilir (tek karakterler yerine hedef dizeyi ayrıştırmak için ayırıcı görevi yapan karakter dizileri).  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Bu örnekleri [GitHub depomuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz. Veya bir zip [dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)örnekleri indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../programming-guide/index.md)
- [Dize](../programming-guide/strings/index.md)
- [.NET Düzenli İfadeler](../../standard/base-types/regular-expressions.md)
