---
ms.openlocfilehash: 48d2f1b5fa2eced30d3c9fb65804268904f11ab8
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065076"
---
### <a name="unicode-category-changed-for-some-latin-1-characters"></a><span data-ttu-id="c002a-101">Bazı Latin-1 karakterleri için Unicode kategorisi değişti</span><span class="sxs-lookup"><span data-stu-id="c002a-101">Unicode category changed for some Latin-1 characters</span></span>

<span data-ttu-id="c002a-102"><xref:System.Char> Yöntemler şimdi Latin-1 aralığındaki karakterler için doğru Unicode kategorisini döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="c002a-102"><xref:System.Char> methods now return the correct Unicode category for characters in the Latin-1 range.</span></span> <span data-ttu-id="c002a-103">Kategori Unicode standardına göre eşleşir.</span><span class="sxs-lookup"><span data-stu-id="c002a-103">The category matches that of the Unicode standard.</span></span>

#### <a name="change-description"></a><span data-ttu-id="c002a-104">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="c002a-104">Change description</span></span>

<span data-ttu-id="c002a-105">Önceki .NET sürümlerinde, <xref:System.Char> Yöntemler Latin-1 aralığındaki karakterler için sabit bir Unicode kategori listesi kullandı.</span><span class="sxs-lookup"><span data-stu-id="c002a-105">In previous .NET versions, <xref:System.Char> methods used a fixed list of Unicode categories for characters in the Latin-1 range.</span></span> <span data-ttu-id="c002a-106">Ancak, Unicode standardı Bu API 'lerin uygulandığından bu karakterlerin bazı kategorilerini değiştirmiştir, bu da bir tutarsızlık oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="c002a-106">However, the Unicode standard has changed the categories of some of these characters since those APIs were implemented, creating a discrepancy.</span></span> <span data-ttu-id="c002a-107">Ayrıca, ve API 'ler arasında bir tutarsızlık vardı <xref:System.Char> <xref:System.Globalization.CharUnicodeInfo> , bu da Unicode standardını izler.</span><span class="sxs-lookup"><span data-stu-id="c002a-107">In addition, there was also a discrepancy between <xref:System.Char> and <xref:System.Globalization.CharUnicodeInfo> APIs, which follow the Unicode standard.</span></span> <span data-ttu-id="c002a-108">.NET 5,0 ve sonraki sürümlerde Yöntemler, <xref:System.Char> tüm karakterler Için Unicode standartınkilerle eşleşen Unicode kategorisini kullanır ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="c002a-108">In .NET 5.0 and later versions, <xref:System.Char> methods use and return the Unicode category that matches the Unicode standard for all characters.</span></span>

<span data-ttu-id="c002a-109">Aşağıdaki tabloda, .NET 5,0 ' de Unicode kategorileri değişmiş olan karakterler gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="c002a-109">The following table shows the characters whose Unicode categories have changed in .NET 5.0:</span></span>

