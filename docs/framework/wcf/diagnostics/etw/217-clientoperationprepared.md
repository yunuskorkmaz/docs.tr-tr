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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5062d2c2146dae8b22165cfbea0c6a78241d17b8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="ff41d-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="ff41d-102">217 - ClientOperationPrepared</span></span>
## <a name="properties"></a><span data-ttu-id="ff41d-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ff41d-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ff41d-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="ff41d-104">ID</span></span>|<span data-ttu-id="ff41d-105">217</span><span class="sxs-lookup"><span data-stu-id="ff41d-105">217</span></span>|  
|<span data-ttu-id="ff41d-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="ff41d-106">Keywords</span></span>|<span data-ttu-id="ff41d-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ff41d-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ff41d-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ff41d-108">Level</span></span>|<span data-ttu-id="ff41d-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="ff41d-109">Information</span></span>|  
|<span data-ttu-id="ff41d-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ff41d-110">Channel</span></span>|<span data-ttu-id="ff41d-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ff41d-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ff41d-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff41d-112">Description</span></span>  
 <span data-ttu-id="ff41d-113">Bu olay yalnızca bir işlem hizmetine gönderilmeden önce istemcileri tarafından yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="ff41d-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ff41d-114">İleti</span><span class="sxs-lookup"><span data-stu-id="ff41d-114">Message</span></span>  
 <span data-ttu-id="ff41d-115">İstemci, '%2' sözleşmeyle ilişkilendirilmiş ' %1' eylemi yürütüyor.</span><span class="sxs-lookup"><span data-stu-id="ff41d-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="ff41d-116">'%3' ileti gönderilir.</span><span class="sxs-lookup"><span data-stu-id="ff41d-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ff41d-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ff41d-117">Details</span></span>  
  
|<span data-ttu-id="ff41d-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ff41d-118">Data Item Name</span></span>|<span data-ttu-id="ff41d-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ff41d-119">Data Item Type</span></span>|<span data-ttu-id="ff41d-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff41d-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ff41d-121">Eylem</span><span class="sxs-lookup"><span data-stu-id="ff41d-121">Action</span></span>|`xs:string`|<span data-ttu-id="ff41d-122">Giden iletinin SOAP eylemi üstbilgisi.</span><span class="sxs-lookup"><span data-stu-id="ff41d-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="ff41d-123">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="ff41d-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="ff41d-124">Anlaşma adı.</span><span class="sxs-lookup"><span data-stu-id="ff41d-124">The name of the contract.</span></span> <span data-ttu-id="ff41d-125">Örnek: ICalculator.</span><span class="sxs-lookup"><span data-stu-id="ff41d-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="ff41d-126">Hedef</span><span class="sxs-lookup"><span data-stu-id="ff41d-126">Destination</span></span>|`xs:string`|<span data-ttu-id="ff41d-127">İleti gönderilir hizmet uç noktası adresi.</span><span class="sxs-lookup"><span data-stu-id="ff41d-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="ff41d-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="ff41d-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="ff41d-129">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ff41d-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ff41d-130">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="ff41d-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ff41d-131">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="ff41d-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ff41d-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ff41d-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ff41d-133">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ff41d-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
