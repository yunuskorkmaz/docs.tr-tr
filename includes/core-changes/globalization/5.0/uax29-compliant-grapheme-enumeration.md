---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888182"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="81963-101">StringInfo ve TextElementEnumerator artık UAX29 uyumlu</span><span class="sxs-lookup"><span data-stu-id="81963-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="81963-102">Bu değişiklik önce <xref:System.Globalization.StringInfo?displayProperty=fullName> <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> ve düzgün tüm grafme kümeleri işlemedi.</span><span class="sxs-lookup"><span data-stu-id="81963-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="81963-103">Bazı grafemeler bir arada tutulmak yerine bileşenlerine bölündü.</span><span class="sxs-lookup"><span data-stu-id="81963-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="81963-104">Şimdi, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> ve Unicode Standardı'nın en son sürümüne göre grafen kümeleri işleme.</span><span class="sxs-lookup"><span data-stu-id="81963-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="81963-105">Buna ek <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> olarak, Visual Basic'teki bir dizedeki karakterleri tersine çeviren yöntem, şimdi grafme kümeleri için Unicode standardını da izler.</span><span class="sxs-lookup"><span data-stu-id="81963-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="81963-106">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="81963-106">Change description</span></span>

<span data-ttu-id="81963-107">[Grafeme](https://www.unicode.org/glossary/#grapheme) veya [genişletilmiş grafeme kümesi,](https://www.unicode.org/glossary/#extended_grapheme_cluster) birden çok Unicode kod noktasından oluşabilir tek bir kullanıcı tarafından algılanan karakterdir.</span><span class="sxs-lookup"><span data-stu-id="81963-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="81963-108">Örneğin, Tay karakteri "kam" ():::no-loc text="กำ":::içeren dize aşağıdaki iki karakterden oluşur:</span><span class="sxs-lookup"><span data-stu-id="81963-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="81963-109">:::no-loc text="ก":::(= '\u0e01') TAY KARAKTER KO KAI</span><span class="sxs-lookup"><span data-stu-id="81963-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="81963-110">:::no-loc text=" ำ":::(= '\u0e33') TAY KARAKTER SARA</span><span class="sxs-lookup"><span data-stu-id="81963-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="81963-111">Kullanıcıya görüntülendiğinde, işletim sistemi tek ekran karakteri (veya grapheme) "kam" veya :::no-loc text="กำ":::.</span><span class="sxs-lookup"><span data-stu-id="81963-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="81963-112">Emoji, benzer şekilde görüntülenmek için birleştirilen birden çok karakterden de oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="81963-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="81963-113">.NET dokümantasyonu bazen grafiğe atıfta bulunarak "metin öğesi" terimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="81963-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="81963-114">Ve <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> sınıflar dizeleri inceler ve içerdikleri grafimeler hakkında bilgi döndürün.</span><span class="sxs-lookup"><span data-stu-id="81963-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="81963-115">.NET Framework (tüm sürümler) ve .NET Core 3.x ve daha önce, bu iki sınıf bazı birleştirme sınıfları işleyen ancak [Unicode Standardına](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)tam olarak uymayan özel mantık kullanır.</span><span class="sxs-lookup"><span data-stu-id="81963-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="81963-116">Örneğin, <xref:System.Globalization.StringInfo> ve <xref:System.Globalization.TextElementEnumerator> sınıflar yanlış yerine onları bir arada tutmak yerine kurucu bileşenlerine tek Tay karakteri "kam" bölünmüş.</span><span class="sxs-lookup"><span data-stu-id="81963-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="81963-117">Bu sınıflar ayrıca yanlış bir şekilde emoji karakterini "🤷🏽 ♀️" olarak tek bir grafi kümesi olarak bir arada tutmak yerine dört kümeye (kişi omuz silkme, cilt tonu değiştirici, cinsiyet değiştirici ve görünmez bir birleşimleyici) böler.</span><span class="sxs-lookup"><span data-stu-id="81963-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="81963-118">.NET 5 ile <xref:System.Globalization.StringInfo> başlayarak, ve <xref:System.Globalization.TextElementEnumerator> sınıflar [Unicode Standart \#Ek 29, rev. 35, sn. 3](https://www.unicode.org/reports/tr29/tr29-35.html)tarafından tanımlanan Unicode standardını uygular.</span><span class="sxs-lookup"><span data-stu-id="81963-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="81963-119">Özellikle, şimdi tüm birleştirici sınıflar için [genişletilmiş grafme kümeleri](https://www.unicode.org/glossary/#extended_grapheme_cluster) döndürün.</span><span class="sxs-lookup"><span data-stu-id="81963-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="81963-120">Aşağıdaki C# kodunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="81963-120">Consider the following C# code:</span></span>

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

<span data-ttu-id="81963-121">.NET Framework ve .NET Core 3.x ve önceki sürümlerde grafemeler ayrılır ve konsol çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="81963-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="81963-122">.NET 5 ve sonraki sürümlerde grafemeler bir arada tutulur ve konsol çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="81963-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="81963-123">Buna ek olarak, .NET <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 5'ten başlayarak Visual Basic'teki bir dizedeki karakterleri tersine çeviren yöntem, şimdi grafme kümeleri için Unicode standardını da izler.</span><span class="sxs-lookup"><span data-stu-id="81963-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="81963-124">Bu değişiklikler, .NET Core 3.0 <xref:System.Text.Rune?displayProperty=fullName> türüyle tanıtılan Unicode skaler değer numaralandırma API'lerini tamamlamak için genişletilmiş bir grafeme küme numaralandırma API'si de dahil olmak üzere .NET'teki daha geniş bir Unicode ve UTF-8 iyileştirmelerinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="81963-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="81963-125">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="81963-125">Version introduced</span></span>

<span data-ttu-id="81963-126">.NET 5.0 Önizleme 1</span><span class="sxs-lookup"><span data-stu-id="81963-126">.NET 5.0 Preview 1</span></span>

### <a name="recommended-action"></a><span data-ttu-id="81963-127">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="81963-127">Recommended action</span></span>

<span data-ttu-id="81963-128">Harekete geçmene gerek yok.</span><span class="sxs-lookup"><span data-stu-id="81963-128">You don't need to take any action.</span></span> <span data-ttu-id="81963-129">Uygulamalarınız, küreselleşmeyle ilgili çeşitli senaryolarda otomatik olarak standartlara uygun bir şekilde davranacaktır.</span><span class="sxs-lookup"><span data-stu-id="81963-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

### <a name="category"></a><span data-ttu-id="81963-130">Kategori</span><span class="sxs-lookup"><span data-stu-id="81963-130">Category</span></span>

<span data-ttu-id="81963-131">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="81963-131">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="81963-132">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="81963-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
