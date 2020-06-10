---
title: Dize içeriğini değiştirme-C# Kılavuzu
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: a32665b67cfa73aa7d4753a1427c6955827e1b86
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/10/2020
ms.locfileid: "84663011"
---
# <a name="how-to-modify-string-contents-in-c"></a>C 'de dize içeriğini değiştirme\#

Bu makalede, var olan bir değişiklik yaparak oluşturmak için çeşitli teknikler gösterilmektedir `string` `string` . Gösterilen tüm teknikler, değişikliklerin sonucunu yeni bir nesne olarak döndürür `string` . Bunu açıkça göstermek için örneklerin hepsi, sonucu yeni bir değişkende depolar. Ardından, her bir örneği çalıştırdığınızda hem orijinali hem de `string` `string` değişikliği ortaya çıkacak şekilde inceleyebilirsiniz.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Bu makalede çeşitli teknikler verilmiştir. Varolan metni değiştirebilirsiniz. Desen arayabilir ve eşleşen metni başka metinle değiştirebilirsiniz. Bir dizeyi bir karakter dizisi olarak kabul edebilirsiniz. Beyaz alanı kaldırmak için kullanışlı yöntemler de kullanabilirsiniz. Senaryonuza en yakından eşleşen teknikleri seçin.

## <a name="replace-text"></a>Metni Değiştir

Aşağıdaki kod, var olan metni bir değiştirme ile değiştirerek yeni bir dize oluşturur.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet1":::

Yukarıdaki kod, dizelerin bu *sabit* özelliğini gösterir. Önceki örnekte, özgün dizesinin `source` değiştirilmediğini görebilirsiniz. <xref:System.String.Replace%2A?displayProperty=nameWithType>Yöntemi `string` , değişiklikleri içeren yeni bir oluşturur.

<xref:System.String.Replace%2A>Yöntemi dizeleri ya da tek karakterleri değiştirebilir. Her iki durumda da, aranan metnin her oluşumu değiştirilmiştir.  Aşağıdaki örnek tüm ' ' karakterlerini ' ' ile değiştirir \_ :

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet2":::

Kaynak dize değiştirilmez ve yeni bir dize değiştirme ile birlikte döndürülür.

## <a name="trim-white-space"></a>Boşluğu Kırp

<xref:System.String.Trim%2A?displayProperty=nameWithType> <xref:System.String.TrimStart%2A?displayProperty=nameWithType> <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> Baştaki veya sondaki boşlukları kaldırmak için,, ve yöntemlerini kullanabilirsiniz.  Aşağıdaki kod, her birine bir örnek gösterir. Kaynak dize değişmez; Bu yöntemler, değiştirilen içeriğe sahip yeni bir dize döndürür.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet3":::

## <a name="remove-text"></a>Metni kaldır

Yöntemini kullanarak bir dizeden metin kaldırabilirsiniz <xref:System.String.Remove%2A?displayProperty=nameWithType> . Bu yöntem, belirli bir dizinden başlayarak birkaç karakteri kaldırır. Aşağıdaki örnek, <xref:System.String.IndexOf%2A?displayProperty=nameWithType> <xref:System.String.Remove%2A> bir dizeden metin kaldırmak için tarafından izlenen ' ın nasıl kullanılacağını gösterir:

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet4":::

## <a name="replace-matching-patterns"></a>Eşleşen desenleri Değiştir

Metin eşleştirme desenlerini, büyük olasılıkla bir desenle tanımlanan yeni metinle değiştirmek için [Normal ifadeleri](../../standard/base-types/regular-expressions.md) kullanabilirsiniz. Aşağıdaki örnek, <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> bir kaynak dizesindeki bir düzeni bulmak ve uygun büyük harfle değiştirmek için sınıfını kullanır. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType>Yöntemi, bağımsız değişkenlerinden biri olarak değiştirme mantığını sağlayan bir işlevi alır. Bu örnekte, bu işlev `LocalReplaceMatchCase` örnek yöntemin içinde belirtilen **yerel bir işlevdir** . `LocalReplaceMatchCase`uygun bir <xref:System.Text.StringBuilder?displayProperty=nameWithType> büyük harfle değiştirme dizesini oluşturmak için sınıfını kullanır.

Normal ifadeler, bilinen metinler yerine bir kalıbı izleyen metni aramak ve değiştirmek için kullanışlıdır. Daha fazla bilgi için bkz. [dizeleri arama](search-strings.md). "The\s" arama deseninin "The" sözcüğünü ve ardından bir boşluk karakteri arar. Bu düzenin bu bölümü, kaynak dizede "orada" ile eşleşmemesini sağlar. Normal ifade dili öğeleri hakkında daha fazla bilgi için bkz. [normal Ifade dili-hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet5":::

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType>Yöntemi, nesnedeki içeriğe sahip sabit bir dize döndürür <xref:System.Text.StringBuilder> .

## <a name="modifying-individual-characters"></a>Tek karakterleri değiştirme

Dizeden bir karakter dizisi oluşturabilir, dizinin içeriğini değiştirebilir ve sonra dizinin değiştirilen içeriğinden yeni bir dize oluşturabilirsiniz.

Aşağıdaki örnek, bir dizedeki bir karakter kümesinin nasıl değiştirileceğini gösterir. İlk olarak, <xref:System.String.ToCharArray?displayProperty=nameWithType> bir karakter dizisi oluşturmak için yöntemini kullanır. <xref:System.String.IndexOf%2A>"Fox" sözcüğünün başlangıç dizinini bulmak için yöntemini kullanır. Sonraki üç karakter, farklı bir sözcükle değiştirilmiştir. Son olarak, güncelleştirilmiş karakter dizisinden yeni bir dize oluşturulur.

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet6":::

## <a name="programmatically-build-up-string-content"></a>Program aracılığıyla dize içeriği oluşturma

Dizeler sabit olduğundan, önceki örneklerin tümü geçici dizeler veya karakter dizileri oluşturur. Yüksek performanslı senaryolarda, bu yığın ayırmalarının oluşmaması istenebilir. .NET Core <xref:System.String.Create%2A?displayProperty=nameWithType> , ara geçici dize ayırmalarını önleyerek bir dizenin karakter içeriğini bir geri çağırma yoluyla programlama yoluyla doldurmanıza olanak sağlayan bir yöntem sağlar.

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs" id="Snippet7":::

Güvenli olmayan koda sahip sabit bir blokta bir dizeyi değiştirebilirsiniz ancak dize oluşturulduktan sonra dize içeriğinin değiştirilmesi **kesinlikle** önerilmez. Bunun yapılması, işlemleri öngörülemeyen yollarla bozacaktır. Örneğin, birisi sizinki ile aynı içeriğe sahip bir dizeyi birbirine kaydetirse, sizin kopyanızı alır ve dizenizi her zaman değiştirmenizi beklemez.

## <a name="see-also"></a>Ayrıca bkz.

- [Normal ifadeleri .NET Framework](../../standard/base-types/regular-expressions.md)
- [Normal ifade dili-hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)
