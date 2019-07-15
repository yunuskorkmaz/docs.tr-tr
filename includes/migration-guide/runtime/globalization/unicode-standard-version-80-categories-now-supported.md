---
ms.openlocfilehash: 480cbdecd681408a7e1d6fa366e3f1a4b131ab42
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857475"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="add2e-101">Artık desteklenen Unicode standart sürümü 8.0 kategorileri</span><span class="sxs-lookup"><span data-stu-id="add2e-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="add2e-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="add2e-102">Details</span></span>|<span data-ttu-id="add2e-103">.NET Framework 4.6.2, Unicode verilerini sürüm 8.0 sürümü 6.3 Unicode standart katmandan yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="add2e-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="add2e-104">.NET Framework 4.6.2 Unicode karakter kategorileri isterken, bazı sonuçları önceki .NET Framework sürümlerini sonuçları eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="add2e-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="add2e-105">Bu çoğunlukla Çeroki hece etkiler ve Yeni Day lu sesli harfler işaretleri ve ses işaretleri değiştirin.</span><span class="sxs-lookup"><span data-stu-id="add2e-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="add2e-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="add2e-106">Suggestion</span></span>|<span data-ttu-id="add2e-107">Kodu gözden geçirin ve Unicode karakter kategorileri sabit kodlanmış bağlıdır mantıksal Kaldır/Değiştir.</span><span class="sxs-lookup"><span data-stu-id="add2e-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="add2e-108">`Scope`</span><span class="sxs-lookup"><span data-stu-id="add2e-108">Scope</span></span>|<span data-ttu-id="add2e-109">Küçük</span><span class="sxs-lookup"><span data-stu-id="add2e-109">Minor</span></span>|
|<span data-ttu-id="add2e-110">Version</span><span class="sxs-lookup"><span data-stu-id="add2e-110">Version</span></span>|<span data-ttu-id="add2e-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="add2e-111">4.6.2</span></span>|
|<span data-ttu-id="add2e-112">Type</span><span class="sxs-lookup"><span data-stu-id="add2e-112">Type</span></span>|<span data-ttu-id="add2e-113">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="add2e-113">Runtime</span></span>|
|<span data-ttu-id="add2e-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="add2e-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|

