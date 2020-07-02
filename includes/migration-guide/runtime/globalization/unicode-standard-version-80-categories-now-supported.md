---
ms.openlocfilehash: a20fad5f9c95e59c14ffd91f4921cf8bfab443cd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621375"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="25d1e-101">Unicode standart sürüm 8,0 kategorileri artık destekleniyor</span><span class="sxs-lookup"><span data-stu-id="25d1e-101">Unicode standard version 8.0 categories now supported</span></span>

#### <a name="details"></a><span data-ttu-id="25d1e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="25d1e-102">Details</span></span>

<span data-ttu-id="25d1e-103">.NET Framework 4.6.2 ' de Unicode verileri, Unicode standart 6,3 sürümünden 8,0 sürümüne yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="25d1e-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="25d1e-104">.NET Framework 4.6.2 ' de Unicode karakter kategorileri istenirken, bazı sonuçlar önceki .NET Framework sürümlerindeki sonuçlarla eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="25d1e-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="25d1e-105">Bu değişiklik genellikle Çeroki heceleri ve yeni Day lü sesli işaretleri ve ses işaretlerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="25d1e-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="25d1e-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="25d1e-106">Suggestion</span></span>

<span data-ttu-id="25d1e-107">Kodu gözden geçirin ve sabit kodlanmış Unicode karakter kategorilerine bağlı olan mantığı kaldırın/değiştirin.</span><span class="sxs-lookup"><span data-stu-id="25d1e-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>

| <span data-ttu-id="25d1e-108">Name</span><span class="sxs-lookup"><span data-stu-id="25d1e-108">Name</span></span>    | <span data-ttu-id="25d1e-109">Değer</span><span class="sxs-lookup"><span data-stu-id="25d1e-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="25d1e-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="25d1e-110">Scope</span></span>   |<span data-ttu-id="25d1e-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="25d1e-111">Minor</span></span>|
|<span data-ttu-id="25d1e-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="25d1e-112">Version</span></span>|<span data-ttu-id="25d1e-113">4.6.2</span><span class="sxs-lookup"><span data-stu-id="25d1e-113">4.6.2</span></span>|
|<span data-ttu-id="25d1e-114">Tür</span><span class="sxs-lookup"><span data-stu-id="25d1e-114">Type</span></span>|<span data-ttu-id="25d1e-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="25d1e-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="25d1e-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="25d1e-116">Affected APIs</span></span>

-<xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
