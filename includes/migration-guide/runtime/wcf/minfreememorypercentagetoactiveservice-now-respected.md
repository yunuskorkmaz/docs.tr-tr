---
ms.openlocfilehash: b23182ad1da8208a69b78fc7bc872780d386a59a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496257"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="2c40c-101">Minfreememoryyüztagetoactiveservice artık dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="2c40c-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="2c40c-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2c40c-102">Details</span></span>

<span data-ttu-id="2c40c-103">Bu ayar, bir WCF hizmetinin etkinleştirilmeden önce sunucuda kullanılabilir olması gereken en düşük belleği belirler.</span><span class="sxs-lookup"><span data-stu-id="2c40c-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="2c40c-104">Özel durumları engellemek için tasarlanmıştır <xref:System.OutOfMemoryException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="2c40c-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="2c40c-105">.NET Framework 4,5 ' de, bu ayarın etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2c40c-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="2c40c-106">.NET Framework 4.5.1, ayar izlenir.</span><span class="sxs-lookup"><span data-stu-id="2c40c-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2c40c-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="2c40c-107">Suggestion</span></span>

<span data-ttu-id="2c40c-108">Web sunucusunda kullanılabilir boş bellek yapılandırma ayarı tarafından tanımlanan yüzdeden küçükse bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="2c40c-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="2c40c-109">Başarılı bir şekilde başlatılan ve kısıtlanmış bir bellek ortamında çalıştırılan bazı WCF Hizmetleri artık başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c40c-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="2c40c-110">Name</span><span class="sxs-lookup"><span data-stu-id="2c40c-110">Name</span></span>    | <span data-ttu-id="2c40c-111">Değer</span><span class="sxs-lookup"><span data-stu-id="2c40c-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2c40c-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="2c40c-112">Scope</span></span>   |<span data-ttu-id="2c40c-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="2c40c-113">Minor</span></span>|
|<span data-ttu-id="2c40c-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="2c40c-114">Version</span></span>|<span data-ttu-id="2c40c-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="2c40c-115">4.5.1</span></span>|
|<span data-ttu-id="2c40c-116">Tür</span><span class="sxs-lookup"><span data-stu-id="2c40c-116">Type</span></span>|<span data-ttu-id="2c40c-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="2c40c-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="2c40c-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="2c40c-118">Affected APIs</span></span>

<span data-ttu-id="2c40c-119">API analizi aracılığıyla algılanamaz.</span><span class="sxs-lookup"><span data-stu-id="2c40c-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
