---
title: .NET 5 + ' da dizeleri karşılaştırırken davranış değişiklikleri
description: .NET 5 ve sonraki Windows sürümlerindeki dize karşılaştırma davranışı değişiklikleri hakkında bilgi edinin.
ms.date: 12/07/2020
ms.openlocfilehash: a53c36b31785fb43c0aa5f5040042abb6d40031a
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851757"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a><span data-ttu-id="3dacc-103">.NET 5 + ' da dizeleri karşılaştırırken davranış değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3dacc-103">Behavior changes when comparing strings on .NET 5+</span></span>

<span data-ttu-id="3dacc-104">.NET 5,0, genelleştirme API 'Lerinin artık tüm desteklenen platformlar arasında [Varsayılan olarak ICU 'yi kullandığı](../../core/compatibility/globalization/5.0/icu-globalization-api.md) bir çalışma zamanı davranış değişikliği sunar.</span><span class="sxs-lookup"><span data-stu-id="3dacc-104">.NET 5.0 introduces a runtime behavioral change where globalization APIs [now use ICU by default](../../core/compatibility/globalization/5.0/icu-globalization-api.md) across all supported platforms.</span></span> <span data-ttu-id="3dacc-105">Bu, önceki .NET Core sürümlerinden ve Windows üzerinde çalışırken işletim sisteminin ulusal dil desteği (NLS) işlevselliğini kullanan .NET Framework bir sistemdir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-105">This is a departure from earlier versions of .NET Core and from .NET Framework, which utilize the operating system's national language support (NLS) functionality when running on Windows.</span></span> <span data-ttu-id="3dacc-106">Bu değişiklikler hakkında daha fazla bilgi için, davranış değişikliğini alan uyumluluk anahtarları dahil, bkz. [.NET Genelleştirme ve ıCU](../globalization-localization/globalization-icu.md).</span><span class="sxs-lookup"><span data-stu-id="3dacc-106">For more information on these changes, including compatibility switches that can revert the behavior change, see [.NET globalization and ICU](../globalization-localization/globalization-icu.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3dacc-107">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3dacc-107">Reason for change</span></span>

