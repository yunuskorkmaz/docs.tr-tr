---
title: 217 - ClientOperationPrepared
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3e1b4e3aab6a6a7f94bfb3783c9e32f83557db19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="9f53b-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="9f53b-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="9f53b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="9f53b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9f53b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="9f53b-104">ID</span></span>|<span data-ttu-id="9f53b-105">217</span><span class="sxs-lookup"><span data-stu-id="9f53b-105">217</span></span>|  
|<span data-ttu-id="9f53b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="9f53b-106">Keywords</span></span>|<span data-ttu-id="9f53b-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9f53b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="9f53b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="9f53b-108">Level</span></span>|<span data-ttu-id="9f53b-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9f53b-109">Information</span></span>|  
|<span data-ttu-id="9f53b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="9f53b-110">Channel</span></span>|<span data-ttu-id="9f53b-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="9f53b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="9f53b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f53b-112">Description</span></span>  
 <span data-ttu-id="9f53b-113">Bu olay yalnızca bir işlem hizmetine gönderilmeden önce istemcileri tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="9f53b-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="9f53b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="9f53b-114">Message</span></span>  
 <span data-ttu-id="9f53b-115">İstemci, '%2' sözleşmeyle ilişkilendirilmiş ' %1' eylemi yürütüyor.</span><span class="sxs-lookup"><span data-stu-id="9f53b-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="9f53b-116">'%3' ileti gönderilir.</span><span class="sxs-lookup"><span data-stu-id="9f53b-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="9f53b-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="9f53b-117">Details</span></span>  
  
|<span data-ttu-id="9f53b-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="9f53b-118">Data Item Name</span></span>|<span data-ttu-id="9f53b-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="9f53b-119">Data Item Type</span></span>|<span data-ttu-id="9f53b-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9f53b-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="9f53b-121">Eylem</span><span class="sxs-lookup"><span data-stu-id="9f53b-121">Action</span></span>|`xs:string`|<span data-ttu-id="9f53b-122">Giden iletinin SOAP eylemi üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="9f53b-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="9f53b-123">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="9f53b-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="9f53b-124">Anlaşma adı.</span><span class="sxs-lookup"><span data-stu-id="9f53b-124">The name of the contract.</span></span> <span data-ttu-id="9f53b-125">Örnek: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="9f53b-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="9f53b-126">Hedef</span><span class="sxs-lookup"><span data-stu-id="9f53b-126">Destination</span></span>|`xs:string`|<span data-ttu-id="9f53b-127">İleti gönderilir hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="9f53b-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="9f53b-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="9f53b-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="9f53b-129">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9f53b-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="9f53b-130">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="9f53b-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="9f53b-131">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="9f53b-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="9f53b-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="9f53b-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="9f53b-133">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="9f53b-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
