---
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 87a98d30f5ecde6f81580a95e337df22341c23d4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279031"
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="278bf-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="278bf-102">213 - ServiceHostStarted</span></span>

## <a name="properties"></a><span data-ttu-id="278bf-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="278bf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="278bf-104">ID</span><span class="sxs-lookup"><span data-stu-id="278bf-104">ID</span></span>|<span data-ttu-id="278bf-105">213</span><span class="sxs-lookup"><span data-stu-id="278bf-105">213</span></span>|  
|<span data-ttu-id="278bf-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="278bf-106">Keywords</span></span>|<span data-ttu-id="278bf-107">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceHost</span><span class="sxs-lookup"><span data-stu-id="278bf-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="278bf-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="278bf-108">Level</span></span>|<span data-ttu-id="278bf-109">Günlüğe kaydetme her zaman</span><span class="sxs-lookup"><span data-stu-id="278bf-109">LogAlways</span></span>|  
|<span data-ttu-id="278bf-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="278bf-110">Channel</span></span>|<span data-ttu-id="278bf-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="278bf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="278bf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="278bf-112">Description</span></span>  

 <span data-ttu-id="278bf-113">Bu olay, Web 'de barındırılan bir hizmet ana bilgisayarı başlatıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="278bf-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="278bf-114">Bu genellikle hizmet bir ileti tarafından etkinleştirildiğinde meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="278bf-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="278bf-115">Hizmet otomatik olarak başlatılacak şekilde yapılandırıldıysa da bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="278bf-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="278bf-116">İleti</span><span class="sxs-lookup"><span data-stu-id="278bf-116">Message</span></span>  

 <span data-ttu-id="278bf-117">ServiceHost başlatıldı: ' %1 '.</span><span class="sxs-lookup"><span data-stu-id="278bf-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="278bf-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="278bf-118">Details</span></span>  
  
|<span data-ttu-id="278bf-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="278bf-119">Data Item Name</span></span>|<span data-ttu-id="278bf-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="278bf-120">Data Item Type</span></span>|<span data-ttu-id="278bf-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="278bf-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="278bf-122">Hizmet türü adı</span><span class="sxs-lookup"><span data-stu-id="278bf-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="278bf-123">Hizmet uygulamasının türünün CLR FullName.</span><span class="sxs-lookup"><span data-stu-id="278bf-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="278bf-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="278bf-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="278bf-125">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="278bf-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="278bf-126">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="278bf-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="278bf-127">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="278bf-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="278bf-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="278bf-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="278bf-129">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="278bf-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