<span data-ttu-id="3dacc-108">Bu değişiklik, birleştirme için sunulmuştur. Tüm desteklenen işletim sistemleri genelinde NET ' in Genelleştirme davranışı.</span><span class="sxs-lookup"><span data-stu-id="3dacc-108">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="3dacc-109">Ayrıca, uygulamaların işletim sisteminin yerleşik kitaplıklarına göre değil, kendi Genelleştirme kitaplıklarını paketleyebilme olanağı da sağlar.</span><span class="sxs-lookup"><span data-stu-id="3dacc-109">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the OS's built-in libraries.</span></span> <span data-ttu-id="3dacc-110">Daha fazla bilgi için bkz. [Son değişiklik bildirimi](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span><span class="sxs-lookup"><span data-stu-id="3dacc-110">For more information, see [the breaking change notification](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="3dacc-111">Davranış farkları</span><span class="sxs-lookup"><span data-stu-id="3dacc-111">Behavioral differences</span></span>

<span data-ttu-id="3dacc-112">`string.IndexOf(string)`Bir bağımsız değişken alan aşırı yüklemeyi çağırmadan gibi işlevleri kullanırsanız <xref:System.StringComparison> , bir *sıra* araması gerçekleştirmeyi düşünebilirsiniz, bunun yerine kültüre özgü davranışa istemeden bir bağımlılık yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-112">If you use functions like `string.IndexOf(string)` without calling the overload that takes a <xref:System.StringComparison> argument, you might intend to perform an *ordinal* search, but instead you inadvertently take a dependency on culture-specific behavior.</span></span> <span data-ttu-id="3dacc-113">NLS ve ıCU, dil karşılaştırıcılarında farklı mantık uygulamayı yaptığından, gibi yöntemlerin sonuçları `string.IndexOf(string)` beklenmedik değerler döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-113">Since NLS and ICU implement different logic in their linguistic comparers, the results of methods like `string.IndexOf(string)` can return unexpected values.</span></span>

<span data-ttu-id="3dacc-114">Bu, her zaman Genelleştirme tesislerinin etkin olmasını beklemeyen yerlerde bile kendi kendine bildirimde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-114">This can manifest itself even in places where you aren't always expecting globalization facilities to be active.</span></span> <span data-ttu-id="3dacc-115">Örneğin, aşağıdaki kod, geçerli çalışma zamanına bağlı olarak farklı bir yanıt oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-115">For example, the following code can produce a different answer depending on the current runtime.</span></span>

```cs
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);

// The snippet prints:
//
// '6' when running on .NET Framework (Windows)
// '6' when running on .NET Core 2.x - 3.x (Windows)
// '-1' when running on .NET 5 (Windows)
// '-1' when running on .NET Core 2.x - 3.x or .NET 5 (non-Windows)
// '6' when running on .NET Core 2.x or .NET 5 (in invariant mode)
```

## <a name="guard-against-unexpected-behavior"></a><span data-ttu-id="3dacc-116">Beklenmeyen davranışa karşı koruma</span><span class="sxs-lookup"><span data-stu-id="3dacc-116">Guard against unexpected behavior</span></span>

<span data-ttu-id="3dacc-117">Bu bölümde, .NET 5,0 ' deki beklenmedik davranış değişiklikleriyle ilgili iki seçenek sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-117">This section provides two options for dealing with unexpected behavior changes in .NET 5.0.</span></span>

### <a name="enable-code-analyzers"></a><span data-ttu-id="3dacc-118">Kod Çözümleyicileri etkinleştir</span><span class="sxs-lookup"><span data-stu-id="3dacc-118">Enable code analyzers</span></span>

<span data-ttu-id="3dacc-119">[Kod Çözümleyicileri](../../fundamentals/code-analysis/overview.md) , muhtemelen önemlidir çağrı sitelerini algılayabilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-119">[Code analyzers](../../fundamentals/code-analysis/overview.md) can detect possibly buggy call sites.</span></span> <span data-ttu-id="3dacc-120">Herhangi bir ortaya çıkacak davranışa karşı koruma sağlamaya yardımcı olmak için, projenizde .NET derleyici platformu (Roslyn) Çözümleyicileri etkinleştirmenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="3dacc-120">To help guard against any surprising behaviors, we recommend enabling .NET compiler platform (Roslyn) analyzers in your project.</span></span> <span data-ttu-id="3dacc-121">Çözümleyiciler, bir sıralı karşılaştırıcı büyük olasılıkla tasarlandıysa, istemeden bir dil karşılaştırıcısı kullanmanın farkında olabilecek kodu işaret eder.</span><span class="sxs-lookup"><span data-stu-id="3dacc-121">The analyzers help flag code that might inadvertently be using a linguistic comparer when an ordinal comparer was likely intended.</span></span> <span data-ttu-id="3dacc-122">Aşağıdaki kurallar, bu sorunları bayrağa getirmenize yardımcı olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="3dacc-122">The following rules should help flag these issues:</span></span>

- [<span data-ttu-id="3dacc-123">CA1307: Daha anlaşılır olması için StringComparison belirtin</span><span class="sxs-lookup"><span data-stu-id="3dacc-123">CA1307: Specify StringComparison for clarity</span></span>](../../fundamentals/code-analysis/quality-rules/ca1307.md)
- [<span data-ttu-id="3dacc-124">CA1309: Sıralı StringComparison kullanın</span><span class="sxs-lookup"><span data-stu-id="3dacc-124">CA1309: Use ordinal StringComparison</span></span>](../../fundamentals/code-analysis/quality-rules/ca1309.md)
- [<span data-ttu-id="3dacc-125">CA1310: Doğruluk için StringComparison belirtin</span><span class="sxs-lookup"><span data-stu-id="3dacc-125">CA1310: Specify StringComparison for correctness</span></span>](../../fundamentals/code-analysis/quality-rules/ca1310.md)

<span data-ttu-id="3dacc-126">Bu özel kurallar varsayılan olarak etkinleştirilmemiştir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-126">These specific rules aren't enabled by default.</span></span> <span data-ttu-id="3dacc-127">Bunları etkinleştirmek ve derleme hatası olarak herhangi bir ihlali göstermek için, proje dosyanızda aşağıdaki özellikleri ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="3dacc-127">To enable them and show any violations as build errors, set the following properties in your project file:</span></span>

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
  <WarningsAsErrors>$(WarningsAsErrors);CA1307;CA1309;CA1310</WarningsAsErrors>
</PropertyGroup>
```

<span data-ttu-id="3dacc-128">Aşağıdaki kod parçacığında ilgili kod Çözümleyicisi uyarılarını veya hatalarını üreten kod örnekleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-128">The following snippet shows examples of code that produces the relevant code analyzer warnings or errors.</span></span>

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1310 for string; CA1307 matches on char ','
int idx = s.IndexOf(",");
Console.WriteLine(idx);

//
// Corrected code - matches the literal substring ",".
//
string s = GetString();
int idx = s.IndexOf(",", StringComparison.Ordinal);
Console.WriteLine(idx);

//
// Corrected code (alternative) - searches for the literal ',' character.
//
string s = GetString();
int idx = s.IndexOf(',');
Console.WriteLine(idx);
```

<span data-ttu-id="3dacc-129">Benzer şekilde, bir dizi dizeyi veya varolan dize tabanlı bir koleksiyonu sıralarken bir açık karşılaştırıcı belirtin.</span><span class="sxs-lookup"><span data-stu-id="3dacc-129">Similarly, when instantiating a sorted collection of strings or sorting an existing string-based collection, specify an explicit comparer.</span></span>

```cs
//
// Potentially incorrect code - behavior might vary based on locale.
//
SortedSet<string> mySet = new SortedSet<string>();
List<string> list = GetListOfStrings();
list.Sort();

//
// Corrected code - uses ordinal sorting; doesn't vary by locale.
//
SortedSet<string> mySet = new SortedSet<string>(StringComparer.Ordinal);
List<string> list = GetListOfStrings();
list.Sort(StringComparer.Ordinal);
```

### <a name="revert-back-to-nls-behaviors"></a><span data-ttu-id="3dacc-130">NLS davranışlarına geri dön</span><span class="sxs-lookup"><span data-stu-id="3dacc-130">Revert back to NLS behaviors</span></span>

<span data-ttu-id="3dacc-131">.NET 5 uygulamalarını Windows üzerinde çalışırken eski NLS davranışlarına geri dönmek için [.NET Genelleştirme ve ıCU](../globalization-localization/globalization-icu.md)içindeki adımları izleyin.</span><span class="sxs-lookup"><span data-stu-id="3dacc-131">To revert .NET 5 applications back to older NLS behaviors when running on Windows, follow the steps in [.NET Globalization and ICU](../globalization-localization/globalization-icu.md).</span></span> <span data-ttu-id="3dacc-132">Bu uygulama genelinde uyumluluk anahtarı, uygulama düzeyinde ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-132">This application-wide compatibility switch must be set at the application level.</span></span> <span data-ttu-id="3dacc-133">Tek tek kitaplıklar bu davranışı kabul edebilir veya devre dışı bırakılamaz.</span><span class="sxs-lookup"><span data-stu-id="3dacc-133">Individual libraries cannot opt-in or opt-out of this behavior.</span></span>

> [!TIP]
> <span data-ttu-id="3dacc-134">Kod durumu 'yı artırmaya ve var olan tüm hata hatalarını bulmaya yardımcı olması için [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md), [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md)ve [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) kod analizi kurallarını etkinleştirmenizi önemle öneririz.</span><span class="sxs-lookup"><span data-stu-id="3dacc-134">We strongly recommend you enable the [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md), [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md), and [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) code analysis rules to help improve code hygiene and discover any existing latent bugs.</span></span> <span data-ttu-id="3dacc-135">Daha fazla bilgi için bkz. [kod Çözümleyicileri etkinleştirme](#enable-code-analyzers).</span><span class="sxs-lookup"><span data-stu-id="3dacc-135">For more information, see [Enable code analyzers](#enable-code-analyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="3dacc-136">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3dacc-136">Affected APIs</span></span>

<span data-ttu-id="3dacc-137">.NET 5,0 ' deki değişiklikler nedeniyle .NET uygulamalarının çoğu beklenmeyen davranışlarla karşılaşmaz.</span><span class="sxs-lookup"><span data-stu-id="3dacc-137">Most .NET applications won't encounter any unexpected behaviors due to the changes in .NET 5.0.</span></span> <span data-ttu-id="3dacc-138">Ancak, etkilenen API 'lerin sayısı ve bu API 'Lerin daha geniş .NET ekosistemine ne olduğu konusunda, istenmeyen davranışları ortaya çıkarmak veya uygulamanızda zaten mevcut olan görünmeyen hataları ortaya çıkarmak için .NET 5,0 potansiyelini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-138">However, due to the number of affected APIs and how foundational these APIs are to the wider .NET ecosystem, you should be aware of the potential for .NET 5.0 to introduce unwanted behaviors or to expose latent bugs that already exist in your application.</span></span>

<span data-ttu-id="3dacc-139">Etkilenen API 'Ler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="3dacc-139">The affected APIs include:</span></span>

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <span data-ttu-id="3dacc-140"><xref:System.Globalization.TextInfo?displayProperty=fullName> (çoğu üye)</span><span class="sxs-lookup"><span data-stu-id="3dacc-140"><xref:System.Globalization.TextInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="3dacc-141"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (çoğu üye)</span><span class="sxs-lookup"><span data-stu-id="3dacc-141"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="3dacc-142"><xref:System.Array.Sort%2A?displayProperty=fullName> (dize dizilerini sıralarken)</span><span class="sxs-lookup"><span data-stu-id="3dacc-142"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting arrays of strings)</span></span>
- <span data-ttu-id="3dacc-143"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (liste öğeleri dizeler olduğunda)</span><span class="sxs-lookup"><span data-stu-id="3dacc-143"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="3dacc-144"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (anahtarlar dizeler olduğunda)</span><span class="sxs-lookup"><span data-stu-id="3dacc-144"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="3dacc-145"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (anahtarlar dizeler olduğunda)</span><span class="sxs-lookup"><span data-stu-id="3dacc-145"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="3dacc-146"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (küme dizeler içerdiğinde)</span><span class="sxs-lookup"><span data-stu-id="3dacc-146"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

> [!NOTE]
> <span data-ttu-id="3dacc-147">Bu, etkilenen API 'lerin ayrıntılı bir listesi değildir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-147">This is not an exhaustive list of affected APIs.</span></span>

<span data-ttu-id="3dacc-148">Yukarıdaki tüm API 'Ler, varsayılan olarak iş parçacığının [geçerli kültürünü](xref:System.Threading.Thread.CurrentCulture)kullanarak *dilsel* dize aramayı ve karşılaştırmayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-148">All of the above APIs use *linguistic* string searching and comparison using the thread's [current culture](xref:System.Threading.Thread.CurrentCulture), by default.</span></span> <span data-ttu-id="3dacc-149">*Dilsel* ve *sıralı* arama ve karşılaştırma arasındaki farklılıklar, [Ordinal ve dilsel arama ve karşılaştırma](#ordinal-vs-linguistic-search-and-comparison)bakımından çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-149">The differences between *linguistic* and *ordinal* search and comparison are called out in the [Ordinal vs. linguistic search and comparison](#ordinal-vs-linguistic-search-and-comparison).</span></span>

<span data-ttu-id="3dacc-150">ICU, .NET Core veya .NET Framework önceki bir sürümünden .NET 5,0 ' e yükseltme yapan ve etkilenen API 'lerden birini çağıran, API 'lerin farklı davranışlar sergilediğine yönelik olarak, dil dizesi karşılaştırmaları, Microsoft 'un önceki bir sürümünden farklı olan Windows tabanlı uygulamalar 'dan farklı bir şekilde uygular.</span><span class="sxs-lookup"><span data-stu-id="3dacc-150">Because ICU implements linguistic string comparisons differently from NLS, Windows-based applications that upgrade to .NET 5.0 from an earlier version of .NET Core or .NET Framework and that call one of the affected APIs may notice that the APIs begin exhibiting different behaviors.</span></span>

### <a name="exceptions"></a><span data-ttu-id="3dacc-151">Özel Durumlar</span><span class="sxs-lookup"><span data-stu-id="3dacc-151">Exceptions</span></span>

* <span data-ttu-id="3dacc-152">Bir API açık `StringComparison` veya parametre kabul ediyorsa `CultureInfo` , bu parametre API 'nin varsayılan davranışını geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="3dacc-152">If an API accepts an explicit `StringComparison` or `CultureInfo` parameter, that parameter overrides the API's default behavior.</span></span>
* <span data-ttu-id="3dacc-153">`System.String` İlk parametrenin türünde olduğu Üyeler `char` (örneğin, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType> ), veya belirten bir açık bağımsız değişken geçirmediği takdirde sıralı arama kullanın `StringComparison` `CurrentCulture[IgnoreCase]` `InvariantCulture[IgnoreCase]` .</span><span class="sxs-lookup"><span data-stu-id="3dacc-153">`System.String` members where the first parameter is of type `char` (for example, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>) use ordinal searching, unless the caller passes an explicit `StringComparison` argument that specifies `CurrentCulture[IgnoreCase]` or `InvariantCulture[IgnoreCase]`.</span></span>

<span data-ttu-id="3dacc-154">Her API 'nin varsayılan davranışının daha ayrıntılı bir analizi için <xref:System.String> , [varsayılan arama ve karşılaştırma türleri](#default-search-and-comparison-types) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3dacc-154">For a more detailed analysis of the default behavior of each <xref:System.String> API, see the [Default search and comparison types](#default-search-and-comparison-types) section.</span></span>

## <a name="ordinal-vs-linguistic-search-and-comparison"></a><span data-ttu-id="3dacc-155">Ordinal ve dilsel arama ve karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="3dacc-155">Ordinal vs. linguistic search and comparison</span></span>

<span data-ttu-id="3dacc-156">*Sıra sayısı* ( *dil olmayan*) arama ve karşılaştırma, bir dizeyi tek tek öğelerine ayırır ve bir Char- `char` by-char araması veya karşılaştırması gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-156">*Ordinal* (also known as *non-linguistic*) search and comparison decomposes a string into its individual `char` elements and performs a char-by-char search or comparison.</span></span> <span data-ttu-id="3dacc-157">Örneğin, `"dog"` `"dog"` *equal* `Ordinal` iki dize tam olarak aynı karakter sırasından bulunduğundan, dizeler ve bir karşılaştırıcı altında eşit olarak karşılaştırın.</span><span class="sxs-lookup"><span data-stu-id="3dacc-157">For example, the strings `"dog"` and `"dog"` compare as *equal* under an `Ordinal` comparer, since the two strings consist of the exact same sequence of chars.</span></span> <span data-ttu-id="3dacc-158">Ancak, `"dog"` `"Dog"` tam olarak aynı karakter dizisinden oluşmadığından, bir karşılaştırıcı altında *eşit değildir* olarak karşılaştırın `Ordinal` .</span><span class="sxs-lookup"><span data-stu-id="3dacc-158">However, `"dog"` and `"Dog"` compare as *not equal* under an `Ordinal` comparer, because they don't consist of the exact same sequence of chars.</span></span> <span data-ttu-id="3dacc-159">Diğer bir deyişle, büyük harfli `'D'` kod noktası, `U+0044` küçük harfli kod noktası öncesinde oluşur `'d'` `U+0064` ve daha `"dog"` önce sıralamaya neden olur `"Dog"` .</span><span class="sxs-lookup"><span data-stu-id="3dacc-159">That is, uppercase `'D'`'s code point `U+0044` occurs before lowercase `'d'`'s code point `U+0064`, resulting in `"dog"` sorting before `"Dog"`.</span></span>

<span data-ttu-id="3dacc-160">Bir `OrdinalIgnoreCase` karşılaştırıcı, char-char temelinde hala çalışır, ancak işlemi gerçekleştirirken büyük/küçük harf farklarını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-160">An `OrdinalIgnoreCase` comparer still operates on a char-by-char basis, but it eliminates case differences while performing the operation.</span></span> <span data-ttu-id="3dacc-161">Bir karşılaştırıcı altında char, `OrdinalIgnoreCase` `'d'` `'D'` ve karakter çiftleri ve gibi *eşit* olarak karşılaştırılmaktadır `'á'` `'Á'` .</span><span class="sxs-lookup"><span data-stu-id="3dacc-161">Under an `OrdinalIgnoreCase` comparer, the char pairs `'d'` and `'D'` compare as *equal*, as do the char pairs `'á'` and `'Á'`.</span></span> <span data-ttu-id="3dacc-162">Ancak, vurgusuz karakter, `'a'` aksanlı char *değerine eşit değil* olarak karşılaştırılmaktadır `'á'` .</span><span class="sxs-lookup"><span data-stu-id="3dacc-162">But the unaccented char `'a'` compares as *not equal* to the accented char `'á'`.</span></span>

<span data-ttu-id="3dacc-163">Bunun bazı örnekleri aşağıdaki tabloda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="3dacc-163">Some examples of this are provided in the following table:</span></span>

| <span data-ttu-id="3dacc-164">Dize 1</span><span class="sxs-lookup"><span data-stu-id="3dacc-164">String 1</span></span> | <span data-ttu-id="3dacc-165">Dize 2</span><span class="sxs-lookup"><span data-stu-id="3dacc-165">String 2</span></span> | <span data-ttu-id="3dacc-166">`Ordinal` Il</span><span class="sxs-lookup"><span data-stu-id="3dacc-166">`Ordinal` comparison</span></span> | <span data-ttu-id="3dacc-167">`OrdinalIgnoreCase` Il</span><span class="sxs-lookup"><span data-stu-id="3dacc-167">`OrdinalIgnoreCase` comparison</span></span> |
|---|---|---|---|
| `"dog"` | `"dog"` | <span data-ttu-id="3dacc-168">equal</span><span class="sxs-lookup"><span data-stu-id="3dacc-168">equal</span></span> | <span data-ttu-id="3dacc-169">equal</span><span class="sxs-lookup"><span data-stu-id="3dacc-169">equal</span></span> |
| `"dog"` | `"Dog"` | <span data-ttu-id="3dacc-170">eşit değildir</span><span class="sxs-lookup"><span data-stu-id="3dacc-170">not equal</span></span> | <span data-ttu-id="3dacc-171">equal</span><span class="sxs-lookup"><span data-stu-id="3dacc-171">equal</span></span> |
| `"resume"` | `"Resume"` | <span data-ttu-id="3dacc-172">eşit değildir</span><span class="sxs-lookup"><span data-stu-id="3dacc-172">not equal</span></span> | <span data-ttu-id="3dacc-173">equal</span><span class="sxs-lookup"><span data-stu-id="3dacc-173">equal</span></span> |
| `"resume"` | `"résumé"` | <span data-ttu-id="3dacc-174">eşit değildir</span><span class="sxs-lookup"><span data-stu-id="3dacc-174">not equal</span></span> | <span data-ttu-id="3dacc-175">eşit değildir</span><span class="sxs-lookup"><span data-stu-id="3dacc-175">not equal</span></span> |

<span data-ttu-id="3dacc-176">Unicode Ayrıca dizelerin birçok farklı bellek içi gösterimlerine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="3dacc-176">Unicode also allows strings to have several different in-memory representations.</span></span> <span data-ttu-id="3dacc-177">Örneğin, bir e-Acute (é) iki olası şekilde gösterilebilir:</span><span class="sxs-lookup"><span data-stu-id="3dacc-177">For example, an e-acute (é) can be represented in two possible ways:</span></span>

* <span data-ttu-id="3dacc-178">Tek bir sabit `'é'` karakter (aynı zamanda olarak yazılmış `'\u00E9'` ).</span><span class="sxs-lookup"><span data-stu-id="3dacc-178">A single literal `'é'` character (also written as `'\u00E9'`).</span></span>
* <span data-ttu-id="3dacc-179">Vurgulanmış `'e'` aksan değiştirici karakteri ve ardından düz bir aksanlı karakter `'\u0301'` .</span><span class="sxs-lookup"><span data-stu-id="3dacc-179">A literal unaccented `'e'` character, followed by a combining accent modifier character `'\u0301'`.</span></span>

<span data-ttu-id="3dacc-180">Bu, aşağıdaki _dört_ dizenin, `"résumé"` yapısal parçaları farklı olsa da, görüntülendiği zaman bir sonucu olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-180">This means that the following _four_ strings all result in `"résumé"` when displayed, even though their constituent pieces are different.</span></span> <span data-ttu-id="3dacc-181">Dizeler, değişmez `'é'` karakterlerin veya değişmez değer aksanlı karakterlerin bileşimini ve `'e'` Birleşik vurgu değiştiricisini kullanır `'\u0301'` .</span><span class="sxs-lookup"><span data-stu-id="3dacc-181">The strings use a combination of literal `'é'` characters or literal unaccented `'e'` characters plus the combining accent modifier `'\u0301'`.</span></span>

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

<span data-ttu-id="3dacc-182">Sıralı karşılaştırıcı altında, Bu dizelerin hiçbiri birbirleriyle eşit olarak karşılaştırılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-182">Under an ordinal comparer, none of these strings compare as equal to each other.</span></span> <span data-ttu-id="3dacc-183">Bunun nedeni, ekranda işlense de, her şey farklı temel karakter dizileri içerse de, hepsi aynı şekilde görünür.</span><span class="sxs-lookup"><span data-stu-id="3dacc-183">This is because they all contain different underlying char sequences, even though when they're rendered to the screen, they all look the same.</span></span>

<span data-ttu-id="3dacc-184">Bir işlem gerçekleştirirken `string.IndexOf(..., StringComparison.Ordinal)` , çalışma zamanı tam bir alt dize eşleşmesi arar.</span><span class="sxs-lookup"><span data-stu-id="3dacc-184">When performing a `string.IndexOf(..., StringComparison.Ordinal)` operation, the runtime looks for an exact substring match.</span></span> <span data-ttu-id="3dacc-185">Sonuçlar aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-185">The results are as follows.</span></span>

```cs
Console.WriteLine("resume".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("resume".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
```

<span data-ttu-id="3dacc-186">Sıralı arama ve karşılaştırma yordamları, geçerli iş parçacığının kültür ayarından hiçbir şekilde etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="3dacc-186">Ordinal search and comparison routines are never affected by the current thread's culture setting.</span></span>

<span data-ttu-id="3dacc-187">*Dilsel* arama ve karşılaştırma yordamları, *harmanlama öğelerine* bir dize ayırır ve bu öğelerde arama veya karşılaştırmalar gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-187">*Linguistic* search and comparison routines decompose a string into *collation elements* and perform searches or comparisons on these elements.</span></span> <span data-ttu-id="3dacc-188">Bir dizenin karakterleri ile onun bileşen harmanlama öğeleri arasında 1:1 eşleme olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3dacc-188">There's not necessarily a 1:1 mapping between a string's characters and its constituent collation elements.</span></span> <span data-ttu-id="3dacc-189">Örneğin, 2 uzunluğunda bir dize yalnızca bir tek harmanlama öğesinden oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-189">For example, a string of length 2 may consist of only a single collation element.</span></span> <span data-ttu-id="3dacc-190">İki dize dile duyarlı bir biçimde karşılaştırıldığı zaman, karşılaştırıcı, dizenin sabit karakterleri farklı olsa da, iki dizenin harmanlama öğelerinin aynı anlamsal anlamı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="3dacc-190">When two strings are compared in a linguistic-aware fashion, the comparer checks whether the two strings' collation elements have the same semantic meaning, even if the string's literal characters are different.</span></span>

<span data-ttu-id="3dacc-191">Dizeyi `"résumé"` ve dört farklı temsilini tekrar düşünün.</span><span class="sxs-lookup"><span data-stu-id="3dacc-191">Consider again the string `"résumé"` and its four different representations.</span></span> <span data-ttu-id="3dacc-192">Aşağıdaki tabloda, harmanlama öğelerine bölünmüş her bir temsil gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-192">The following table shows each representation broken down into its collation elements.</span></span>

| <span data-ttu-id="3dacc-193">Dize</span><span class="sxs-lookup"><span data-stu-id="3dacc-193">String</span></span> | <span data-ttu-id="3dacc-194">Harmanlama öğeleri olarak</span><span class="sxs-lookup"><span data-stu-id="3dacc-194">As collation elements</span></span> |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

<span data-ttu-id="3dacc-195">Harmanlama öğesi, okuyucuların tek bir karakter veya karakter kümesi olarak düşündüklerini gevşektir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-195">A collation element corresponds loosely to what readers would think of as a single character or cluster of characters.</span></span> <span data-ttu-id="3dacc-196">Bu, kavramsal olarak bir [grafem kümesine](character-encoding-introduction.md#grapheme-clusters) benzer ancak biraz daha büyük bir şemsiye kapsar.</span><span class="sxs-lookup"><span data-stu-id="3dacc-196">It's conceptually similar to a [grapheme cluster](character-encoding-introduction.md#grapheme-clusters) but encompasses a somewhat larger umbrella.</span></span>

<span data-ttu-id="3dacc-197">Bir dil karşılaştırıcısı altında, tam eşleşmeler gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-197">Under a linguistic comparer, exact matches aren't necessary.</span></span> <span data-ttu-id="3dacc-198">Harmanlama öğeleri anlam anlamlarına göre karşılaştırılır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-198">Collation elements are instead compared based on their semantic meaning.</span></span> <span data-ttu-id="3dacc-199">Örneğin, bir dil karşılaştırıcısı, `"\u00E9"` `"e\u0301"` her ikisi de "dar vurgu değiştiricisi ile küçük harf e" olarak kullanıldığından, alt dizeleri ve eşit olarak davranır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-199">For example, a linguistic comparer treats the substrings `"\u00E9"` and `"e\u0301"` as equal since they both semantically mean "a lowercase e with an acute accent modifier."</span></span> <span data-ttu-id="3dacc-200">Bu yöntem, `IndexOf` `"e\u0301"` `"\u00E9"` Aşağıdaki kod örneğinde gösterildiği gibi, anlam ile eşdeğer alt dizeyi içeren daha büyük bir dizedeki alt dizeden eşleşmesi için yönteminin kullanılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-200">This allows the `IndexOf` method to match the substring `"e\u0301"` within a larger string that contains the semantically equivalent substring `"\u00E9"`, as shown in the following code sample.</span></span>

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

<span data-ttu-id="3dacc-201">Bunun sonucunda, bir dil karşılaştırması kullanılıyorsa farklı uzunluklardan oluşan iki dize eşit olarak karşılaştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-201">As a consequence of this, two strings of different lengths may compare as equal if a linguistic comparison is used.</span></span> <span data-ttu-id="3dacc-202">Çağıranlar, bu tür senaryolarda dize uzunluğu ile ilgilenen özel durum mantığına dikkat edilmelidir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-202">Callers should take care not to special-case logic that deals with string length in such scenarios.</span></span>

<span data-ttu-id="3dacc-203">*Kültüre duyarlı* arama ve karşılaştırma yordamları, dil arama ve karşılaştırma yordamlarının özel bir biçimidir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-203">*Culture-aware* search and comparison routines are a special form of linguistic search and comparison routines.</span></span> <span data-ttu-id="3dacc-204">Kültüre duyarlı bir karşılaştırıcı kapsamında, harmanlama öğesi kavramı, belirtilen kültüre özgü bilgileri içerecek şekilde genişletilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-204">Under a culture-aware comparer, the concept of a collation element is extended to include information specific to the specified culture.</span></span>

<span data-ttu-id="3dacc-205">Örneğin, [Macarca alfabede](https://en.wikipedia.org/wiki/Hungarian_alphabet)iki karakter geri döndüğünüzde \<dz\> , ya da veya birbirinden farklı olan benzersiz mektuplardan ayrı olarak değerlendirilir \<d\> \<z\> .</span><span class="sxs-lookup"><span data-stu-id="3dacc-205">For example, [in the Hungarian alphabet](https://en.wikipedia.org/wiki/Hungarian_alphabet), when the two characters \<dz\> appear back-to-back, they are considered their own unique letter distinct from either \<d\> or \<z\>.</span></span> <span data-ttu-id="3dacc-206">Bu \<dz\> , bir dize içinde görüldüğünde, bir Macarca kültüre duyarlı bir karşılaştırıcının tek bir harmanlama öğesi olarak davrandığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-206">This means that when \<dz\> is seen in a string, a Hungarian culture-aware comparer treats it as a single collation element.</span></span>

| <span data-ttu-id="3dacc-207">Dize</span><span class="sxs-lookup"><span data-stu-id="3dacc-207">String</span></span> | <span data-ttu-id="3dacc-208">Harmanlama öğeleri olarak</span><span class="sxs-lookup"><span data-stu-id="3dacc-208">As collation elements</span></span> | <span data-ttu-id="3dacc-209">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dacc-209">Remarks</span></span> |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | <span data-ttu-id="3dacc-210">(Standart bir dil karşılaştırıcısı kullanarak)</span><span class="sxs-lookup"><span data-stu-id="3dacc-210">(using a standard linguistic comparer)</span></span> |
| `"endz"` | `"e" + "n" + "dz"` | <span data-ttu-id="3dacc-211">(Macarca kültüre duyarlı bir karşılaştırıcı kullanarak)</span><span class="sxs-lookup"><span data-stu-id="3dacc-211">(using a Hungarian culture-aware comparer)</span></span> |

<span data-ttu-id="3dacc-212">Bir Macarca kültüre duyarlı bir karşılaştırıcı kullanırken bu, dizenin alt `"endz"` dizeden *bitmediği* anlamına gelir `"z"` , çünkü < \dz \> ve < \z, \> farklı anlam anlamı olan harmanlama öğeleri olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-212">When using a Hungarian culture-aware comparer, this means that the string `"endz"` *does not* end with the substring `"z"`, as <\dz\> and <\z\> are considered collation elements with different semantic meaning.</span></span>

```cs
// Set thread culture to Hungarian
CultureInfo.CurrentCulture = CultureInfo.GetCultureInfo("hu-HU");
Console.WriteLine("endz".EndsWith("z")); // Prints 'False'

// Set thread culture to invariant culture
CultureInfo.CurrentCulture = CultureInfo.InvariantCulture;
Console.WriteLine("endz".EndsWith("z")); // Prints 'True'
```

> [!NOTE]
>
> - <span data-ttu-id="3dacc-213">Davranış: dilsel ve kültüre duyarlı karşılaştırıcılarla, zaman zaman davranış ayarlamalarını olumsuz şekilde gerçekleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-213">Behavior: Linguistic and culture-aware comparers can undergo behavioral adjustments from time to time.</span></span> <span data-ttu-id="3dacc-214">Hem ıCU hem de eski Windows NLS özelliği, dünya dillerinin nasıl değişdiklerini hesaba göre güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-214">Both ICU and the older Windows NLS facility are updated to account for how world languages change.</span></span> <span data-ttu-id="3dacc-215">Daha fazla bilgi için bkz. Web günlüğü gönderi [yerel ayar (kültür) veri karmaşası](/archive/blogs/shawnste/locale-culture-data-churn).</span><span class="sxs-lookup"><span data-stu-id="3dacc-215">For more information, see the blog post [Locale (culture) data churn](/archive/blogs/shawnste/locale-culture-data-churn).</span></span> <span data-ttu-id="3dacc-216">*Sıralı* karşılaştırıcı davranışı, tam bit düzeyinde arama ve karşılaştırma gerçekleştirdiğinden dolayı hiçbir şekilde değişmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-216">The *Ordinal* comparer's behavior will never change since it performs exact bitwise searching and comparison.</span></span> <span data-ttu-id="3dacc-217">Bununla birlikte, daha fazla karakter kümesi kapsayacak şekilde Unicode büyüdükçe ve mevcut büyük küçük harf verilerinde da ihmallerinden 'yi düzelterek *OrdinalIgnoreCase* karşılaştırıcı davranışı değişebilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-217">However, the *OrdinalIgnoreCase* comparer's behavior may change as Unicode grows to encompass more character sets and corrects omissions in existing casing data.</span></span>
> - <span data-ttu-id="3dacc-218">Kullanım: karşılaştırıcılarla `StringComparison.InvariantCulture` ve `StringComparison.InvariantCultureIgnoreCase` kültüre duyarlı olmayan dil Karşılaştırıcılar.</span><span class="sxs-lookup"><span data-stu-id="3dacc-218">Usage: The comparers `StringComparison.InvariantCulture` and `StringComparison.InvariantCultureIgnoreCase` are linguistic comparers that are not culture-aware.</span></span> <span data-ttu-id="3dacc-219">Diğer bir deyişle, bu Karşılaştırıcılar, birden çok olası temel temsilde sahip olan ve bu tür temsillerin eşit olarak değerlendirilme karakteri gibi kavramları anlamalıdır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-219">That is, these comparers understand concepts such as the accented character é having multiple possible underlying representations, and that all such representations should be treated equal.</span></span> <span data-ttu-id="3dacc-220">Ancak kültüre duyarlı olmayan dil Karşılaştırıcılar \<dz\> \<d\> \<z\> , yukarıda gösterildiği gibi veya ' den farklı olarak özel işleme içermez.</span><span class="sxs-lookup"><span data-stu-id="3dacc-220">But non-culture-aware linguistic comparers won't contain special handling for \<dz\> as distinct from \<d\> or \<z\>, as shown above.</span></span> <span data-ttu-id="3dacc-221">Ayrıca, Almanya Eszett (ß) gibi özel durum karakterleri de olmaz.</span><span class="sxs-lookup"><span data-stu-id="3dacc-221">They also won't special-case characters like the German Eszett (ß).</span></span>

<span data-ttu-id="3dacc-222">.NET ayrıca *sabit Genelleştirme modunu* da sunmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-222">.NET also offers the *invariant globalization mode*.</span></span> <span data-ttu-id="3dacc-223">Bu katılım modu, dilsel arama ve karşılaştırma yordamlarına yönelik kod yollarını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-223">This opt-in mode disables code paths that deal with linguistic search and comparison routines.</span></span> <span data-ttu-id="3dacc-224">Bu modda tüm işlemler, *Ordinal* *OrdinalIgnoreCase* `CultureInfo` `StringComparison` çağıranın sağladığı veya bağımsız değişkenden bağımsız olarak Ordinal veya OrdinalIgnoreCase davranışları kullanır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-224">In this mode, all operations use *Ordinal* or *OrdinalIgnoreCase* behaviors, regardless of what `CultureInfo` or `StringComparison` argument the caller provides.</span></span> <span data-ttu-id="3dacc-225">Daha fazla bilgi için bkz. Genelleştirme ve [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md) [için çalışma zamanı yapılandırma seçenekleri](../../core/run-time-config/globalization.md) .</span><span class="sxs-lookup"><span data-stu-id="3dacc-225">For more information, see [Run-time configuration options for globalization](../../core/run-time-config/globalization.md) and [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

<span data-ttu-id="3dacc-226">Daha fazla bilgi için bkz. [.net 'teki dizeleri karşılaştırmak Için en iyi uygulamalar](best-practices-strings.md).</span><span class="sxs-lookup"><span data-stu-id="3dacc-226">For more information, see [Best practices for comparing strings in .NET](best-practices-strings.md).</span></span>

## <a name="security-implications"></a><span data-ttu-id="3dacc-227">Güvenlik üzerindeki etkileri</span><span class="sxs-lookup"><span data-stu-id="3dacc-227">Security implications</span></span>

<span data-ttu-id="3dacc-228">Uygulamanız filtreleme için etkilenen bir API kullanıyorsa, bir sıra araması yerine bir dil aramasının yanlışlıkla kullanıldığı yerleri bulmaya yardımcı olması için CA1307 ve CA1309 kod analizi kurallarının etkinleştirilmesini öneririz.</span><span class="sxs-lookup"><span data-stu-id="3dacc-228">If your app uses an affected API for filtering, we recommend enabling the CA1307 and CA1309 code analysis rules to help locate places where a linguistic search may have inadvertently been used instead of an ordinal search.</span></span> <span data-ttu-id="3dacc-229">Aşağıdakiler gibi kod desenleri güvenlik açıklarına maruz kalabilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-229">Code patterns like the following may be susceptible to security exploits.</span></span>

```cs
//
// THIS SAMPLE CODE IS INCORRECT.
// DO NOT USE IT IN PRODUCTION.
//
public bool ContainsHtmlSensitiveCharacters(string input)
{
    if (input.IndexOf("<") >= 0) { return true; }
    if (input.IndexOf("&") >= 0) { return true; }
    return false;
}
```

<span data-ttu-id="3dacc-230">`string.IndexOf(string)`Yöntemi varsayılan olarak bir dilsel arama kullandığından, bir dize bir sabit değer `'<'` veya `'&'` karakter içermesi ve `string.IndexOf(string)` yordamın dönmesi için arama alt dizesinin `-1` bulunamadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-230">Because the `string.IndexOf(string)` method uses a linguistic search by default, it's possible for a string to contain a literal `'<'` or `'&'` character and for the `string.IndexOf(string)` routine to return `-1`, indicating that the search substring was not found.</span></span> <span data-ttu-id="3dacc-231">Kod analizi kuralları CA1307 ve CA1309 bayrağıyla ilgili siteler ve geliştirici olası bir sorun olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-231">Code analysis rules CA1307 and CA1309 flag such call sites and alert the developer that there's a potential problem.</span></span>

## <a name="default-search-and-comparison-types"></a><span data-ttu-id="3dacc-232">Varsayılan arama ve karşılaştırma türleri</span><span class="sxs-lookup"><span data-stu-id="3dacc-232">Default search and comparison types</span></span>

<span data-ttu-id="3dacc-233">Aşağıdaki tabloda, çeşitli dize ve dize benzeri API 'Ler için varsayılan arama ve karşılaştırma türleri listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-233">The following table lists the default search and comparison types for various string and string-like APIs.</span></span> <span data-ttu-id="3dacc-234">Çağıran açık `CultureInfo` veya `StringComparison` parametre sağlıyorsa, bu parametre varsayılan olarak kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-234">If the caller provides an explicit `CultureInfo` or `StringComparison` parameter, that parameter will be honored over any default.</span></span>

| <span data-ttu-id="3dacc-235">API</span><span class="sxs-lookup"><span data-stu-id="3dacc-235">API</span></span> | <span data-ttu-id="3dacc-236">Varsayılan davranış</span><span class="sxs-lookup"><span data-stu-id="3dacc-236">Default behavior</span></span> | <span data-ttu-id="3dacc-237">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dacc-237">Remarks</span></span> |
|---|---|---|
| `string.Compare` | <span data-ttu-id="3dacc-238">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-238">CurrentCulture</span></span> | |
| `string.CompareTo` | <span data-ttu-id="3dacc-239">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-239">CurrentCulture</span></span> | |
| `string.Contains` | <span data-ttu-id="3dacc-240">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-240">Ordinal</span></span> | |
| `string.EndsWith` | <span data-ttu-id="3dacc-241">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-241">Ordinal</span></span> | <span data-ttu-id="3dacc-242">(ilk parametre bir olduğunda `char` )</span><span class="sxs-lookup"><span data-stu-id="3dacc-242">(when the first parameter is a `char`)</span></span> |
| `string.EndsWith` | <span data-ttu-id="3dacc-243">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-243">CurrentCulture</span></span> | <span data-ttu-id="3dacc-244">(ilk parametre bir olduğunda `string` )</span><span class="sxs-lookup"><span data-stu-id="3dacc-244">(when the first parameter is a `string`)</span></span> |
| `string.Equals` | <span data-ttu-id="3dacc-245">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-245">Ordinal</span></span> | |
| `string.GetHashCode` | <span data-ttu-id="3dacc-246">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-246">Ordinal</span></span> | |
| `string.IndexOf` | <span data-ttu-id="3dacc-247">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-247">Ordinal</span></span> | <span data-ttu-id="3dacc-248">(ilk parametre bir olduğunda `char` )</span><span class="sxs-lookup"><span data-stu-id="3dacc-248">(when the first parameter is a `char`)</span></span> |
| `string.IndexOf` | <span data-ttu-id="3dacc-249">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-249">CurrentCulture</span></span> | <span data-ttu-id="3dacc-250">(ilk parametre bir olduğunda `string` )</span><span class="sxs-lookup"><span data-stu-id="3dacc-250">(when the first parameter is a `string`)</span></span> |
| `string.IndexOfAny` | <span data-ttu-id="3dacc-251">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-251">Ordinal</span></span> | |
| `string.LastIndexOf` | <span data-ttu-id="3dacc-252">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-252">Ordinal</span></span> | <span data-ttu-id="3dacc-253">(ilk parametre bir olduğunda `char` )</span><span class="sxs-lookup"><span data-stu-id="3dacc-253">(when the first parameter is a `char`)</span></span> |
| `string.LastIndexOf` | <span data-ttu-id="3dacc-254">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-254">CurrentCulture</span></span> | <span data-ttu-id="3dacc-255">(ilk parametre bir olduğunda `string` )</span><span class="sxs-lookup"><span data-stu-id="3dacc-255">(when the first parameter is a `string`)</span></span> |
| `string.LastIndexOfAny` | <span data-ttu-id="3dacc-256">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-256">Ordinal</span></span> | |
| `string.Replace` | <span data-ttu-id="3dacc-257">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-257">Ordinal</span></span> | |
| `string.Split` | <span data-ttu-id="3dacc-258">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-258">Ordinal</span></span> | |
| `string.StartsWith` | <span data-ttu-id="3dacc-259">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-259">Ordinal</span></span> | <span data-ttu-id="3dacc-260">(ilk parametre bir olduğunda `char` )</span><span class="sxs-lookup"><span data-stu-id="3dacc-260">(when the first parameter is a `char`)</span></span> |
| `string.StartsWith` | <span data-ttu-id="3dacc-261">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-261">CurrentCulture</span></span> | <span data-ttu-id="3dacc-262">(ilk parametre bir olduğunda `string` )</span><span class="sxs-lookup"><span data-stu-id="3dacc-262">(when the first parameter is a `string`)</span></span> |
| `string.ToLower` | <span data-ttu-id="3dacc-263">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-263">CurrentCulture</span></span> | |
| `string.ToLowerInvariant` | <span data-ttu-id="3dacc-264">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-264">InvariantCulture</span></span> | |
| `string.ToUpper` | <span data-ttu-id="3dacc-265">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-265">CurrentCulture</span></span> | |
| `string.ToUpperInvariant` | <span data-ttu-id="3dacc-266">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-266">InvariantCulture</span></span> | |
| `string.Trim` | <span data-ttu-id="3dacc-267">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-267">Ordinal</span></span> | |
| `string.TrimEnd` | <span data-ttu-id="3dacc-268">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-268">Ordinal</span></span> | |
| `string.TrimStart` | <span data-ttu-id="3dacc-269">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-269">Ordinal</span></span> | |
| `string == string` | <span data-ttu-id="3dacc-270">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-270">Ordinal</span></span> | |
| `string != string` | <span data-ttu-id="3dacc-271">Sıralı</span><span class="sxs-lookup"><span data-stu-id="3dacc-271">Ordinal</span></span> | |

<span data-ttu-id="3dacc-272">API 'lerden farklı olarak `string` , tüm `MemoryExtensions` API 'ler varsayılan olarak *sıralı* aramalar ve karşılaştırmalar gerçekleştirerek aşağıdaki özel durumlarla yapılır.</span><span class="sxs-lookup"><span data-stu-id="3dacc-272">Unlike `string` APIs, all `MemoryExtensions` APIs perform *Ordinal* searches and comparisons by default, with the following exceptions.</span></span>

| <span data-ttu-id="3dacc-273">API</span><span class="sxs-lookup"><span data-stu-id="3dacc-273">API</span></span> | <span data-ttu-id="3dacc-274">Varsayılan davranış</span><span class="sxs-lookup"><span data-stu-id="3dacc-274">Default behavior</span></span> | <span data-ttu-id="3dacc-275">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3dacc-275">Remarks</span></span> |
|---|---|---|
| `MemoryExtensions.ToLower` | <span data-ttu-id="3dacc-276">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-276">CurrentCulture</span></span> | <span data-ttu-id="3dacc-277">(null `CultureInfo` bağımsız değişken geçirildiğinde)</span><span class="sxs-lookup"><span data-stu-id="3dacc-277">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToLowerInvariant` | <span data-ttu-id="3dacc-278">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-278">InvariantCulture</span></span> | |
| `MemoryExtensions.ToUpper` | <span data-ttu-id="3dacc-279">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-279">CurrentCulture</span></span> | <span data-ttu-id="3dacc-280">(null `CultureInfo` bağımsız değişken geçirildiğinde)</span><span class="sxs-lookup"><span data-stu-id="3dacc-280">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToUpperInvariant` | <span data-ttu-id="3dacc-281">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="3dacc-281">InvariantCulture</span></span> | |

<span data-ttu-id="3dacc-282">Sonuç olarak, kodun tüketme 'den kullanıma dönüştürülmesi `string` `ReadOnlySpan<char>` , davranış değişikliklerinin yanlışlıkla tanıtılmasından bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="3dacc-282">A consequence is that when converting code from consuming `string` to consuming `ReadOnlySpan<char>`, behavioral changes may be introduced inadvertently.</span></span> <span data-ttu-id="3dacc-283">Buna bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-283">An example of this follows.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

<span data-ttu-id="3dacc-284">Bunu ele almak için önerilen yol, bu API 'lere açık bir parametre geçirmektir `StringComparison` .</span><span class="sxs-lookup"><span data-stu-id="3dacc-284">The recommended way to address this is to pass an explicit `StringComparison` parameter to these APIs.</span></span> <span data-ttu-id="3dacc-285">CA1307 ve CA1309 kod analizi kuralları buna yardımcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="3dacc-285">The code analysis rules CA1307 and CA1309 can assist with this.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a><span data-ttu-id="3dacc-286">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3dacc-286">See also</span></span>

- [<span data-ttu-id="3dacc-287">Genelleştirme son değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3dacc-287">Globalization breaking changes</span></span>](../../core/compatibility/globalization.md)
- [<span data-ttu-id="3dacc-288">.NET 'teki dizeleri karşılaştırmak için en iyi yöntemler</span><span class="sxs-lookup"><span data-stu-id="3dacc-288">Best practices for comparing strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="3dacc-289">C 'de dizeleri karşılaştırma #</span><span class="sxs-lookup"><span data-stu-id="3dacc-289">How to compare strings in C#</span></span>](../../csharp/how-to/compare-strings.md)
- [<span data-ttu-id="3dacc-290">.NET Genelleştirme ve ıCU</span><span class="sxs-lookup"><span data-stu-id="3dacc-290">.NET globalization and ICU</span></span>](../globalization-localization/globalization-icu.md)
- [<span data-ttu-id="3dacc-291">Ordinal ve kültüre duyarlı dize işlemleri</span><span class="sxs-lookup"><span data-stu-id="3dacc-291">Ordinal vs. culture-sensitive string operations</span></span>](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [<span data-ttu-id="3dacc-292">.NET kaynak kodu çözümlemesine genel bakış</span><span class="sxs-lookup"><span data-stu-id="3dacc-292">Overview of .NET source code analysis</span></span>](../../fundamentals/code-analysis/overview.md)
