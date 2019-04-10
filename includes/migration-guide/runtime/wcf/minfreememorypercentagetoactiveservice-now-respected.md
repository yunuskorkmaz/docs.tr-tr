---
ms.openlocfilehash: fa472b3a142f55f0cbdd83eabbbb00bddd9786d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235885"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="f220b-101">MinFreeMemoryPercentageToActiveService artık uyulduğundan</span><span class="sxs-lookup"><span data-stu-id="f220b-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

|   |   |
|---|---|
|<span data-ttu-id="f220b-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f220b-102">Details</span></span>|<span data-ttu-id="f220b-103">Bu ayar, bir WCF hizmet aktif edilmeden önce sunucuda bellek alt sınırı belirler.</span><span class="sxs-lookup"><span data-stu-id="f220b-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="f220b-104">Önlemek üzere tasarlanmış <xref:System.OutOfMemoryException?displayProperty=name> özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="f220b-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=name> exceptions.</span></span> <span data-ttu-id="f220b-105">.NET Framework 4.5, bu ayarın hiçbir etkisi vardı.</span><span class="sxs-lookup"><span data-stu-id="f220b-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="f220b-106">.NET Framework 4.5.1, ayar dikkate alınır.</span><span class="sxs-lookup"><span data-stu-id="f220b-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>|
|<span data-ttu-id="f220b-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="f220b-107">Suggestion</span></span>|<span data-ttu-id="f220b-108">Web sunucusunda kullanılabilir boş bellek yapılandırma ayarları tarafından tanımlandığı yüzdenin ise bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="f220b-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="f220b-109">Başarıyla başlatıldı ve kısıtlı bellek ortamında çalışan bazı WCF hizmetlerinde başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="f220b-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>|
|<span data-ttu-id="f220b-110">Kapsam</span><span class="sxs-lookup"><span data-stu-id="f220b-110">Scope</span></span>|<span data-ttu-id="f220b-111">İkincil</span><span class="sxs-lookup"><span data-stu-id="f220b-111">Minor</span></span>|
|<span data-ttu-id="f220b-112">Sürüm</span><span class="sxs-lookup"><span data-stu-id="f220b-112">Version</span></span>|<span data-ttu-id="f220b-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="f220b-113">4.5.1</span></span>|
|<span data-ttu-id="f220b-114">Tür</span><span class="sxs-lookup"><span data-stu-id="f220b-114">Type</span></span>|<span data-ttu-id="f220b-115">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="f220b-115">Runtime</span></span>|
