---
description: 'Hakkında daha fazla bilgi edinin: 303-UserDefinedInformationEventOccured'
title: 303 - UserDefinedInformationEventOccured
ms.date: 03/30/2017
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
ms.openlocfilehash: 51c4acd5d10a2d563dd7fbcebf90b75c64ff20ad
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794240"
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="14817-103">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="14817-103">303 - UserDefinedInformationEventOccured</span></span>

## <a name="properties"></a><span data-ttu-id="14817-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="14817-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="14817-105">ID</span><span class="sxs-lookup"><span data-stu-id="14817-105">ID</span></span>|<span data-ttu-id="14817-106">303</span><span class="sxs-lookup"><span data-stu-id="14817-106">303</span></span>|  
|<span data-ttu-id="14817-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="14817-107">Keywords</span></span>|<span data-ttu-id="14817-108">Sorun giderme, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="14817-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="14817-109">Level</span><span class="sxs-lookup"><span data-stu-id="14817-109">Level</span></span>|<span data-ttu-id="14817-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="14817-110">Information</span></span>|  
|<span data-ttu-id="14817-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="14817-111">Channel</span></span>|<span data-ttu-id="14817-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="14817-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="14817-113">Description</span><span class="sxs-lookup"><span data-stu-id="14817-113">Description</span></span>  

 <span data-ttu-id="14817-114">Bu olay kullanıcı kodundan yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="14817-114">This event is emitted from user code.</span></span> <span data-ttu-id="14817-115">Geliştiriciler, hizmetinde özel tanımlanmış bilgilendirici bir olay gerçekleştiğinde bu olayı oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="14817-115">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="14817-116">Bu, API 'ler kullanılarak yapılabilir <xref:System.Diagnostics.Eventing> .</span><span class="sxs-lookup"><span data-stu-id="14817-116">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="14817-117">Ayrıca, bu API 'YI sarmalayan ve bu olayı doğru şekilde nasıl yayılacağını gösteren bir WCF örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="14817-117">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="14817-118">İleti</span><span class="sxs-lookup"><span data-stu-id="14817-118">Message</span></span>  

 <span data-ttu-id="14817-119">Ad: ' %1 ', başvuru: ' %2 ', yük: %3</span><span class="sxs-lookup"><span data-stu-id="14817-119">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="14817-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="14817-120">Details</span></span>  
  
|<span data-ttu-id="14817-121">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="14817-121">Data Item Name</span></span>|<span data-ttu-id="14817-122">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="14817-122">Data Item Type</span></span>|<span data-ttu-id="14817-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="14817-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="14817-124">Ad</span><span class="sxs-lookup"><span data-stu-id="14817-124">Name</span></span>|`xs:string`|<span data-ttu-id="14817-125">Etkinliğin Kullanıcı tanımlı adı</span><span class="sxs-lookup"><span data-stu-id="14817-125">The user-defined name of the event</span></span>|  
|<span data-ttu-id="14817-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="14817-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="14817-127">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="14817-127">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="14817-128">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="14817-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="14817-129">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="14817-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="14817-130">Te</span><span class="sxs-lookup"><span data-stu-id="14817-130">Payload</span></span>|`xs:string`|<span data-ttu-id="14817-131">Etkinliğin Kullanıcı tanımlı yükü.</span><span class="sxs-lookup"><span data-stu-id="14817-131">The user-defined payload of the event.</span></span>|
