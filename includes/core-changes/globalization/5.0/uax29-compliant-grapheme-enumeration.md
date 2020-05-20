---
ms.openlocfilehash: c0c1c9c9d8e3aeb6f689f754d09b50b208b54112
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702264"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="6043b-101">StringInfo ve TextElementEnumerator artık UAX29 uyumlu</span><span class="sxs-lookup"><span data-stu-id="6043b-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="6043b-102">Bu değişiklikten önce, <xref:System.Globalization.StringInfo?displayProperty=fullName> <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> Tüm grafem kümelerini düzgün şekilde işlemedi.</span><span class="sxs-lookup"><span data-stu-id="6043b-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="6043b-103">Bazı graphemes, birlikte tutulması yerine bileşen bileşenlerine bölündü.</span><span class="sxs-lookup"><span data-stu-id="6043b-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="6043b-104">Şimdi, <xref:System.Globalization.StringInfo> <xref:System.Globalization.TextElementEnumerator> Unicode standardının en son sürümüne göre grafem kümelerini işleyin.</span><span class="sxs-lookup"><span data-stu-id="6043b-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="6043b-105">Ayrıca, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> Visual Basic bir dizedeki karakterleri ters döndüren yöntem, artık grafem kümeleri için Unicode standardını da izler.</span><span class="sxs-lookup"><span data-stu-id="6043b-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6043b-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="6043b-106">Change description</span></span>

<span data-ttu-id="6043b-107">[Grafem](https://www.unicode.org/glossary/#grapheme) veya [genişletilmiş grafem kümesi](https://www.unicode.org/glossary/#extended_grapheme_cluster) , birden çok Unicode kod noktasından oluşan tek bir kullanıcı tarafından algılanan karakterdir.</span><span class="sxs-lookup"><span data-stu-id="6043b-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="6043b-108">Örneğin, "kaI" () Tayland karakterini içeren dize :::no-loc text="กำ"::: aşağıdaki iki karakterden oluşur:</span><span class="sxs-lookup"><span data-stu-id="6043b-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="6043b-109">:::no-loc text="ก":::(= ' \u0e01 ') TAY DILI KO KAI KARAKTERI</span><span class="sxs-lookup"><span data-stu-id="6043b-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="6043b-110">:::no-loc text=" ำ":::(= ' \u0e33 ') TAY DILI SARA HAR KARAKTERI</span><span class="sxs-lookup"><span data-stu-id="6043b-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="6043b-111">Kullanıcıya görüntülendiğinde, işletim sistemi iki karakteri birleştirerek tek bir görüntüleme karakteri (veya grapheme) "kam" ya da oluşturur :::no-loc text="กำ"::: .</span><span class="sxs-lookup"><span data-stu-id="6043b-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="6043b-112">Emoji Ayrıca, benzer bir şekilde görüntülenmek üzere birleştirilmiş birden fazla karakterden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="6043b-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="6043b-113">.NET belgeleri bazen bir grapheme 'ya başvururken "metin öğesi" terimini kullanır.</span><span class="sxs-lookup"><span data-stu-id="6043b-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="6043b-114"><xref:System.Globalization.StringInfo>Ve <xref:System.Globalization.TextElementEnumerator> sınıfları dizeleri inceler ve içerdikleri grafemes hakkındaki bilgileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="6043b-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="6043b-115">.NET Framework (tüm sürümler) ve .NET Core 3. x ve önceki sürümlerde, bu iki sınıf birleştirme bazı sınıfları işleyen ancak [Unicode standardına](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)tam olarak uyumlu olmayan özel mantık kullanır.</span><span class="sxs-lookup"><span data-stu-id="6043b-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="6043b-116">Örneğin, <xref:System.Globalization.StringInfo> ve sınıfları, <xref:System.Globalization.TextElementEnumerator> tek Tayland "Kad" karakterini birlikte tutmak yerine onun bileşen bileşenlerine doğru şekilde ayırır.</span><span class="sxs-lookup"><span data-stu-id="6043b-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="6043b-117">Bu sınıflar ayrıca "🤷🏽 ♀️" emoji karakterini, tek bir grafem kümesi olarak birlikte tutmak yerine dört kümeye (Person Shrugging, Skin Tone değiştirici, cinsiyet değiştiricisi ve görünmeyen bir birleştirici) yanlış şekilde ayırır.</span><span class="sxs-lookup"><span data-stu-id="6043b-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="6043b-118">.NET 5 ' den itibaren, <xref:System.Globalization.StringInfo> ve <xref:System.Globalization.TextElementEnumerator> sınıfları [Unicode standart ek \# 29, Rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html)tarafından tanımlanan şekilde Unicode standardı uygular.</span><span class="sxs-lookup"><span data-stu-id="6043b-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="6043b-119">Özellikle, artık tüm birleştirme sınıfları için [genişletilmiş grafem kümeleri](https://www.unicode.org/glossary/#extended_grapheme_cluster) döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="6043b-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="6043b-120">Aşağıdaki C# kodunu göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="6043b-120">Consider the following C# code:</span></span>

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

<span data-ttu-id="6043b-121">.NET Framework ve .NET Core 3. x ve önceki sürümlerinde, grak 'lar bölünür ve konsol çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6043b-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="6043b-122">.NET 5 ve sonraki sürümlerinde, graphemes birlikte tutulur ve konsol çıktısı aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="6043b-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="6043b-123">Ayrıca, .NET 5 ' ten itibaren, <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> Visual Basic bir dizedeki karakterleri ters döndüren yöntem, artık grafem kümeleri için Unicode standardını da izler.</span><span class="sxs-lookup"><span data-stu-id="6043b-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="6043b-124">Bu değişiklikler .net <xref:System.Text.Rune?displayProperty=fullName> Core 3,0 ' de bulunan türle birlikte sunulan Unicode skaler değer numaralandırma API 'lerini tamamlamak için genişletilmiş bir grafem kümesi sıralama API 'si de dahil olmak üzere, .net 'teki daha geniş bir Unicode ve UTF-8 geliştirmelerinden oluşan bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="6043b-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6043b-125">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6043b-125">Version introduced</span></span>

<span data-ttu-id="6043b-126">.NET 5,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="6043b-126">.NET 5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6043b-127">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6043b-127">Recommended action</span></span>

<span data-ttu-id="6043b-128">Herhangi bir işlem yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="6043b-128">You don't need to take any action.</span></span> <span data-ttu-id="6043b-129">Uygulamalarınız, Genelleştirme ile ilgili çeşitli senaryolarda otomatik olarak daha fazla standartlara uygun bir şekilde davranır.</span><span class="sxs-lookup"><span data-stu-id="6043b-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

#### <a name="category"></a><span data-ttu-id="6043b-130">Kategori</span><span class="sxs-lookup"><span data-stu-id="6043b-130">Category</span></span>

<span data-ttu-id="6043b-131">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="6043b-131">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6043b-132">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6043b-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
