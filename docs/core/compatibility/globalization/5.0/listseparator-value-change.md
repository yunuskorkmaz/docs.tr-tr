---
title: 'Son değişiklik: TextInfo. ListSeparator değer değişikliği'
description: 5,0 ve 5.0.1 sürümleri arasında TextInfo. ListSeparator öğesinin varsayılan değerinin değiştiği .NET 5 ile ilgili bir değişiklik hakkında bilgi edinin.
ms.date: 12/10/2020
ms.openlocfilehash: 9a319da8ea8e3cbf62cbf4730e553b03f5bfdc89
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256731"
---
# <a name="textinfolistseparator-values-changed"></a><span data-ttu-id="56ff1-103">TextInfo. ListSeparator değerleri değişti</span><span class="sxs-lookup"><span data-stu-id="56ff1-103">TextInfo.ListSeparator values changed</span></span>

<span data-ttu-id="56ff1-104"><xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType>Farklı kültürler için varsayılan değerler tüm işletim sistemlerinde değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="56ff1-104">The default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures have changed on all operating systems.</span></span>

## <a name="change-description"></a><span data-ttu-id="56ff1-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="56ff1-105">Change description</span></span>

<span data-ttu-id="56ff1-106">.NET 5.0.0 'de, [NLS 'den ICU kitaplıklarına geçiş](icu-globalization-api.md)bir parçası olarak, <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> farklı kültürler Için varsayılan değerler Windows üzerinde değişmiştir.</span><span class="sxs-lookup"><span data-stu-id="56ff1-106">In .NET 5.0.0, as part of the [switch from NLS to ICU libraries](icu-globalization-api.md), the default <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for different cultures changed on Windows.</span></span> <span data-ttu-id="56ff1-107">Unicode (ıCU) için uluslararası bileşenlerden alınan ondalık ayırıcı değerleri, değerler olarak kullanılmıştır <xref:System.Globalization.TextInfo.ListSeparator> .</span><span class="sxs-lookup"><span data-stu-id="56ff1-107">Decimal separator values, obtained from International Components for Unicode (ICU), were used as the <xref:System.Globalization.TextInfo.ListSeparator> values.</span></span> <span data-ttu-id="56ff1-108">Linux ve macOS 'ta, değerlerde hiçbir değişiklik yoktu <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> ; diğer bir deyişle, ondalık ayırıcı değerlerini kullanmaya devam ederler.</span><span class="sxs-lookup"><span data-stu-id="56ff1-108">On Linux and macOS, there was no change in <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values; that is, they continued to use decimal separator values.</span></span>

<span data-ttu-id="56ff1-109">.NET 5.0.1 ve sonraki sürümlerindeki tüm işletim sistemleri için değerleri, <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> NLS 'den elde edilecek değerlerle eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="56ff1-109">For all operating systems in .NET 5.0.1 and later versions, the values for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> are equivalent to the values that would be obtained from NLS.</span></span> <span data-ttu-id="56ff1-110">Windows için bu, değerlerin .NET Framework ve .NET Core 1,0-3,1 ' de oldukları değere eşit olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="56ff1-110">For Windows, this means the values are equivalent to what they were in .NET Framework and .NET Core 1.0 - 3.1.</span></span> <span data-ttu-id="56ff1-111">Linux ve macOS için, <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> değerler artık <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> Windows için değerlerle eşleşir.</span><span class="sxs-lookup"><span data-stu-id="56ff1-111">For Linux and macOS, the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values now match the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values for Windows.</span></span>

<span data-ttu-id="56ff1-112">Aşağıdaki tabloda değerleri için değişiklikler özetlenmektedir <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="56ff1-112">The following table summarizes the changes for <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

| | <span data-ttu-id="56ff1-113">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="56ff1-113">.NET Framework</span></span><br/><span data-ttu-id="56ff1-114">.NET Core 1,0-3,1</span><span class="sxs-lookup"><span data-stu-id="56ff1-114">.NET Core 1.0 - 3.1</span></span> | <span data-ttu-id="56ff1-115">.NET 5</span><span class="sxs-lookup"><span data-stu-id="56ff1-115">.NET 5</span></span> | <span data-ttu-id="56ff1-116">.NET 5.0.1</span><span class="sxs-lookup"><span data-stu-id="56ff1-116">.NET 5.0.1</span></span> |
-|-|-|-
| <span data-ttu-id="56ff1-117">**Windows**</span><span class="sxs-lookup"><span data-stu-id="56ff1-117">**Windows**</span></span> | <span data-ttu-id="56ff1-118">NLS 'den al</span><span class="sxs-lookup"><span data-stu-id="56ff1-118">Obtain from NLS</span></span> | <span data-ttu-id="56ff1-119">ICU 'dan ondalık ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="56ff1-119">Decimal separator from ICU.</span></span><br/><span data-ttu-id="56ff1-120">, NLS 'ye geri dönebilir.</span><span class="sxs-lookup"><span data-stu-id="56ff1-120">Can switch back to NLS.</span></span> | <span data-ttu-id="56ff1-121">NLS ile eşdeğer</span><span class="sxs-lookup"><span data-stu-id="56ff1-121">Equivalent to NLS</span></span> |
| <span data-ttu-id="56ff1-122">**Linux ve macOS**</span><span class="sxs-lookup"><span data-stu-id="56ff1-122">**Linux and macOS**</span></span> | <span data-ttu-id="56ff1-123">ICU 'den ondalık ayırıcı</span><span class="sxs-lookup"><span data-stu-id="56ff1-123">Decimal separator from ICU</span></span> | <span data-ttu-id="56ff1-124">ICU 'den ondalık ayırıcı</span><span class="sxs-lookup"><span data-stu-id="56ff1-124">Decimal separator from ICU</span></span> | <span data-ttu-id="56ff1-125">NLS ile eşdeğer</span><span class="sxs-lookup"><span data-stu-id="56ff1-125">Equivalent to NLS</span></span> |

## <a name="version-introduced"></a><span data-ttu-id="56ff1-126">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="56ff1-126">Version introduced</span></span>

<span data-ttu-id="56ff1-127">5.0.1</span><span class="sxs-lookup"><span data-stu-id="56ff1-127">5.0.1</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="56ff1-128">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="56ff1-128">Reason for change</span></span>

<span data-ttu-id="56ff1-129">Geliştiriciler, <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> virgülle ayrılmış değer (CSV) dosyalarını ayrıştırırken özelliği kullandıklarını ve yeni değerlerin bu ayrıştırma ile ilgili olduğunu bildirdi <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="56ff1-129">Developers reported that they use the <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> property when parsing comma-separated value (CSV) files, and the new <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values broke that parsing.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="56ff1-130">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="56ff1-130">Recommended action</span></span>

<span data-ttu-id="56ff1-131">Kodunuz önceki ondalık ayırıcı değerlerini kullanıyorsa, istenen <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> değerleri gönderebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="56ff1-131">If your code relies on the previous decimal separator values, you can hardcode the desired <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> values.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="56ff1-132">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="56ff1-132">Affected APIs</span></span>

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
