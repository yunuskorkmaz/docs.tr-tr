---
ms.openlocfilehash: 70b71fc55f76514dd17e5b9ba0e76151a966eebb
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539484"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a>StringInfo ve TextElementEnumerator artık UAX29 uyumlu

Bu değişiklikten önce, <xref:System.Globalization.StringInfo?displayProperty=fullName> <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> Tüm grafem kümelerini düzgün şekilde işlemedi. Bazı graphemes, birlikte tutulması yerine bileşen bileşenlerine bölündü. Şimdi, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> Unicode standardının en son sürümüne göre grafem kümelerini işleyin.

Ayrıca, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> Visual Basic bir dizedeki karakterleri ters döndüren yöntem, artık grafem kümeleri için Unicode standardını da izler.

#### <a name="change-description"></a>Açıklamayı Değiştir

[Grafem](https://www.unicode.org/glossary/#grapheme) veya [genişletilmiş grafem kümesi](https://www.unicode.org/glossary/#extended_grapheme_cluster) , birden çok Unicode kod noktasından oluşan tek bir kullanıcı tarafından algılanan karakterdir. Örneğin, "kaI" () Tayland karakterini içeren dize :::no-loc text="กำ"::: aşağıdaki iki karakterden oluşur:

- :::no-loc text="ก"::: (= ' \u0e01 ') TAY DILI KO KAI KARAKTERI
- :::no-loc text=" ำ"::: (= ' \u0e33 ') TAY DILI SARA HAR KARAKTERI

Kullanıcıya görüntülendiğinde, işletim sistemi iki karakteri birleştirerek tek bir görüntüleme karakteri (veya grapheme) "kam" ya da oluşturur :::no-loc text="กำ"::: . Emoji Ayrıca, benzer bir şekilde görüntülenmek üzere birleştirilmiş birden fazla karakterden oluşabilir.

> [!TIP]
> .NET belgeleri bazen bir grapheme 'ya başvururken "metin öğesi" terimini kullanır.

<xref:System.Globalization.StringInfo>Ve <xref:System.Globalization.TextElementEnumerator> sınıfları dizeleri inceler ve içerdikleri grafemes hakkındaki bilgileri döndürür. .NET Framework (tüm sürümler) ve .NET Core 3. x ve önceki sürümlerde, bu iki sınıf birleştirme bazı sınıfları işleyen ancak [Unicode standardına](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)tam olarak uyumlu olmayan özel mantık kullanır. Örneğin, <xref:System.Globalization.StringInfo> ve sınıfları, <xref:System.Globalization.TextElementEnumerator> tek Tayland "Kad" karakterini birlikte tutmak yerine onun bileşen bileşenlerine doğru şekilde ayırır. Bu sınıflar ayrıca "🤷🏽 ♀️" emoji karakterini, tek bir grafem kümesi olarak birlikte tutmak yerine dört kümeye (Person Shrugging, Skin Tone değiştirici, cinsiyet değiştiricisi ve görünmeyen bir birleştirici) yanlış şekilde ayırır.

.NET 5 ' den itibaren, <xref:System.Globalization.StringInfo> ve <xref:System.Globalization.TextElementEnumerator> sınıfları [Unicode standart ek \# 29, Rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html)tarafından tanımlanan şekilde Unicode standardı uygular. Özellikle, artık tüm birleştirme sınıfları için [genişletilmiş grafem kümeleri](https://www.unicode.org/glossary/#extended_grapheme_cluster) döndürüyor.

Aşağıdaki C# kodunu göz önünde bulundurun:

```csharp
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

.NET Framework ve .NET Core 3. x ve önceki sürümlerinde, grak 'lar bölünür ve konsol çıktısı aşağıdaki gibidir:

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

.NET 5 ve sonraki sürümlerinde, graphemes birlikte tutulur ve konsol çıktısı aşağıdaki gibidir:

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

Ayrıca, .NET 5 ' ten itibaren, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> Visual Basic bir dizedeki karakterleri ters döndüren yöntem, artık grafem kümeleri için Unicode standardını da izler.

Bu değişiklikler .net <xref:System.Text.Rune?displayProperty=fullName> Core 3,0 ' de bulunan türle birlikte sunulan Unicode skaler değer numaralandırma API 'lerini tamamlamak için genişletilmiş bir grafem kümesi sıralama API 'si de dahil olmak üzere, .net 'teki daha geniş bir Unicode ve UTF-8 geliştirmelerinden oluşan bir parçasıdır.

#### <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0 Preview 1

#### <a name="recommended-action"></a>Önerilen eylem

Herhangi bir işlem yapmanız gerekmez. Uygulamalarınız, Genelleştirme ile ilgili çeşitli senaryolarda otomatik olarak daha fazla standartlara uygun bir şekilde davranır.

#### <a name="category"></a>Kategori

Genelleştirme

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
