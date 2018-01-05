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
ms.workload: dotnet
ms.openlocfilehash: 3bd4d94d457793eb036f037cc6dc22bff6d26ee2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="303---userdefinedinformationeventoccured"></a><span data-ttu-id="9aecd-102">303 - UserDefinedInformationEventOccured</span><span class="sxs-lookup"><span data-stu-id="9aecd-102">303 - UserDefinedInformationEventOccured</span></span>
## <a name="properties"></a><span data-ttu-id="9aecd-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9aecd-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9aecd-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9aecd-104">ID</span></span>|<span data-ttu-id="9aecd-105">303</span><span class="sxs-lookup"><span data-stu-id="9aecd-105">303</span></span>|  
|<span data-ttu-id="9aecd-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9aecd-106">Keywords</span></span>|<span data-ttu-id="9aecd-107">Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="9aecd-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="9aecd-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9aecd-108">Level</span></span>|<span data-ttu-id="9aecd-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9aecd-109">Information</span></span>|  
|<span data-ttu-id="9aecd-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9aecd-110">Channel</span></span>|<span data-ttu-id="9aecd-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="9aecd-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9aecd-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9aecd-112">Description</span></span>  
 <span data-ttu-id="9aecd-113">Bu olay, kullanıcı kodundan yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="9aecd-113">This event is emitted from user code.</span></span> <span data-ttu-id="9aecd-114">Geliştiriciler kendi hizmetinde özel tanımlı bilgilendirici olay ortaya çıktığında bu olay yayma.</span><span class="sxs-lookup"><span data-stu-id="9aecd-114">Developers can emit this event when a custom-defined informational event occurs in their service.</span></span> <span data-ttu-id="9aecd-115">Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri.</span><span class="sxs-lookup"><span data-stu-id="9aecd-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="9aecd-116">Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="9aecd-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9aecd-117">İleti</span><span class="sxs-lookup"><span data-stu-id="9aecd-117">Message</span></span>  
 <span data-ttu-id="9aecd-118">Ad: '%1', başvuru: '%2', yük: % 3</span><span class="sxs-lookup"><span data-stu-id="9aecd-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="9aecd-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9aecd-119">Details</span></span>  
  
|<span data-ttu-id="9aecd-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9aecd-120">Data Item Name</span></span>|<span data-ttu-id="9aecd-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9aecd-121">Data Item Type</span></span>|<span data-ttu-id="9aecd-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9aecd-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9aecd-123">Ad</span><span class="sxs-lookup"><span data-stu-id="9aecd-123">Name</span></span>|`xs:string`|<span data-ttu-id="9aecd-124">Olayın kullanıcı tanımlı adı</span><span class="sxs-lookup"><span data-stu-id="9aecd-124">The user-defined name of the event</span></span>|  
|<span data-ttu-id="9aecd-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="9aecd-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="9aecd-126">Bu alan, barındırılan Web Hizmetleri için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9aecd-126">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9aecd-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="9aecd-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9aecd-128">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="9aecd-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9aecd-129">Yükü</span><span class="sxs-lookup"><span data-stu-id="9aecd-129">Payload</span></span>|`xs:string`|<span data-ttu-id="9aecd-130">Kullanıcı tanımlı yükü olay.</span><span class="sxs-lookup"><span data-stu-id="9aecd-130">The user-defined payload of the event.</span></span>|
