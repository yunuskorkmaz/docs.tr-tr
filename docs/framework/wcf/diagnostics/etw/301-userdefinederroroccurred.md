---
description: 'Hakkında daha fazla bilgi edinin: 301-UserDefinedErrorOccurred'
title: 301 - UserDefinedErrorOccurred
ms.date: 03/30/2017
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
ms.openlocfilehash: 15e12bb27e3626f80747498a1387aa90fc461d28
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794253"
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="c5e57-103">301 - UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="c5e57-103">301 - UserDefinedErrorOccurred</span></span>

## <a name="properties"></a><span data-ttu-id="c5e57-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c5e57-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c5e57-105">ID</span><span class="sxs-lookup"><span data-stu-id="c5e57-105">ID</span></span>|<span data-ttu-id="c5e57-106">301</span><span class="sxs-lookup"><span data-stu-id="c5e57-106">301</span></span>|  
|<span data-ttu-id="c5e57-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="c5e57-107">Keywords</span></span>|<span data-ttu-id="c5e57-108">Sorun giderme, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="c5e57-108">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="c5e57-109">Level</span><span class="sxs-lookup"><span data-stu-id="c5e57-109">Level</span></span>|<span data-ttu-id="c5e57-110">Hata</span><span class="sxs-lookup"><span data-stu-id="c5e57-110">Error</span></span>|  
|<span data-ttu-id="c5e57-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="c5e57-111">Channel</span></span>|<span data-ttu-id="c5e57-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="c5e57-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c5e57-113">Description</span><span class="sxs-lookup"><span data-stu-id="c5e57-113">Description</span></span>  

 <span data-ttu-id="c5e57-114">Bu olay kullanıcı kodundan yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="c5e57-114">This event is emitted from user code.</span></span> <span data-ttu-id="c5e57-115">Geliştiriciler, hizmetinde özel olarak tanımlanan bir hata oluştuğunda bu olayı oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="c5e57-115">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="c5e57-116">Bu, API 'ler kullanılarak yapılabilir <xref:System.Diagnostics.Eventing> .</span><span class="sxs-lookup"><span data-stu-id="c5e57-116">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="c5e57-117">Ayrıca, bu API 'YI sarmalayan ve bu olayı doğru şekilde nasıl yayılacağını gösteren bir WCF örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="c5e57-117">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c5e57-118">İleti</span><span class="sxs-lookup"><span data-stu-id="c5e57-118">Message</span></span>  

 <span data-ttu-id="c5e57-119">Ad: ' %1 ', başvuru: ' %2 ', yük: %3</span><span class="sxs-lookup"><span data-stu-id="c5e57-119">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="c5e57-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c5e57-120">Details</span></span>  
  
|<span data-ttu-id="c5e57-121">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c5e57-121">Data Item Name</span></span>|<span data-ttu-id="c5e57-122">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c5e57-122">Data Item Type</span></span>|<span data-ttu-id="c5e57-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5e57-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c5e57-124">Ad</span><span class="sxs-lookup"><span data-stu-id="c5e57-124">Name</span></span>|`xs:string`|<span data-ttu-id="c5e57-125">Etkinliğin Kullanıcı tanımlı adı.</span><span class="sxs-lookup"><span data-stu-id="c5e57-125">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="c5e57-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="c5e57-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="c5e57-127">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c5e57-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c5e57-128">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c5e57-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c5e57-129">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="c5e57-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c5e57-130">Te</span><span class="sxs-lookup"><span data-stu-id="c5e57-130">Payload</span></span>|`xs:string`|<span data-ttu-id="c5e57-131">Etkinliğin Kullanıcı tanımlı yükü.</span><span class="sxs-lookup"><span data-stu-id="c5e57-131">The user-defined payload of the event.</span></span>|
