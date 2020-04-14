---
title: Dize içeriği nasıl değiştirilir - C# Guide
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: f31fa94501ac2120e22e229dfc11babb8b8cc0f3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242861"
---
# <a name="how-to-modify-string-contents-in-c"></a>C'de dize içeriği nasıl değiştirilir?\#

Bu makalede, varolan `string` `string`bir değiştirerek bir üretmek için çeşitli teknikler gösterir. Tüm teknikler yeni `string` bir nesne olarak değişikliklerin sonucu nu döndürtün gösterdi. Bunu açıkça göstermek için, örneklerin tümü sonucu yeni bir değişkende saklar. Daha sonra her örneği `string` çalıştırdığınızda hem orijinali hem de değişiklikten `string` kaynaklanan sonucu inceleyebilirsiniz.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Bu makalede gösterilen çeşitli teknikler vardır. Varolan metni değiştirebilirsiniz. Desenleri arayabilir ve eşleşen metni diğer metinlerle değiştirebilirsiniz. Bir dizeyi bir karakter dizisi olarak değerlendirebilirsiniz. Ayrıca, beyaz alanı kaldıran kolaylık yöntemleri de kullanabilirsiniz. Senaryonuzla en yakından eşleşen teknikleri seçmelisiniz.

## <a name="replace-text"></a>Metni değiştirme

Aşağıdaki kod, varolan metni bir yedekle değiştirerek yeni bir dize oluşturur.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Önceki kod dizeleri bu *değişmez* özelliğini gösterir. Yukarıdaki örnekte, özgün dize, `source`, , değiştirilmediğini görebilirsiniz. Yöntem, <xref:System.String.Replace%2A?displayProperty=nameWithType> değişiklikleri içeren `string` yeni bir yöntem oluşturur.

Yöntem <xref:System.String.Replace%2A> dizeleri veya tek karakter değiştirebilirsiniz. Her iki durumda da, aranan metnin her oluşumu değiştirilir.  Aşağıdaki örnektüm ' ' karakterlerinin\_yerine ' ' ile '

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Kaynak dize değişmez ve yeni bir dize değiştirimle döndürülür.

## <a name="trim-white-space"></a>Beyaz alanı kırpın

Herhangi bir <xref:System.String.Trim%2A?displayProperty=nameWithType>satır <xref:System.String.TrimStart%2A?displayProperty=nameWithType>veya <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> sondaki beyaz alanı kaldırmak için , ve yöntemleri kullanabilirsiniz.  Aşağıdaki kod her birinin bir örneğini gösterir. Kaynak dize değişmez; bu yöntemler değiştirilmiş içeriği ile yeni bir dize döndürün.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Metni kaldırma

<xref:System.String.Remove%2A?displayProperty=nameWithType> Yöntemi kullanarak metni bir dizeden kaldırabilirsiniz. Bu yöntem, belirli bir dizin başlayarak karakter bir dizi kaldırır. Aşağıdaki örnekte, bir <xref:System.String.IndexOf%2A?displayProperty=nameWithType> dizeden metni kaldırmak <xref:System.String.Remove%2A> için nasıl kullanılacağı gösterilmektedir:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Eşleşen desenleri değiştirme

Metin eşleştirme [desenlerini](../../standard/base-types/regular-expressions.md) büyük olasılıkla bir desentarafından tanımlanan yeni metinle değiştirmek için normal ifadeler kullanabilirsiniz. Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> kaynak dizesinde bir desen bulmak ve uygun büyük harfle değiştirmek için sınıfı kullanır. Yöntem, <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> bağımsız değişkenlerinden biri olarak değiştirme mantığını sağlayan bir işlev alır. Bu örnekte, bu `LocalReplaceMatchCase` işlev, örnek yöntem içinde bildirilen yerel bir **işlevdir.** `LocalReplaceMatchCase`uygun <xref:System.Text.StringBuilder?displayProperty=nameWithType> büyük harfle değiştirme dizesi oluşturmak için sınıfı kullanır.

Normal ifadeler, bilinen metin yerine bir deseni izleyen metni aramak ve değiştirmek için en yararlıdır. Daha fazla ayrıntı için [dizeleri arama ya da arama](search-strings.md) Arama deseni, "the\s" sözcüğün "the" sözcüğüne ve ardından bir beyaz boşluk karakterini arar. Desenin bu bölümü, kaynak dizedeki "orada" ile eşleşmemesini sağlar. Normal ifade dili öğeleri hakkında daha fazla bilgi için [Bkz. Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

Yöntem, <xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> <xref:System.Text.StringBuilder> nesnedeki içeriği içeren değişmez bir dize döndürür.

## <a name="modifying-individual-characters"></a>Tek tek karakterleri değiştirme

Bir dizeden bir karakter dizisi oluşturabilir, dizinin içeriğini değiştirebilir ve ardından dizinin değiştirilmiş içeriğinden yeni bir dize oluşturabilirsiniz.

Aşağıdaki örnek, dizedeki bir karakter kümesinin nasıl değiştirilebildiğini gösterir. İlk olarak, <xref:System.String.ToCharArray?displayProperty=nameWithType> bir karakter dizisi oluşturmak için yöntemi kullanır. "Tilki" <xref:System.String.IndexOf%2A> kelimesinin başlangıç indeksini bulmak için yöntemi kullanır. Sonraki üç karakter farklı bir sözcük ile değiştirilir. Son olarak, güncelleştirilmiş karakter dizisinden yeni bir dize oluşturulur.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>Programlı bir şekilde dize içeriği oluşturmak

Dizeleri değişmez olduğundan, önceki örneklerin tümü geçici dizeleri veya karakter dizileri oluşturur. Yüksek performanslı senaryolarda, bu yığın ayırmaları önlemek için istenebilir. .NET Core, <xref:System.String.Create%2A?displayProperty=nameWithType> ara geçici dize ayırmalarından kaçınırken bir geri arama yoluyla bir dizenin karakter içeriğini programlı olarak doldurmanızı sağlayan bir yöntem sağlar.

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Sabit bir bloktaki bir dizeyi güvenli olmayan kodla değiştirebilirsiniz, ancak dize oluşturulduktan sonra dize içeriğini değiştirmeniz **şiddetle** önerilmez. Bunu yapmak, olayları tahmin edilemeyecek şekillerde kırar. Örneğin, birisi sizinkiyle aynı içeriğe sahip bir dize yi interns, kopyanızı alır ve dizesini hiç değiştirmenizi beklemez.

Bu örnekleri [GitHub depomuzdaki](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz. Veya bir zip [dosyası olarak](../../../samples/snippets/csharp/how-to/strings.zip)örnekleri indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework Normal İfadeleri](../../standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)
