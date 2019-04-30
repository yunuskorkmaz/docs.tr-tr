---
title: 225 - TraceCorrelationKeys
ms.date: 03/30/2017
ms.assetid: d9083aaf-3816-4c1c-bae0-2d7f49628345
ms.openlocfilehash: 0bb54387dbd738a01225008edfc45ecb7297cd00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755668"
---
# <a name="225---tracecorrelationkeys"></a><span data-ttu-id="3893b-102">225 - TraceCorrelationKeys</span><span class="sxs-lookup"><span data-stu-id="3893b-102">225 - TraceCorrelationKeys</span></span>
## <a name="properties"></a><span data-ttu-id="3893b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3893b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3893b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="3893b-104">ID</span></span>|<span data-ttu-id="3893b-105">225</span><span class="sxs-lookup"><span data-stu-id="3893b-105">225</span></span>|  
|<span data-ttu-id="3893b-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="3893b-106">Keywords</span></span>|<span data-ttu-id="3893b-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3893b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3893b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="3893b-108">Level</span></span>|<span data-ttu-id="3893b-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="3893b-109">Information</span></span>|  
|<span data-ttu-id="3893b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="3893b-110">Channel</span></span>|<span data-ttu-id="3893b-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="3893b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3893b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3893b-112">Description</span></span>  
 <span data-ttu-id="3893b-113">Bu olay, bir iş akışı hizmeti için içerik temelli bağıntı kullanıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="3893b-113">This event is emitted when content-based correlation is used for a workflow service.</span></span> <span data-ttu-id="3893b-114">Bu örneği mesajıyla uygulanan bağıntı anahtarlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="3893b-114">It contains the correlation keys that are applied to correlate a message to an instance.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3893b-115">İleti</span><span class="sxs-lookup"><span data-stu-id="3893b-115">Message</span></span>  
 <span data-ttu-id="3893b-116">Bağıntı anahtar '%1' değerleri '%2' üst kapsamda '%3' kullanılarak hesaplanır.</span><span class="sxs-lookup"><span data-stu-id="3893b-116">Calculated correlation key '%1' using values '%2' in parent scope '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3893b-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3893b-117">Details</span></span>  
  
|<span data-ttu-id="3893b-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="3893b-118">Data Item Name</span></span>|<span data-ttu-id="3893b-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="3893b-119">Data Item Type</span></span>|<span data-ttu-id="3893b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3893b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3893b-121">Örnek anahtarı</span><span class="sxs-lookup"><span data-stu-id="3893b-121">Instance Key</span></span>|`xs:GUID`|<span data-ttu-id="3893b-122">Bağıntı değerlerden oluşturulan anahtar.</span><span class="sxs-lookup"><span data-stu-id="3893b-122">The key that was generated from the correlation values.</span></span>|  
|<span data-ttu-id="3893b-123">Değerler</span><span class="sxs-lookup"><span data-stu-id="3893b-123">Values</span></span>|`xs:string`|<span data-ttu-id="3893b-124">Bağıntı örneği anahtarı hesaplamak için kullanılan değerler.</span><span class="sxs-lookup"><span data-stu-id="3893b-124">The values that were used to compute the correlation instance key.</span></span>|  
|<span data-ttu-id="3893b-125">Üst kapsam</span><span class="sxs-lookup"><span data-stu-id="3893b-125">Parent Scope</span></span>|`xs:string`||  
|<span data-ttu-id="3893b-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="3893b-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="3893b-127">Bu alan, barındırılan Web Hizmetleri için Hizmet Web hiyerarşideki benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3893b-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3893b-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="3893b-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3893b-129">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="3893b-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3893b-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3893b-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3893b-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="3893b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
