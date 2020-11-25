---
title: "Son değişiklik: genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır"
description: ICU kitaplıklarının NLS yerine Genelleştirme işlevselliği için kullanıldığı .NET 5,0 ' de Genelleştirme bölünmesi değişikliği hakkında bilgi edinin.
ms.date: 05/19/2020
ms.openlocfilehash: efc20e21969ea4a83c9122e40b262e1dc38e6770
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761706"
---
# <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="c11a3-103">Genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır</span><span class="sxs-lookup"><span data-stu-id="c11a3-103">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="c11a3-104">.NET 5,0 ve sonraki sürümleri, Windows 10 Mayıs 2019 güncelleştirme veya sonrasında çalışırken Genelleştirme işlevselliği için [Unicode (ıCU)](http://site.icu-project.org/home) kitaplıklarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="c11a3-104">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

## <a name="change-description"></a><span data-ttu-id="c11a3-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c11a3-105">Change description</span></span>

<span data-ttu-id="c11a3-106">.NET Core 1,0-3,1 ve .NET Framework 4 ve üzeri sürümlerde, .NET kitaplıkları Windows üzerinde Genelleştirme işlevselliği için [ulusal dil desteği (NLS)](/windows/win32/intl/national-language-support) API 'lerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c11a3-106">In .NET Core 1.0 - 3.1 and .NET Framework 4 and later, .NET libraries use [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality on Windows.</span></span> <span data-ttu-id="c11a3-107">Örneğin, NLS işlevleri dizeleri karşılaştırmak, kültür bilgilerini almak ve uygun kültür içinde dize büyük harfleri gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c11a3-107">For example, NLS functions were used to compare strings, get culture information, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="c11a3-108">.NET 5,0 ' den itibaren, bir uygulama Windows 10 Mayıs 2019 veya sonraki sürümlerde çalışıyorsa, .NET kitaplıkları varsayılan olarak [ICU](http://site.icu-project.org/home) genelleştirme API 'lerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c11a3-108">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs, by default.</span></span>

> [!NOTE]
> <span data-ttu-id="c11a3-109">Windows 10 Mayıs 2019 güncelleştirmesi ve sonraki sürümleri ıCU yerel kitaplığıyla birlikte sevk.</span><span class="sxs-lookup"><span data-stu-id="c11a3-109">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="c11a3-110">.NET çalışma zamanı ıCU 'yi yükleye, bunun yerine NLS kullanır.</span><span class="sxs-lookup"><span data-stu-id="c11a3-110">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="c11a3-111">Davranış farkları</span><span class="sxs-lookup"><span data-stu-id="c11a3-111">Behavioral differences</span></span>

<span data-ttu-id="c11a3-112">Genelleştirme tesislerini kullandığınızı fark etmeseniz bile uygulamanızdaki değişiklikleri görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c11a3-112">You might see changes in your app even if you don't realize you're using globalization facilities.</span></span> <span data-ttu-id="c11a3-113">Bu bölüm, görebileceğiniz bazı davranış değişikliklerini listeler, ancak diğerleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="c11a3-113">This section lists a couple of the behavioral changes you might see, but there are others too.</span></span>

### <a name="stringindexof"></a><span data-ttu-id="c11a3-114">String. IndexOf</span><span class="sxs-lookup"><span data-stu-id="c11a3-114">String.IndexOf</span></span>

<span data-ttu-id="c11a3-115"><xref:System.String.IndexOf(System.String)?displayProperty=nameWithType>Bir dizedeki yeni satır karakterinin dizinini bulmak için çağıran aşağıdaki kodu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c11a3-115">Consider the following code that calls <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> to find the index of the newline character in a string.</span></span>

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- <span data-ttu-id="c11a3-116">Önceki .NET sürümlerinde, kod parçacığı yazdırılır `6` .</span><span class="sxs-lookup"><span data-stu-id="c11a3-116">In previous versions of .NET on Windows, the snippet prints `6`.</span></span>
- <span data-ttu-id="c11a3-117">.NET 5,0 ve sonraki sürümlerinde, kod parçacığı yazdırılır `-1` .</span><span class="sxs-lookup"><span data-stu-id="c11a3-117">In .NET 5.0 and later versions on Windows 19H1 and later versions, the snippet prints `-1`.</span></span>

<span data-ttu-id="c11a3-118">Kültüre duyarlı arama yerine bir sıralı arama gerçekleştirerek bu kodu onarmak için, <xref:System.String.IndexOf(System.String,System.StringComparison)> aşırı yüklemeyi çağırın ve <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> bağımsız değişken olarak geçirin.</span><span class="sxs-lookup"><span data-stu-id="c11a3-118">To fix this code by conducting an ordinal search instead of a culture-sensitive search, call the <xref:System.String.IndexOf(System.String,System.StringComparison)> overload and pass in <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> as an argument.</span></span>

<span data-ttu-id="c11a3-119">Kod çözümleme kurallarını [CA1307: açıklık ve CA1309 Için StringComparison belirtin](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) : kodunuzda bu çağrı sitelerini bulmak Için [sıralı StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1309.md) ' i kullanın.</span><span class="sxs-lookup"><span data-stu-id="c11a3-119">You can run code analysis rules [CA1307: Specify StringComparison for clarity](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309: Use ordinal StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1309.md) to find these call sites in your code.</span></span>

<span data-ttu-id="c11a3-120">Daha fazla bilgi için bkz. [.NET 5 + üzerindeki dizeleri karşılaştırırken davranış değişiklikleri](../../../../standard/base-types/string-comparison-net-5-plus.md).</span><span class="sxs-lookup"><span data-stu-id="c11a3-120">For more information, see [Behavior changes when comparing strings on .NET 5+](../../../../standard/base-types/string-comparison-net-5-plus.md).</span></span>

### <a name="currency-symbol"></a><span data-ttu-id="c11a3-121">Para birimi simgesi</span><span class="sxs-lookup"><span data-stu-id="c11a3-121">Currency symbol</span></span>

<span data-ttu-id="c11a3-122">Para birimi biçim belirticisini kullanarak bir dizeyi biçimlendiren aşağıdaki kodu göz önünde bulundurun `C` .</span><span class="sxs-lookup"><span data-stu-id="c11a3-122">Consider the following code that formats a string using the currency format specifier `C`.</span></span> <span data-ttu-id="c11a3-123">Geçerli iş parçacığının kültürü, ülkeyi değil yalnızca dili içeren bir kültüre ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c11a3-123">The current thread's culture is set to a culture that includes only the language and not the country.</span></span>

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- <span data-ttu-id="c11a3-124">Önceki .NET sürümlerinde, metin değeri `"100,00 €"` .</span><span class="sxs-lookup"><span data-stu-id="c11a3-124">In previous versions of .NET on Windows, the value of text is `"100,00 €"`.</span></span>
- <span data-ttu-id="c11a3-125">.NET 5,0 ve sonraki sürümlerde Windows 19H1 ve sonraki sürümlerinde, metin değeri, `"100,00 ¤"` Euro yerine uluslararası para birimi sembolünü kullanan olur.</span><span class="sxs-lookup"><span data-stu-id="c11a3-125">In .NET 5.0 and later versions on Windows 19H1 and later versions, the value of text is `"100,00 ¤"`, which uses the international currency symbol instead of the euro.</span></span> <span data-ttu-id="c11a3-126">ICU 'de tasarım, bir para biriminin bir ülke veya bölgenin bir dil değil bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="c11a3-126">In ICU, the design is that a currency is a property of a country or region, not a language.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="c11a3-127">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c11a3-127">Reason for change</span></span>

<span data-ttu-id="c11a3-128">Bu değişiklik, birleştirme için sunulmuştur. Tüm desteklenen işletim sistemleri genelinde NET ' in Genelleştirme davranışı.</span><span class="sxs-lookup"><span data-stu-id="c11a3-128">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="c11a3-129">Ayrıca, uygulamaların işletim sisteminin yerleşik kitaplıklarına göre değil, kendi Genelleştirme kitaplıklarını paketleyebilme olanağı da sağlar.</span><span class="sxs-lookup"><span data-stu-id="c11a3-129">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the operating system's built-in libraries.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c11a3-130">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c11a3-130">Version introduced</span></span>

<span data-ttu-id="c11a3-131">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="c11a3-131">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c11a3-132">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c11a3-132">Recommended action</span></span>

<span data-ttu-id="c11a3-133">Geliştiricinin bölümünde herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="c11a3-133">No action is required on the part of the developer.</span></span> <span data-ttu-id="c11a3-134">Ancak, NLS genelleştirme API 'Lerini kullanmaya devam etmek istiyorsanız, bu davranışa dönmek için bir [çalışma zamanı anahtarı](../../../run-time-config/globalization.md#nls) ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c11a3-134">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="c11a3-135">Kullanılabilir anahtarlar hakkında daha fazla bilgi için bkz. [.NET Genelleştirme ve ıCU](../../../../standard/globalization-localization/globalization-icu.md) makalesi.</span><span class="sxs-lookup"><span data-stu-id="c11a3-135">For more information about the available switches, see the [.NET globalization and ICU](../../../../standard/globalization-localization/globalization-icu.md) article.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c11a3-136">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c11a3-136">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="c11a3-137">Ad alanındaki çoğu tür <xref:System.Globalization?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="c11a3-137">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>
- <span data-ttu-id="c11a3-138"><xref:System.Array.Sort%2A?displayProperty=fullName> (dizeler dizisini sıralarken)</span><span class="sxs-lookup"><span data-stu-id="c11a3-138"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting an array of strings)</span></span>
- <span data-ttu-id="c11a3-139"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (liste öğeleri dizeler olduğunda)</span><span class="sxs-lookup"><span data-stu-id="c11a3-139"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="c11a3-140"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (anahtarlar dizeler olduğunda)</span><span class="sxs-lookup"><span data-stu-id="c11a3-140"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="c11a3-141"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (anahtarlar dizeler olduğunda)</span><span class="sxs-lookup"><span data-stu-id="c11a3-141"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="c11a3-142"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (küme dizeler içerdiğinde)</span><span class="sxs-lookup"><span data-stu-id="c11a3-142"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

<!--

### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

### Category

- Core .NET libraries
- Globalization

-->
