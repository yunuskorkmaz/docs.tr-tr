---
title: 'Nasıl yapılır: String.Split kullanarak dizeleri ayrıştırma (C# Kılavuzu)'
description: String.Split sınırlayıcılar kümesinden bölme dizisini döndürür. Dizeleri ayrıştırma kolay bir yoludur.
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: a8cb3a62497379f60e9cc6dec3d342192361f865
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672347"
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Nasıl yapılır: String.Split kullanarak dizeleri ayrıştırma (C# Kılavuzu)

<xref:System.String.Split%2A?displayProperty=nameWithType> Yöntemi, bir veya daha fazla ayırıcıları göre giriş dizesini bölerek alt dizeler dizisi oluşturur. Bir sözcük sınırlarından dizesine ayırmak için genellikle en kolay yoludur. Ayrıca, diğer belirli karakterler veya dizelerin dizeleri bölmek için kullanılır.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki kodu ortak bir deyim için her bir sözcüğün bir dize dizisi halinde böler.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Her örnek bir ayırıcı karakteri döndürülen dizideki bir değer üretir. Ardışık ayırıcı karakter, döndürülen dizi değer olarak boş bir dize oluşturur.  Bu alanı bir ayırıcı olarak kullanan aşağıdaki örnekte görebilirsiniz:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Bu davranış biçimlerini tablosal verileri temsil eden virgülle ayrılmış değerler (CSV) dosyaları gibi kolaylaştırır. Art arda virgüllerle boş bir sütunu temsil eder.

İsteğe bağlı geçirebilirsiniz <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> döndürülen dizideki herhangi bir boş dizeler hariç tutmak için parametre. Daha karmaşık döndürülen koleksiyon işleme için kullanabileceğiniz [LINQ](../programming-guide/concepts/linq/index.md) Sonuç dizisini değiştirmek için.

<xref:System.String.Split%2A?displayProperty=nameWithType> birden fazla ayırıcı karakter kullanabilirsiniz.
Aşağıdaki örnek, boşluk, virgül, nokta, iki nokta üst üste ve sekmeler, tüm bu karakterler için ayırma içeren bir dizi içinde geçirilen kullanır <xref:System.String.Split%2A>.
Döngü kodunun altındaki her bir kelimelerin döndürülen dizideki görüntüler.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Tüm ayırıcı ardışık örnekleri bir çıkış dizisinde boş dize üretir:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> (tek karakter yerine hedef dizesini ayrıştırmak için ayırıcı olarak davranmak karakter dizileri) dize dizisi alabilir.  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Bu örnekler kodda bakarak deneyebilirsiniz bizim [GitHub deposu](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings). Örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../programming-guide/index.md)
- [Dizeler](../programming-guide/strings/index.md)
- [.NET normal ifadeler](../../standard/base-types/regular-expressions.md)