| <span data-ttu-id="c002a-110">Karakter</span><span class="sxs-lookup"><span data-stu-id="c002a-110">Character</span></span>    | <span data-ttu-id="c002a-111">Unicode kategorisi</span><span class="sxs-lookup"><span data-stu-id="c002a-111">Unicode category</span></span><br><span data-ttu-id="c002a-112">önceki .NET sürümlerinde</span><span class="sxs-lookup"><span data-stu-id="c002a-112">in previous .NET versions</span></span> | <span data-ttu-id="c002a-113">Unicode kategorisi</span><span class="sxs-lookup"><span data-stu-id="c002a-113">Unicode category</span></span><br><span data-ttu-id="c002a-114">.NET 5,0 ve sonraki sürümlerde</span><span class="sxs-lookup"><span data-stu-id="c002a-114">in .NET 5.0 and later versions</span></span> |
|:------------:|:---------------------------------------------:|:--------------------------------------------------:|
| <span data-ttu-id="c002a-115">§ (\u00a7)</span><span class="sxs-lookup"><span data-stu-id="c002a-115">§ (\u00a7)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="c002a-116">ª (\u00aa)</span><span class="sxs-lookup"><span data-stu-id="c002a-116">ª (\u00aa)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |
| <span data-ttu-id="c002a-117">KıY (\u00ad)</span><span class="sxs-lookup"><span data-stu-id="c002a-117">SHY (\u00ad)</span></span> | `DashPunctuation`                             | `Format`                                           |
| <span data-ttu-id="c002a-118">¶ (\u00b6)</span><span class="sxs-lookup"><span data-stu-id="c002a-118">¶ (\u00b6)</span></span>   | `OtherSymbol`                                 | `OtherPunctuation`                                 |
| <span data-ttu-id="c002a-119">† (\u00ba)</span><span class="sxs-lookup"><span data-stu-id="c002a-119">º (\u00ba)</span></span>   | `LowercaseLetter`                             | `OtherLetter`                                      |

#### <a name="version-introduced"></a><span data-ttu-id="c002a-120">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="c002a-120">Version introduced</span></span>

<span data-ttu-id="c002a-121">.NET 5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="c002a-121">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c002a-122">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="c002a-122">Recommended action</span></span>

<span data-ttu-id="c002a-123">Sınıfını kullanarak Unicode karakter kategorisini alan herhangi bir kodunuz varsa <xref:System.Char> ve kategorinin hiçbir şekilde değişmediğini kabul eterdiğinizi, güncelleştirmeniz gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="c002a-123">If you have any code that gets the Unicode character category by using the <xref:System.Char> class and assumes the category will never change, you may need to update it.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c002a-124">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="c002a-124">Reason for change</span></span>

<span data-ttu-id="c002a-125">Bu değişiklik, türü tarafından döndürülen kategorilerin <xref:System.Char> hem Unicode standardı hem de türü ile tutarlı olması için yapılmıştır <xref:System.Globalization.CharUnicodeInfo> .</span><span class="sxs-lookup"><span data-stu-id="c002a-125">This change was made so that the categories returned by the <xref:System.Char> type are consistent with both the Unicode standard and the <xref:System.Globalization.CharUnicodeInfo> type.</span></span>

#### <a name="category"></a><span data-ttu-id="c002a-126">Kategori</span><span class="sxs-lookup"><span data-stu-id="c002a-126">Category</span></span>

- <span data-ttu-id="c002a-127">Core .NET kitaplıkları</span><span class="sxs-lookup"><span data-stu-id="c002a-127">Core .NET libraries</span></span>
- <span data-ttu-id="c002a-128">Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="c002a-128">Globalization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c002a-129">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="c002a-129">Affected APIs</span></span>

- <xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>
- <xref:System.Char.IsLetter%2A?displayProperty=fullName>
- <xref:System.Char.IsPunctuation%2A?displayProperty=fullName>
- <xref:System.Char.IsSymbol%2A?displayProperty=fullName>
- <xref:System.Char.IsLower%2A?displayProperty=fullName>

<span data-ttu-id="c002a-130">Ayrıca, <xref:System.Char> Unicode karakter kategorisini elde etmek için bağlı olan herhangi bir sınıf, örneğin, <xref:System.Text.RegularExpressions.Regex> Bu değişiklikten etkilenir.</span><span class="sxs-lookup"><span data-stu-id="c002a-130">Additionally, any class that depends on <xref:System.Char> to obtain the Unicode character category, for example, <xref:System.Text.RegularExpressions.Regex>, is affected by this change.</span></span>

<!--

#### Affected APIs

- `Overload:System.Char.GetUnicodeCategory`
- `Overload:System.Char.IsLetter`
- `Overload:System.Char.IsPunctuation`
- `Overload:System.Char.IsSymbol`
- `Overload:System.Char.IsLower`

-->
