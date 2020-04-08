---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888182"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo ve TextElementEnumerator artık UAX29 uyumlu

Bu değişiklik önce <xref:System.Globalization.StringInfo?displayProperty=fullName> <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> ve düzgün tüm grafme kümeleri işlemedi. Bazı grafemeler bir arada tutulmak yerine bileşenlerine bölündü. Şimdi, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> ve Unicode Standardı'nın en son sürümüne göre grafen kümeleri işleme.

Buna ek <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> olarak, Visual Basic'teki bir dizedeki karakterleri tersine çeviren yöntem, şimdi grafme kümeleri için Unicode standardını da izler.

#### <a name="change-description"></a>Açıklamayı değiştir

[Grafeme](https://www.unicode.org/glossary/#grapheme) veya [genişletilmiş grafeme kümesi,](https://www.unicode.org/glossary/#extended_grapheme_cluster) birden çok Unicode kod noktasından oluşabilir tek bir kullanıcı tarafından algılanan karakterdir. Örneğin, Tay karakteri "kam" ():::no-loc text="กำ":::içeren dize aşağıdaki iki karakterden oluşur:

- :::no-loc text="ก":::(= '\u0e01') TAY KARAKTER KO KAI
- :::no-loc text=" ำ":::(= '\u0e33') TAY KARAKTER SARA

Kullanıcıya görüntülendiğinde, işletim sistemi tek ekran karakteri (veya grapheme) "kam" veya :::no-loc text="กำ":::. Emoji, benzer şekilde görüntülenmek için birleştirilen birden çok karakterden de oluşabilir.

> [!TIP]
> .NET dokümantasyonu bazen grafiğe atıfta bulunarak "metin öğesi" terimini kullanır.

Ve <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> sınıflar dizeleri inceler ve içerdikleri grafimeler hakkında bilgi döndürün. .NET Framework (tüm sürümler) ve .NET Core 3.x ve daha önce, bu iki sınıf bazı birleştirme sınıfları işleyen ancak [Unicode Standardına](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)tam olarak uymayan özel mantık kullanır. Örneğin, <xref:System.Globalization.StringInfo> ve <xref:System.Globalization.TextElementEnumerator> sınıflar yanlış yerine onları bir arada tutmak yerine kurucu bileşenlerine tek Tay karakteri "kam" bölünmüş. Bu sınıflar ayrıca yanlış bir şekilde emoji karakterini "🤷🏽 ♀️" olarak tek bir grafi kümesi olarak bir arada tutmak yerine dört kümeye (kişi omuz silkme, cilt tonu değiştirici, cinsiyet değiştirici ve görünmez bir birleşimleyici) böler.

.NET 5 ile <xref:System.Globalization.StringInfo> başlayarak, ve <xref:System.Globalization.TextElementEnumerator> sınıflar [Unicode Standart \#Ek 29, rev. 35, sn. 3](https://www.unicode.org/reports/tr29/tr29-35.html)tarafından tanımlanan Unicode standardını uygular. Özellikle, şimdi tüm birleştirici sınıflar için [genişletilmiş grafme kümeleri](https://www.unicode.org/glossary/#extended_grapheme_cluster) döndürün.

Aşağıdaki C# kodunu göz önünde bulundurun:

```cs
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

.NET Framework ve .NET Core 3.x ve önceki sürümlerde grafemeler ayrılır ve konsol çıktısı aşağıdaki gibidir:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

.NET 5 ve sonraki sürümlerde grafemeler bir arada tutulur ve konsol çıktısı aşağıdaki gibidir:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

Buna ek olarak, .NET <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 5'ten başlayarak Visual Basic'teki bir dizedeki karakterleri tersine çeviren yöntem, şimdi grafme kümeleri için Unicode standardını da izler.

Bu değişiklikler, .NET Core 3.0 <xref:System.Text.Rune?displayProperty=fullName> türüyle tanıtılan Unicode skaler değer numaralandırma API'lerini tamamlamak için genişletilmiş bir grafeme küme numaralandırma API'si de dahil olmak üzere .NET'teki daha geniş bir Unicode ve UTF-8 iyileştirmelerinin bir parçasıdır.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

.NET 5.0 Önizleme 1

### <a name="recommended-action"></a>Önerilen eylem

Harekete geçmene gerek yok. Uygulamalarınız, küreselleşmeyle ilgili çeşitli senaryolarda otomatik olarak standartlara uygun bir şekilde davranacaktır.

### <a name="category"></a>Kategori

Genelleştirme

### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
