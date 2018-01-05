---
title: 301 - UserDefinedErrorOccurred
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0285d1c-550f-4c14-9c36-a96e97f1c4e4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b24d54930a29a24dab97ce403c2808fb74b8cbfe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="301---userdefinederroroccurred"></a><span data-ttu-id="9f001-102">301 - UserDefinedErrorOccurred</span><span class="sxs-lookup"><span data-stu-id="9f001-102">301 - UserDefinedErrorOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="9f001-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9f001-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f001-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9f001-104">ID</span></span>|<span data-ttu-id="9f001-105">301</span><span class="sxs-lookup"><span data-stu-id="9f001-105">301</span></span>|  
|<span data-ttu-id="9f001-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9f001-106">Keywords</span></span>|<span data-ttu-id="9f001-107">Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="9f001-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="9f001-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9f001-108">Level</span></span>|<span data-ttu-id="9f001-109">Hata</span><span class="sxs-lookup"><span data-stu-id="9f001-109">Error</span></span>|  
|<span data-ttu-id="9f001-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9f001-110">Channel</span></span>|<span data-ttu-id="9f001-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="9f001-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9f001-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f001-112">Description</span></span>  
 <span data-ttu-id="9f001-113">Bu olay, kullanıcı kodundan yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="9f001-113">This event is emitted from user code.</span></span> <span data-ttu-id="9f001-114">Geliştiriciler kendi hizmetinde özel tanımlanmış bir hata oluştuğunda bu olay yayma.</span><span class="sxs-lookup"><span data-stu-id="9f001-114">Developers can emit this event when a custom-defined error occurs in their service.</span></span> <span data-ttu-id="9f001-115">Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri.</span><span class="sxs-lookup"><span data-stu-id="9f001-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="9f001-116">Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="9f001-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9f001-117">İleti</span><span class="sxs-lookup"><span data-stu-id="9f001-117">Message</span></span>  
 <span data-ttu-id="9f001-118">Ad: '%1', başvuru: '%2', yük: % 3</span><span class="sxs-lookup"><span data-stu-id="9f001-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="9f001-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9f001-119">Details</span></span>  
  
|<span data-ttu-id="9f001-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9f001-120">Data Item Name</span></span>|<span data-ttu-id="9f001-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9f001-121">Data Item Type</span></span>|<span data-ttu-id="9f001-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f001-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9f001-123">Ad</span><span class="sxs-lookup"><span data-stu-id="9f001-123">Name</span></span>|`xs:string`|<span data-ttu-id="9f001-124">Kullanıcı tanımlı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="9f001-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="9f001-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="9f001-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="9f001-126">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f001-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9f001-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="9f001-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9f001-128">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="9f001-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9f001-129">Yükü</span><span class="sxs-lookup"><span data-stu-id="9f001-129">Payload</span></span>|`xs:string`|<span data-ttu-id="9f001-130">Kullanıcı tanımlı yükü olay.</span><span class="sxs-lookup"><span data-stu-id="9f001-130">The user-defined payload of the event.</span></span>|
