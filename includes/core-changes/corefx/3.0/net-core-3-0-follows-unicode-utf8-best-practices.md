---
ms.openlocfilehash: 843c78bb4e4f88d9ac58308a91ab8278364c9580
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021596"
---
### <a name="net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences"></a><span data-ttu-id="19465-101">.NET Core 3.0, kötü biçimlendirilmiş UTF-8 bayt dizilerini değiştirirken Unicode en iyi uygulamalarını takip eder</span><span class="sxs-lookup"><span data-stu-id="19465-101">.NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>

<span data-ttu-id="19465-102"><xref:System.Text.UTF8Encoding> Sınıf, bayt-karakter transkodlama işlemi sırasında kötü biçimlendirilmiş bir UTF-8 bayt dizisiyle karşılaştığında, bu diziyi çıkış dizesinde ' ' (U+FFFD REPLACEMENT CHARACTER) karakteriyle değiştirir.</span><span class="sxs-lookup"><span data-stu-id="19465-102">When the <xref:System.Text.UTF8Encoding> class encounters an ill-formed UTF-8 byte sequence during a byte-to-character transcoding operation, it will replace that sequence with a '�' (U+FFFD REPLACEMENT CHARACTER) character in the output string.</span></span> <span data-ttu-id="19465-103">.NET Core 3.0, transkodlama işlemi sırasında bu değişikliği gerçekleştirmek için Unicode en iyi uygulama aşağıdaki .NET Core ve .NET Framework önceki sürümlerinden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="19465-103">.NET Core 3.0 differs from previous versions of .NET Core and the .NET Framework by following the Unicode best practice for performing this replacement during the transcoding operation.</span></span>

<span data-ttu-id="19465-104">Bu, yeni <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> ve <xref:System.Text.Rune?displayProperty=nameWithType> türler de dahil olmak üzere .NET boyunca UTF-8 işleme geliştirmek için daha büyük bir çabanın bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="19465-104">This is part of a larger effort to improve UTF-8 handling throughout .NET, including by the new <xref:System.Text.Unicode.Utf8?displayProperty=nameWithType> and <xref:System.Text.Rune?displayProperty=nameWithType> types.</span></span> <span data-ttu-id="19465-105">Tür, <xref:System.Text.UTF8Encoding> yeni tanıtılan türlerle tutarlı çıktı üretecek şekilde geliştirilmiş hata işleme mekaniği verildi.</span><span class="sxs-lookup"><span data-stu-id="19465-105">The <xref:System.Text.UTF8Encoding> type was given improved error handling mechanics so that it produces output consistent with the newly introduced types.</span></span>

#### <a name="change-description"></a><span data-ttu-id="19465-106">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="19465-106">Change description</span></span>

<span data-ttu-id="19465-107">.NET Core 3.0 ile başlayarak, karakterlere baytlar transcoding yaparken, <xref:System.Text.UTF8Encoding> sınıf Unicode en iyi uygulamaları dayalı karakter değiştirme gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="19465-107">Starting with .NET Core 3.0, when transcoding bytes to characters, the <xref:System.Text.UTF8Encoding> class performs character substitution based on Unicode best practices.</span></span> <span data-ttu-id="19465-108">Kullanılan ikame mekanizması [Unicode Standard, Sürüm 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) tarafından _Maksimal Alt Parçaların U+FFFD Ikamesi_başlığıaltında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="19465-108">The substitution mechanism used is described by [The Unicode Standard, Version 12.0, Sec. 3.9 (PDF)](https://www.unicode.org/versions/Unicode12.0.0/ch03.pdf) in the heading titled _U+FFFD Substitution of Maximal Subparts_.</span></span>

<span data-ttu-id="19465-109">Bu _davranış_ yalnızca giriş bayt dizisi kötü biçimlendirilmiş UTF-8 verileri içeriyorsa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="19465-109">This behavior _only_ applies when the input byte sequence contains ill-formed UTF-8 data.</span></span> <span data-ttu-id="19465-110">Ayrıca, <xref:System.Text.UTF8Encoding> örnek ([UTF8Encoding constructor documentation] ile `throwOnInvalidBytes: true` <xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>oluşturulmuşsa, `UTF8Encoding` örnek U+FFFD değiştirme gerçekleştirmek yerine geçersiz giriş atmaya devam edecektir.</span><span class="sxs-lookup"><span data-stu-id="19465-110">Additionally, if the <xref:System.Text.UTF8Encoding> instance has been constructed with `throwOnInvalidBytes: true` (see the [UTF8Encoding constructor documentation](<xref:System.Text.UTF8Encoding.%23ctor(System.Boolean,System.Boolean)>, the `UTF8Encoding` instance will continue to throw on invalid input rather than perform U+FFFD replacement.</span></span>

<span data-ttu-id="19465-111">Aşağıda, bu değişikliğin geçersiz bir 3 bayt girişiyle etkisi gösteriş ve gösteriş gösteriş ve</span><span class="sxs-lookup"><span data-stu-id="19465-111">The following illustrates the impact of this change with an invalid 3-byte input:</span></span>

|<span data-ttu-id="19465-112">Kötü biçimlendirilmiş 3 bayt girişi</span><span class="sxs-lookup"><span data-stu-id="19465-112">Ill-formed 3-byte input</span></span>|<span data-ttu-id="19465-113">.NET Core 3.0'dan önceki çıktı</span><span class="sxs-lookup"><span data-stu-id="19465-113">Output before .NET Core 3.0</span></span>|<span data-ttu-id="19465-114">.NET Core 3.0 ile başlayan çıktı</span><span class="sxs-lookup"><span data-stu-id="19465-114">Output starting with .NET Core 3.0</span></span>|
|---|---|---|
| `[ ED A0 90 ]` | <span data-ttu-id="19465-115">`[ FFFD FFFD ]`(2 karakterçıkış)</span><span class="sxs-lookup"><span data-stu-id="19465-115">`[ FFFD FFFD ]` (2-character output)</span></span>| <span data-ttu-id="19465-116">`[ FFFD FFFD FFFD ]`(3 karakterçıkış)</span><span class="sxs-lookup"><span data-stu-id="19465-116">`[ FFFD FFFD FFFD ]` (3-character output)</span></span>|

<span data-ttu-id="19465-117">Bu 3-char çıktı, tablo _3-9'a_ göre daha önce bağlı olan Unicode Standart PDF'ye göre tercih edilen çıktıdır.</span><span class="sxs-lookup"><span data-stu-id="19465-117">This 3-char output is the preferred output, according to _Table 3-9_ of the previously linked Unicode Standard PDF.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="19465-118">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="19465-118">Version introduced</span></span>

<span data-ttu-id="19465-119">3,0</span><span class="sxs-lookup"><span data-stu-id="19465-119">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="19465-120">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="19465-120">Recommended action</span></span>

<span data-ttu-id="19465-121">Geliştirici adına herhangi bir eylem gerekmez.</span><span class="sxs-lookup"><span data-stu-id="19465-121">No action is required on the part of the developer.</span></span>

#### <a name="category"></a><span data-ttu-id="19465-122">Kategori</span><span class="sxs-lookup"><span data-stu-id="19465-122">Category</span></span>

<span data-ttu-id="19465-123">Çekirdek .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="19465-123">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="19465-124">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="19465-124">Affected APIs</span></span>

- <xref:System.Text.UTF8Encoding.GetCharCount%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetChars%2A?displayProperty=nameWithType>
- <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Text.UTF8Encoding.GetCharCount`
- `Overload:System.Text.UTF8Encoding.GetChars`
- `M:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)`

-->
