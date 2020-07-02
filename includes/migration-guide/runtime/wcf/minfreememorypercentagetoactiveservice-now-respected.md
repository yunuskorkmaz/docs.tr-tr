---
ms.openlocfilehash: f8e5dee9e97956cea78b7c8ec999af1afe9ac66b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620651"
---
### <a name="minfreememorypercentagetoactiveservice-is-now-respected"></a><span data-ttu-id="50019-101">Minfreememoryyüztagetoactiveservice artık dikkate alındı</span><span class="sxs-lookup"><span data-stu-id="50019-101">MinFreeMemoryPercentageToActiveService is now respected</span></span>

#### <a name="details"></a><span data-ttu-id="50019-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="50019-102">Details</span></span>

<span data-ttu-id="50019-103">Bu ayar, bir WCF hizmetinin etkinleştirilmeden önce sunucuda kullanılabilir olması gereken en düşük belleği belirler.</span><span class="sxs-lookup"><span data-stu-id="50019-103">This setting establishes the minimum memory that must be available on the server before a WCF service can be activated.</span></span> <span data-ttu-id="50019-104">Özel durumları engellemek için tasarlanmıştır <xref:System.OutOfMemoryException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="50019-104">It is designed to prevent <xref:System.OutOfMemoryException?displayProperty=fullName> exceptions.</span></span> <span data-ttu-id="50019-105">.NET Framework 4,5 ' de, bu ayarın etkisi yoktur.</span><span class="sxs-lookup"><span data-stu-id="50019-105">In the .NET Framework 4.5, this setting had no effect.</span></span> <span data-ttu-id="50019-106">.NET Framework 4.5.1, ayar izlenir.</span><span class="sxs-lookup"><span data-stu-id="50019-106">In the .NET Framework 4.5.1, the setting is observed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="50019-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="50019-107">Suggestion</span></span>

<span data-ttu-id="50019-108">Web sunucusunda kullanılabilir boş bellek yapılandırma ayarı tarafından tanımlanan yüzdeden küçükse bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="50019-108">An exception occurs if the free memory available on the web server is less than the percentage defined by the configuration setting.</span></span> <span data-ttu-id="50019-109">Başarılı bir şekilde başlatılan ve kısıtlanmış bir bellek ortamında çalıştırılan bazı WCF Hizmetleri artık başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="50019-109">Some WCF services that successfully started and ran in a constrained memory environment may now fail.</span></span>

| <span data-ttu-id="50019-110">Name</span><span class="sxs-lookup"><span data-stu-id="50019-110">Name</span></span>    | <span data-ttu-id="50019-111">Değer</span><span class="sxs-lookup"><span data-stu-id="50019-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="50019-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="50019-112">Scope</span></span>   |<span data-ttu-id="50019-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="50019-113">Minor</span></span>|
|<span data-ttu-id="50019-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="50019-114">Version</span></span>|<span data-ttu-id="50019-115">4.5.1</span><span class="sxs-lookup"><span data-stu-id="50019-115">4.5.1</span></span>|
|<span data-ttu-id="50019-116">Tür</span><span class="sxs-lookup"><span data-stu-id="50019-116">Type</span></span>|<span data-ttu-id="50019-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="50019-117">Runtime</span></span>|
