---
title: 303 - UserDefinedInformationEventOccured
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ed5acaf-3755-4417-92c4-4ebc8e854ca1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3bc04837834277dccc9d21d27e89c84f09f36167
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="66e90-102">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="66e90-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="66e90-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="66e90-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="66e90-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="66e90-104">ID</span></span>|<span data-ttu-id="66e90-105">303</span><span class="sxs-lookup"><span data-stu-id="66e90-105">303</span></span>|  
|<span data-ttu-id="66e90-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="66e90-106">Keywords</span></span>|<span data-ttu-id="66e90-107">Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="66e90-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="66e90-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="66e90-108">Level</span></span>|<span data-ttu-id="66e90-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="66e90-109">Information</span></span>|  
|<span data-ttu-id="66e90-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="66e90-110">Channel</span></span>|<span data-ttu-id="66e90-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="66e90-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="66e90-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66e90-112">Description</span></span>  
 <span data-ttu-id="66e90-113">Bu olay, kullanıcı kodundan yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="66e90-113">This event is emitted from user code.</span></span> <span data-ttu-id="66e90-114">Geliştiriciler kendi hizmetinde özel tanımlı bilgilendirici olay ortaya çıktığında bu olay yayma.</span><span class="sxs-lookup"><span data-stu-id="66e90-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="66e90-115">Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri.</span><span class="sxs-lookup"><span data-stu-id="66e90-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="66e90-116">Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="66e90-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="66e90-117">İleti</span><span class="sxs-lookup"><span data-stu-id="66e90-117">Message</span></span>  
 <span data-ttu-id="66e90-118">Ad: '%1', başvuru: '%2', yük: % 3</span><span class="sxs-lookup"><span data-stu-id="66e90-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="66e90-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="66e90-119">Details</span></span>  
  
|<span data-ttu-id="66e90-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="66e90-120">Data Item Name</span></span>|<span data-ttu-id="66e90-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="66e90-121">Data Item Type</span></span>|<span data-ttu-id="66e90-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="66e90-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="66e90-123">Ad</span><span class="sxs-lookup"><span data-stu-id="66e90-123">Name</span></span>|`xs:string`|<span data-ttu-id="66e90-124">Olayın kullanıcı tanımlı adı</span><span class="sxs-lookup"><span data-stu-id="66e90-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="66e90-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="66e90-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="66e90-126">Bu alan, barındırılan Web Hizmetleri için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="66e90-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="66e90-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="66e90-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="66e90-128">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="66e90-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="66e90-129">Yükü</span><span class="sxs-lookup"><span data-stu-id="66e90-129">Payload</span></span>|`xs:string`|<span data-ttu-id="66e90-130">Kullanıcı tanımlı yükü olay.</span><span class="sxs-lookup"><span data-stu-id="66e90-130">The user-defined payload of the event.</span></span>|
