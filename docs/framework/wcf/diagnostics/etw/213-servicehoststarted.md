---
title: 213 - ServiceHostStarted
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f7facc-342f-46bb-9d52-a470178ba6bb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 61d79adce71be9ef93e9232e01a8cba5f5319f79
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="213---servicehoststarted"></a><span data-ttu-id="1fe70-102">213 - ServiceHostStarted</span><span class="sxs-lookup"><span data-stu-id="1fe70-102">213 - ServiceHostStarted</span></span>
## <a name="properties"></a><span data-ttu-id="1fe70-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="1fe70-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1fe70-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="1fe70-104">ID</span></span>|<span data-ttu-id="1fe70-105">213</span><span class="sxs-lookup"><span data-stu-id="1fe70-105">213</span></span>|  
|<span data-ttu-id="1fe70-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="1fe70-106">Keywords</span></span>|<span data-ttu-id="1fe70-107">Sorun giderme, ServiceHost EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="1fe70-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceHost</span></span>|  
|<span data-ttu-id="1fe70-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="1fe70-108">Level</span></span>|<span data-ttu-id="1fe70-109">LogAlways</span><span class="sxs-lookup"><span data-stu-id="1fe70-109">LogAlways</span></span>|  
|<span data-ttu-id="1fe70-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="1fe70-110">Channel</span></span>|<span data-ttu-id="1fe70-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="1fe70-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="1fe70-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fe70-112">Description</span></span>  
 <span data-ttu-id="1fe70-113">Bir Web barındırılan hizmeti ana bilgisayar başlatıldığında bu olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="1fe70-113">This event is emitted when a Web-hosted service host is started.</span></span> <span data-ttu-id="1fe70-114">Bu, genelde hizmet tarafından bir ileti etkinleştirildiğinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="1fe70-114">This typically happens when the service is activated by a message.</span></span> <span data-ttu-id="1fe70-115">Hizmet otomatik olarak başlatılacak şekilde yapılandırılmış olsa da oluşabilir.</span><span class="sxs-lookup"><span data-stu-id="1fe70-115">It may also happen if the service is configured to be automatically started.</span></span>  
  
## <a name="message"></a><span data-ttu-id="1fe70-116">İleti</span><span class="sxs-lookup"><span data-stu-id="1fe70-116">Message</span></span>  
 <span data-ttu-id="1fe70-117">ServiceHost başlatıldı: '%1'.</span><span class="sxs-lookup"><span data-stu-id="1fe70-117">ServiceHost started: '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="1fe70-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1fe70-118">Details</span></span>  
  
|<span data-ttu-id="1fe70-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="1fe70-119">Data Item Name</span></span>|<span data-ttu-id="1fe70-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="1fe70-120">Data Item Type</span></span>|<span data-ttu-id="1fe70-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1fe70-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="1fe70-122">Hizmet türü adı</span><span class="sxs-lookup"><span data-stu-id="1fe70-122">Service Type Name</span></span>|`xs:string`|<span data-ttu-id="1fe70-123">Hizmet uygulama türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="1fe70-123">The CLR FullName of the type of the service implementation.</span></span>|  
|<span data-ttu-id="1fe70-124">HostReference</span><span class="sxs-lookup"><span data-stu-id="1fe70-124">HostReference</span></span>|`xs:string`|<span data-ttu-id="1fe70-125">Bu alan, barındırılan Web Hizmetleri için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1fe70-125">For Web hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="1fe70-126">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="1fe70-126">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="1fe70-127">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="1fe70-127">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="1fe70-128">AppDomain</span><span class="sxs-lookup"><span data-stu-id="1fe70-128">AppDomain</span></span>|`xs:string`|<span data-ttu-id="1fe70-129">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="1fe70-129">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
