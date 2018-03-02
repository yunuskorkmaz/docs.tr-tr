---
title: "Nasıl yapılır: String.Split (C# Kılavuzu) kullanarak dizeleri ayrıştırma"
description: "String.Split sınırlayıcıları kümesinden bölünmüş bir dizeler dizisi döndürür. Dizeleri ayrıştırma kolay bir yoludur."
ms.date: 01/03/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
author: BillWagner
ms.author: wiwagn
ms.custom: mvc
ms.openlocfilehash: afaff6f81a1a4240214f738d0fc9f3bafdaf868c
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-parse-strings-using-stringsplit-c-guide"></a>Nasıl yapılır: String.Split (C# Kılavuzu) kullanarak dizeleri ayrıştırma

<xref:System.String.Split%2A?displayProperty=nameWithType> Yöntemi, bir veya daha fazla ayırıcıları temel giriş dizesi bölerek alt dizeler dizisi oluşturur. Bir dize word sınırlarındaki ayırmak için genellikle en kolay yoludur. Ayrıca, dizeleri diğer özel karakterler veya dizeleri bölme için de kullanılır.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Aşağıdaki kodu her sözcüğün dizelerden oluşan bir dizi ortak bir deyim ayıran.

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

Her bir ayırıcı karakter örneğini döndürülen dizideki bir değer oluşturur. Ardışık ayırıcı karakter boş dize verilen dizi değer olarak üretir.  Bu alan bir ayırıcı olarak kullanan aşağıdaki örnekte görebilirsiniz:

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

Bu davranış biçimleri için tablo verileri temsil eden virgülle ayrılmış değerler (CSV) dosyaları gibi kolaylaştırır. Ardışık virgül boş bir sütunu temsil eder.

İsteğe bağlı bir geçirebilirsiniz <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> herhangi boş dizeler döndürülen dizideki dışlamak için parametre. Döndürülen koleksiyon daha karmaşık işlenmesi için kullandığınız [LINQ](../programming-guide/concepts/linq/index.md) Sonuç dizisini denetlemek için.    

<xref:System.String.Split%2A?displayProperty=nameWithType> birden çok ayırıcı karakter kullanabilirsiniz. Aşağıdaki örnek, boşluk, virgül, nokta, iki nokta üst üste ve sekmeler, tüm bu karakterler için ayırma içeren bir dizi geçirilen kullanır <xref:System.String.Split%2A>.  Kod alt döngü her sözcüklerin döndürülen dizideki görüntüler.  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

Tüm ayırıcı ardışık örnekleri çıkış dizisi boş dizesinde üretir:

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<xref:System.String.Split%2A?displayProperty=nameWithType> dizeler (tek karakter yerine hedef dizesini ayrıştırmak için ayırıcı olarak davranmak karakter sıraları) dizisi alabilir.  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

Kodda bakarak bu örnekleri deneyebilirsiniz bizim [GitHub deposunu](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings). Veya örnekleri indirebilirsiniz [zip dosyası olarak](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings.zip).

## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../programming-guide/index.md)  
 [Dizeler](../programming-guide/strings/index.md)  
 [.NET normal ifadeler](../../standard/base-types/regular-expressions.md)
