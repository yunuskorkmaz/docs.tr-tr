---
ms.openlocfilehash: 14581b193fc000c7f805a0602e191cad688c014a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497460"
---
### <a name="persian-calendar-now-uses-the-hijri-solar-algorithm"></a><span data-ttu-id="b5e64-101">Farsça takvimi artık Hicri güneş algoritmasını kullanıyor</span><span class="sxs-lookup"><span data-stu-id="b5e64-101">Persian calendar now uses the Hijri solar algorithm</span></span>

#### <a name="details"></a><span data-ttu-id="b5e64-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b5e64-102">Details</span></span>

<span data-ttu-id="b5e64-103">.NET Framework 4,6 ' den başlayarak, <xref:System.Globalization.PersianCalendar?displayProperty=fullName> sınıfı Hicri Solar algoritmasını kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5e64-103">Starting with the .NET Framework 4.6, the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> class uses the Hijri solar algorithm.</span></span> <span data-ttu-id="b5e64-104">Ve diğer takvimler arasındaki tarihleri dönüştürmek, <xref:System.Globalization.PersianCalendar?displayProperty=fullName> 2023 1800 ' den (Gregoryen) daha önceki tarihler için .NET Framework 4,6 ' den başlayarak biraz farklı bir sonuç üretebilir. Ayrıca, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> artık <code>March 22, 0622</code> yerine <code>March 21, 0622</code> .</span><span class="sxs-lookup"><span data-stu-id="b5e64-104">Converting dates between the <xref:System.Globalization.PersianCalendar?displayProperty=fullName> and other calendars may produce a slightly different result beginning with the .NET Framework 4.6 for dates earlier than 1800 or later than 2023 (Gregorian).Also, <xref:System.Globalization.PersianCalendar.MinSupportedDateTime?displayProperty=nameWithType> is now <code>March 22, 0622</code> instead of <code>March 21, 0622</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b5e64-105">Öneri</span><span class="sxs-lookup"><span data-stu-id="b5e64-105">Suggestion</span></span>

<span data-ttu-id="b5e64-106">.NET Framework 4,6 ' de Persıancalendar kullanılırken erken veya geç tarihlerin biraz farklı olabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="b5e64-106">Be aware that some early or late dates may be slightly different when using the PersianCalendar in .NET Framework 4.6.</span></span> <span data-ttu-id="b5e64-107">Ayrıca, farklı .NET Framework sürümlerde çalışabilen süreçler arasındaki tarihleri serileştirilirken, bu değerler farklı olabileceğinden, bunları bir veya daha fazla takvim tarih dizesi olarak saklamayın.</span><span class="sxs-lookup"><span data-stu-id="b5e64-107">Also, when serializing dates between processes which may run on different .NET Framework versions, do not store them as PersianCalendar date strings (since those values may be different).</span></span>

| <span data-ttu-id="b5e64-108">Name</span><span class="sxs-lookup"><span data-stu-id="b5e64-108">Name</span></span>    | <span data-ttu-id="b5e64-109">Değer</span><span class="sxs-lookup"><span data-stu-id="b5e64-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b5e64-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b5e64-110">Scope</span></span>   |<span data-ttu-id="b5e64-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="b5e64-111">Minor</span></span>|
|<span data-ttu-id="b5e64-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b5e64-112">Version</span></span>|<span data-ttu-id="b5e64-113">4.6</span><span class="sxs-lookup"><span data-stu-id="b5e64-113">4.6</span></span>|
|<span data-ttu-id="b5e64-114">Tür</span><span class="sxs-lookup"><span data-stu-id="b5e64-114">Type</span></span>|<span data-ttu-id="b5e64-115">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b5e64-115">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b5e64-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b5e64-116">Affected APIs</span></span>

- <xref:System.Globalization.PersianCalendar?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:System.Globalization.PersianCalendar`

-->
