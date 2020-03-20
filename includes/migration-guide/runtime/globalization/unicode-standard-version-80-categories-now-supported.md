---
ms.openlocfilehash: efa0efaf40e2e432d477f1659d7bde3abc98241d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67857475"
---
### <a name="unicode-standard-version-80-categories-now-supported"></a><span data-ttu-id="58014-101">Unicode standart sürüm 8.0 kategorileri şimdi desteklenen</span><span class="sxs-lookup"><span data-stu-id="58014-101">Unicode standard version 8.0 categories now supported</span></span>

|   |   |
|---|---|
|<span data-ttu-id="58014-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="58014-102">Details</span></span>|<span data-ttu-id="58014-103">.NET Framework 4.6.2'de, Unicode verileri Unicode Standard sürüm 6.3'ten sürüm 8.0'a yükseltildi.</span><span class="sxs-lookup"><span data-stu-id="58014-103">In .NET Framework 4.6.2, Unicode data has been upgraded from Unicode Standard version 6.3 to version 8.0.</span></span>  <span data-ttu-id="58014-104">.NET Framework 4.6.2'de Unicode karakter kategorileri istenirken, bazı sonuçlar önceki .NET Framework sürümlerindeki sonuçlarla eşleşmeyebilir.</span><span class="sxs-lookup"><span data-stu-id="58014-104">When requesting Unicode character categories in .NET Framework 4.6.2, some results might not match the results in previous .NET Framework versions.</span></span>  <span data-ttu-id="58014-105">Bu değişiklik çoğunlukla Cherokee heceleri ve Yeni Tai Lue sesli harfler işaretleri ve sesi işaretleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="58014-105">This change mostly affects Cherokee syllables and New Tai Lue vowels signs and tone marks.</span></span>|
|<span data-ttu-id="58014-106">Öneri</span><span class="sxs-lookup"><span data-stu-id="58014-106">Suggestion</span></span>|<span data-ttu-id="58014-107">Kodu gözden geçirin ve sabit kodlanmış Unicode karakter kategorilerine bağlı olan kaldırma/değiştirme mantığı.</span><span class="sxs-lookup"><span data-stu-id="58014-107">Review code and remove/change logic that depends on hard-coded Unicode character categories.</span></span>|
|<span data-ttu-id="58014-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="58014-108">Scope</span></span>|<span data-ttu-id="58014-109">İkincil</span><span class="sxs-lookup"><span data-stu-id="58014-109">Minor</span></span>|
|<span data-ttu-id="58014-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="58014-110">Version</span></span>|<span data-ttu-id="58014-111">4.6.2</span><span class="sxs-lookup"><span data-stu-id="58014-111">4.6.2</span></span>|
|<span data-ttu-id="58014-112">Tür</span><span class="sxs-lookup"><span data-stu-id="58014-112">Type</span></span>|<span data-ttu-id="58014-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="58014-113">Runtime</span></span>|
|<span data-ttu-id="58014-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="58014-114">Affected APIs</span></span>|<ul><li><xref:System.Char.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.Char)?displayProperty=nameWithType></li><li><xref:System.Globalization.CharUnicodeInfo.GetUnicodeCategory(System.String,System.Int32)?displayProperty=nameWithType></li></ul>|
