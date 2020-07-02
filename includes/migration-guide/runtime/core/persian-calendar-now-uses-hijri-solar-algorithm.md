---
ms.openlocfilehash: e4d9efe7d2a06a1e501b070c23184dcd913dba71
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621411"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="18803-101">Farsça takvimi artık Hicri güneş algoritmasını kullanıyor</span><span class="sxs-lookup"><span data-stu-id="18803-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="18803-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="18803-102">Details</span></span>

<span data-ttu-id="18803-103">.NET Framework 4,6 ' den başlayarak, <xref:System.Globalization.PersianCalendar?displayProperty=fullName> sınıfı Hicri Solar algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="18803-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="18803-104">Ve diğer takvimler arasındaki tarihleri dönüştürmek, <xref:System.Globalization.PersianCalendar?displayProperty=fullName> 2023 1800 ' den (Gregoryen) daha önceki tarihler için .NET Framework 4,6 ' den başlayarak biraz farklı bir sonuç üretebilir. Ayrıca, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> artık <code>March 22, 0622</code> yerine <code>March 21, 0622</code> .</span><span class="sxs-lookup"><span data-stu-id="18803-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="18803-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="18803-105">Suggestion</span></span>

<span data-ttu-id="18803-106">.NET Framework 4,6 ' de Persıancalendar kullanılırken erken veya geç tarihlerin biraz farklı olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="18803-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="18803-107">Ayrıca, farklı .NET Framework sürümlerde çalışabilen süreçler arasındaki tarihleri serileştirilirken, bu değerler farklı olabileceğinden, bunları bir veya daha fazla takvim tarih dizesi olarak saklamayın.</span><span class="sxs-lookup"><span data-stu-id="18803-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="18803-108">Name</span><span class="sxs-lookup"><span data-stu-id="18803-108">Name</span></span>    | <span data-ttu-id="18803-109">Değer</span><span class="sxs-lookup"><span data-stu-id="18803-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="18803-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="18803-110">Scope</span></span>   |<span data-ttu-id="18803-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="18803-111">Minor</span></span>|
|<span data-ttu-id="18803-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="18803-112">Version</span></span>|<span data-ttu-id="18803-113">4.6</span><span class="sxs-lookup"><span data-stu-id="18803-113">4.6</span></span>|
|<span data-ttu-id="18803-114">Tür</span><span class="sxs-lookup"><span data-stu-id="18803-114">Type</span></span>|<span data-ttu-id="18803-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="18803-115">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="18803-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="18803-116">Affected APIs</span></span>

-<xref:System.Globalization.PersianCalendar?displayProperty=nameWithType></li></ul>|
