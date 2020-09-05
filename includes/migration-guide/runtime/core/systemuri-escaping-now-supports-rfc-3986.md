---
ms.openlocfilehash: e7001fcfdf88fd9e710fbb702f2ed39d63b1e080
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496132"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a><span data-ttu-id="13247-101">System. Uri kaçış artık RFC 3986 ' i desteklemektedir</span><span class="sxs-lookup"><span data-stu-id="13247-101">System.Uri escaping now supports RFC 3986</span></span>

#### <a name="details"></a><span data-ttu-id="13247-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="13247-102">Details</span></span>

<span data-ttu-id="13247-103">.NET Framework 4,5 ' de, [RFC 3986](https://tools.ietf.org/html/rfc3986)' i desteklemek için URI kaçış değeri değişti.</span><span class="sxs-lookup"><span data-stu-id="13247-103">URI escaping has changed in .NET Framework 4.5 to support [RFC 3986](https://tools.ietf.org/html/rfc3986).</span></span> <span data-ttu-id="13247-104">Belirli değişiklikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="13247-104">Specific changes include:</span></span><ul><li><span data-ttu-id="13247-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> RFC 3986 ' i temel alarak ayrılmış karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="13247-105"><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName> escapes reserved characters based on RFC 3986.</span></span></li><li><span data-ttu-id="13247-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> ayrılmış karakterlerden kaçış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="13247-106"><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName> does not escape reserved characters.</span></span></li><li><span data-ttu-id="13247-107"><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> geçersiz bir kaçış dizisiyle karşılaşırsa özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="13247-107"><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> does not throw an exception if it encounters an invalid escape sequence.</span></span></li><li><span data-ttu-id="13247-108">Ayrılmamış kaçış karakterleri, kaçılmamış durumdadır.</span><span class="sxs-lookup"><span data-stu-id="13247-108">Unreserved escaped characters are un-escaped.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="13247-109">Öneri</span><span class="sxs-lookup"><span data-stu-id="13247-109">Suggestion</span></span>

<ul><li><span data-ttu-id="13247-110">Uygulamaları <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> , geçersiz bir kaçış sırası durumunda throw 'e dayanmayan olarak güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="13247-110">Update applications to not rely on <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> to throw in the case of an invalid escape sequence.</span></span> <span data-ttu-id="13247-111">Bu tür diziler doğrudan hemen algılanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="13247-111">Such sequences must be detected directly now.</span></span></li><li><span data-ttu-id="13247-112">Benzer şekilde, kaçış ve kaçışsız URI ve veri dizelerinin .NET Framework 4,0 ve .NET Framework 4,5 ' den değişebildiğinden ve .NET sürümleri arasında doğrudan karşılaştırılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="13247-112">Similarly, expect that Escaped and Unescaped URI and Data strings may vary from .NET Framework 4.0 and .NET Framework 4.5 and should not be compared across .NET versions directly.</span></span> <span data-ttu-id="13247-113">Bunun yerine, karşılaştırmalar yapılmadan önce bunların tek bir .NET sürümünde ayrıştırılıp normalleştirilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="13247-113">Instead, they should be parsed and normalized in a single .NET version before any comparisons are made.</span></span></li></ul>

| <span data-ttu-id="13247-114">Name</span><span class="sxs-lookup"><span data-stu-id="13247-114">Name</span></span>    | <span data-ttu-id="13247-115">Değer</span><span class="sxs-lookup"><span data-stu-id="13247-115">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="13247-116">Kapsam</span><span class="sxs-lookup"><span data-stu-id="13247-116">Scope</span></span>   |<span data-ttu-id="13247-117">İkincil</span><span class="sxs-lookup"><span data-stu-id="13247-117">Minor</span></span>|
|<span data-ttu-id="13247-118">Sürüm</span><span class="sxs-lookup"><span data-stu-id="13247-118">Version</span></span>|<span data-ttu-id="13247-119">4,5</span><span class="sxs-lookup"><span data-stu-id="13247-119">4.5</span></span>|
|<span data-ttu-id="13247-120">Tür</span><span class="sxs-lookup"><span data-stu-id="13247-120">Type</span></span>|<span data-ttu-id="13247-121">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="13247-121">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="13247-122">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="13247-122">Affected APIs</span></span>

- <xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType>
- <xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType>
- <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Uri.EscapeDataString(System.String)`
- `M:System.Uri.EscapeUriString(System.String)`
- `M:System.Uri.UnescapeDataString(System.String)`

-->
