---
title: Dize içeriğini değiştirme- C# kılavuz
ms.date: 02/26/2018
helpviewer_keywords:
- strings [C#], modifying
ms.openlocfilehash: ecedd9a9027aa925c753f8e187d611b19d3db991
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543267"
---
# <a name="how-to-modify-string-contents-in-c"></a>C\# dize içeriklerini değiştirme

Bu makalede, var olan bir `string`değiştirerek `string` oluşturmak için çeşitli teknikler gösterilmektedir. Gösterilen tüm teknikler, değişikliklerin sonucunu yeni bir `string` nesne olarak döndürür. Bunu açıkça göstermek için örneklerin hepsi, sonucu yeni bir değişkende depolar. Ardından, her bir örneği çalıştırdığınızda hem özgün `string` hem de değişiklikten kaynaklanan `string` inceleyebilirsiniz.

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

Bu makalede çeşitli teknikler verilmiştir. Varolan metni değiştirebilirsiniz. Desen arayabilir ve eşleşen metni başka metinle değiştirebilirsiniz. Bir dizeyi bir karakter dizisi olarak kabul edebilirsiniz. Beyaz alanı kaldırmak için kullanışlı yöntemler de kullanabilirsiniz. Senaryonuza en yakından eşleşen teknikleri seçmeniz gerekir.

## <a name="replace-text"></a>Metni Değiştir

Aşağıdaki kod, var olan metni bir değiştirme ile değiştirerek yeni bir dize oluşturur.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#1)]

Yukarıdaki kod, dizelerin bu *sabit* özelliğini gösterir. Önceki örnekte, `source`özgün dizesinin değiştirilmediğini görebilirsiniz. <xref:System.String.Replace%2A?displayProperty=nameWithType> yöntemi, değişiklikleri içeren yeni bir `string` oluşturur.

<xref:System.String.Replace%2A> yöntemi dizeleri ya da tek karakterleri değiştirebilir. Her iki durumda da, aranan metnin her oluşumu değiştirilmiştir.  Aşağıdaki örnek tüm ' ' karakterlerini '\_' ile değiştirir:

[!code-csharp-interactive[replace characters](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#2)]

Kaynak dize değiştirilmez ve yeni bir dize değiştirme ile birlikte döndürülür.

## <a name="trim-white-space"></a>Boşluğu Kırp

Baştaki veya sondaki boşlukları kaldırmak için <xref:System.String.Trim%2A?displayProperty=nameWithType>, <xref:System.String.TrimStart%2A?displayProperty=nameWithType>ve <xref:System.String.TrimEnd%2A?displayProperty=nameWithType> yöntemlerini kullanabilirsiniz.  Aşağıdaki kod, her birine bir örnek gösterir. Kaynak dize değişmez; Bu yöntemler, değiştirilen içeriğe sahip yeni bir dize döndürür.

[!code-csharp-interactive[trim white space](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#3)]

## <a name="remove-text"></a>Metni kaldır

<xref:System.String.Remove%2A?displayProperty=nameWithType> yöntemi kullanarak bir dizeden metin kaldırabilirsiniz. Bu yöntem, belirli bir dizinden başlayarak birkaç karakteri kaldırır. Aşağıdaki örnek, bir dizeden metin kaldırmak için <xref:System.String.Remove%2A> tarafından izlenen <xref:System.String.IndexOf%2A?displayProperty=nameWithType> nasıl kullanacağınızı gösterir:

[!code-csharp-interactive[remove text](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#4)]

## <a name="replace-matching-patterns"></a>Eşleşen desenleri Değiştir

Metin eşleştirme desenlerini, büyük olasılıkla bir desenle tanımlanan yeni metinle değiştirmek için [Normal ifadeleri](../../standard/base-types/regular-expressions.md) kullanabilirsiniz. Aşağıdaki örnek, bir kaynak dizesindeki bir düzeni bulmak ve uygun büyük harfle değiştirmek için <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> sınıfını kullanır. <xref:System.Text.RegularExpressions.Regex.Replace(System.String,System.String,System.Text.RegularExpressions.MatchEvaluator,System.Text.RegularExpressions.RegexOptions)?displayProperty=nameWithType> yöntemi, bağımsız değişkenlerinden biri olarak değiştirme mantığını sağlayan bir işlevi alır. Bu örnekte, `LocalReplaceMatchCase` işlevi örnek yöntemin içinde belirtilen **yerel bir işlevdir** . `LocalReplaceMatchCase`, doğru büyük küçük harfe sahip değiştirme dizesini oluşturmak için <xref:System.Text.StringBuilder?displayProperty=nameWithType> sınıfını kullanır.

Normal ifadeler, bilinen metinler yerine bir kalıbı izleyen metni aramak ve değiştirmek için kullanışlıdır. Daha fazla ayrıntı için bkz. [dizeleri arama](search-strings.md) . "The\s" arama deseninin "The" sözcüğünü ve ardından bir boşluk karakteri arar. Bu düzenin bu bölümü, kaynak dizede "orada" ile eşleşmemesini sağlar. Normal ifade dili öğeleri hakkında daha fazla bilgi için bkz. [normal Ifade dili-hızlı başvuru](../../standard/base-types/regular-expression-language-quick-reference.md).

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#5)]

<xref:System.Text.StringBuilder.ToString%2A?displayProperty=nameWithType> yöntemi, <xref:System.Text.StringBuilder> nesnesindeki içeriğe sahip sabit bir dize döndürür.

## <a name="modifying-individual-characters"></a>Tek karakterleri değiştirme

Dizeden bir karakter dizisi oluşturabilir, dizinin içeriğini değiştirebilir ve sonra dizinin değiştirilen içeriğinden yeni bir dize oluşturabilirsiniz.

Aşağıdaki örnek, bir dizedeki bir karakter kümesinin nasıl değiştirileceğini gösterir. İlk olarak, bir karakter dizisi oluşturmak için <xref:System.String.ToCharArray?displayProperty=nameWithName> yöntemini kullanır. "Fox" sözcüğünün başlangıç dizinini bulmak için <xref:System.String.IndexOf%2A> yöntemini kullanır. Sonraki üç karakter, farklı bir sözcükle değiştirilmiştir. Son olarak, güncelleştirilmiş karakter dizisinden yeni bir dize oluşturulur.

[!code-csharp-interactive[replace creates a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#6)]

## <a name="programmatically-build-up-string-content"></a>Program aracılığıyla dize içeriği oluşturma

Dizeler sabit olduğundan, önceki örneklerin tümü geçici dizeler veya karakter dizileri oluşturur. Yüksek performans senaryolarında bu yığın ayırmalarının oluşmaması istenebilir. .NET Core, ara geçici dize ayırmalarını önleyerek bir dizenin karakter içeriğini bir geri çağırma yoluyla programlama yoluyla doldurmanıza olanak sağlayan bir <xref:System.String.Create%2A?displayProperty=nameWithType> yöntemi sağlar.

[!code-csharp[using string.Create to programmatically build the string content for a new string](../../../samples/snippets/csharp/how-to/strings/ModifyStrings.cs#7)]

Güvenli olmayan koda sahip sabit bir blokta bir dizeyi değiştirebilirsiniz ancak dize oluşturulduktan sonra dize içeriğinin değiştirilmesi **kesinlikle** önerilmez. Bunun yapılması, işlemleri öngörülemeyen yollarla bozacaktır. Örneğin, birisi sizinki ile aynı içeriğe sahip bir dizeyi birbirine kaydetirse, sizin kopyanızı alır ve dizenizi her zaman değiştirmenizi beklemez.

Bu örnekleri, [GitHub deponuzdaki](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/strings)koda bakarak deneyebilirsiniz. Ya da örnekleri [zip dosyası olarak](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/strings.zip)indirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Normal Ifadeleri .NET Framework](../../standard/base-types/regular-expressions.md)
- [Normal İfade Dili - Hızlı Başvuru](../../standard/base-types/regular-expression-language-quick-reference.md)
