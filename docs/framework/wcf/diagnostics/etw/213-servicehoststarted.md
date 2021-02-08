---
description: 'Hakkında daha fazla bilgi edinin: 213-ServiceHostStarted'
title: 213 - ServiceHostStarted
ms.date: 03/30/2017
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
ms.openlocfilehash: 5e2b5b7c633ef053c449ad62c4f8fee40798a386
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794422"
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="4786d-103">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="4786d-103">213 - ServiceHostStarted</span></span>

## <a name="properties"></a><span data-ttu-id="4786d-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4786d-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4786d-105">ID</span><span class="sxs-lookup"><span data-stu-id="4786d-105">ID</span></span>|<span data-ttu-id="4786d-106">213</span><span class="sxs-lookup"><span data-stu-id="4786d-106">213</span></span>|  
|<span data-ttu-id="4786d-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4786d-107">Keywords</span></span>|<span data-ttu-id="4786d-108">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceHost</span><span class="sxs-lookup"><span data-stu-id="4786d-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="4786d-109">Level</span><span class="sxs-lookup"><span data-stu-id="4786d-109">Level</span></span>|<span data-ttu-id="4786d-110">Günlüğe kaydetme her zaman</span><span class="sxs-lookup"><span data-stu-id="4786d-110">LogAlways</span></span>|  
|<span data-ttu-id="4786d-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="4786d-111">Channel</span></span>|<span data-ttu-id="4786d-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="4786d-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4786d-113">Description</span><span class="sxs-lookup"><span data-stu-id="4786d-113">Description</span></span>  

 <span data-ttu-id="4786d-114">Bu olay, Web 'de barındırılan bir hizmet ana bilgisayarı başlatıldığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="4786d-114">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="4786d-115">Bu genellikle hizmet bir ileti tarafından etkinleştirildiğinde meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="4786d-115">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="4786d-116">Hizmet otomatik olarak başlatılacak şekilde yapılandırıldıysa da bu durum oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="4786d-116">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4786d-117">İleti</span><span class="sxs-lookup"><span data-stu-id="4786d-117">Message</span></span>  

 <span data-ttu-id="4786d-118">ServiceHost başlatıldı: ' %1 '.</span><span class="sxs-lookup"><span data-stu-id="4786d-118">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4786d-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4786d-119">Details</span></span>  
  
|<span data-ttu-id="4786d-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4786d-120">Data Item Name</span></span>|<span data-ttu-id="4786d-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4786d-121">Data Item Type</span></span>|<span data-ttu-id="4786d-122">Description</span><span class="sxs-lookup"><span data-stu-id="4786d-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4786d-123">Hizmet türü adı</span><span class="sxs-lookup"><span data-stu-id="4786d-123">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="4786d-124">Hizmet uygulamasının türünün CLR FullName.</span><span class="sxs-lookup"><span data-stu-id="4786d-124">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="4786d-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="4786d-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="4786d-126">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4786d-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4786d-127">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4786d-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4786d-128">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="4786d-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4786d-129">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4786d-129">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4786d-130">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4786d-130">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
