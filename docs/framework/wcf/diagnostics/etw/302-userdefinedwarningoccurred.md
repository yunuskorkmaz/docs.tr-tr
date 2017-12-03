---
title: 302 - UserDefinedWarningOccurred
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d1f0bf1-0151-45e6-be92-573d397b54de
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61ec1e341d5220000b928409e006553c71ab379a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="302---userdefinedwarningoccurred"></a><span data-ttu-id="a973f-102">302 - UserDefinedWarningOccurred</span><span class="sxs-lookup"><span data-stu-id="a973f-102">302 - UserDefinedWarningOccurred</span></span>
## <a name="properties"></a><span data-ttu-id="a973f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="a973f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a973f-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="a973f-104">ID</span></span>|<span data-ttu-id="a973f-105">302</span><span class="sxs-lookup"><span data-stu-id="a973f-105">302</span></span>|  
|<span data-ttu-id="a973f-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="a973f-106">Keywords</span></span>|<span data-ttu-id="a973f-107">Sorun giderme, ögesi, UserEvents, ServiceModel, EndToEndMonitoring</span><span class="sxs-lookup"><span data-stu-id="a973f-107">Troubleshooting, HealthMonitoring, UserEvents, ServiceModel, EndToEndMonitoring</span></span>|  
|<span data-ttu-id="a973f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="a973f-108">Level</span></span>|<span data-ttu-id="a973f-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="a973f-109">Warning</span></span>|  
|<span data-ttu-id="a973f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="a973f-110">Channel</span></span>|<span data-ttu-id="a973f-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="a973f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="a973f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a973f-112">Description</span></span>  
 <span data-ttu-id="a973f-113">Bu olay, kullanıcı kodundan yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="a973f-113">This event is emitted from user code.</span></span> <span data-ttu-id="a973f-114">Geliştiriciler kendi hizmetinde özel tanımlanmış uyarı olayı meydana geldiğinde bu olay yayma.</span><span class="sxs-lookup"><span data-stu-id="a973f-114">Developers can emit this event when a custom-defined warning event occurs in their service.</span></span> <span data-ttu-id="a973f-115">Bu yapılabilir kullanarak <xref:System.Diagnostics.Eventing> API'leri.</span><span class="sxs-lookup"><span data-stu-id="a973f-115">This can be done using the <xref:System.Diagnostics.Eventing> APIs.</span></span> <span data-ttu-id="a973f-116">Ayrıca, bu API sarmalar ve bu olay düzgün bir şekilde yayma yapmayı gösteren bir WCF örneği yoktur.</span><span class="sxs-lookup"><span data-stu-id="a973f-116">Additionally, there is a WCF sample that wraps that API and demonstrates how to properly emit this event.</span></span>  
  
## <a name="message"></a><span data-ttu-id="a973f-117">İleti</span><span class="sxs-lookup"><span data-stu-id="a973f-117">Message</span></span>  
 <span data-ttu-id="a973f-118">Ad: '%1', başvuru: '%2', yük: % 3</span><span class="sxs-lookup"><span data-stu-id="a973f-118">Name:'%1', Reference:'%2', Payload:%3</span></span>  
  
## <a name="details"></a><span data-ttu-id="a973f-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="a973f-119">Details</span></span>  
  
|<span data-ttu-id="a973f-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="a973f-120">Data Item Name</span></span>|<span data-ttu-id="a973f-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="a973f-121">Data Item Type</span></span>|<span data-ttu-id="a973f-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a973f-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="a973f-123">Ad</span><span class="sxs-lookup"><span data-stu-id="a973f-123">Name</span></span>|`xs:string`|<span data-ttu-id="a973f-124">Kullanıcı tanımlı olayın adı.</span><span class="sxs-lookup"><span data-stu-id="a973f-124">The user-defined name of the event.</span></span>|  
|<span data-ttu-id="a973f-125">HostReference</span><span class="sxs-lookup"><span data-stu-id="a973f-125">HostReference</span></span>|`xs:string`|<span data-ttu-id="a973f-126">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="a973f-126">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="a973f-127">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="a973f-127">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="a973f-128">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="a973f-128">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="a973f-129">Yükü</span><span class="sxs-lookup"><span data-stu-id="a973f-129">Payload</span></span>|`xs:string`|<span data-ttu-id="a973f-130">Kullanıcı tanımlı yükü olay.</span><span class="sxs-lookup"><span data-stu-id="a973f-130">The user-defined payload of the event.</span></span>|
