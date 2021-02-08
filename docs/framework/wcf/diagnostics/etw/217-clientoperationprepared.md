---
description: 'Hakkında daha fazla bilgi edinin: 217-Clientoperationhazırlandı'
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: eab6a9a654e6e48a8831f238cdf3a3bf7a9f62d2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794357"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="8f00b-103">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="8f00b-103">217 - ClientOperationPrepared</span></span>

## <a name="properties"></a><span data-ttu-id="8f00b-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="8f00b-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8f00b-105">ID</span><span class="sxs-lookup"><span data-stu-id="8f00b-105">ID</span></span>|<span data-ttu-id="8f00b-106">217</span><span class="sxs-lookup"><span data-stu-id="8f00b-106">217</span></span>|  
|<span data-ttu-id="8f00b-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="8f00b-107">Keywords</span></span>|<span data-ttu-id="8f00b-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8f00b-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="8f00b-109">Level</span><span class="sxs-lookup"><span data-stu-id="8f00b-109">Level</span></span>|<span data-ttu-id="8f00b-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="8f00b-110">Information</span></span>|  
|<span data-ttu-id="8f00b-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="8f00b-111">Channel</span></span>|<span data-ttu-id="8f00b-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="8f00b-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="8f00b-113">Description</span><span class="sxs-lookup"><span data-stu-id="8f00b-113">Description</span></span>  

 <span data-ttu-id="8f00b-114">Bu olay, yalnızca bir işlem hizmete gönderilmeden önce istemciler tarafından yayılır.</span><span class="sxs-lookup"><span data-stu-id="8f00b-114">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="8f00b-115">İleti</span><span class="sxs-lookup"><span data-stu-id="8f00b-115">Message</span></span>  

 <span data-ttu-id="8f00b-116">Istemci, ' %2 ' sözleşmesiyle ilişkili ' %1 ' eylemini yürütüyor.</span><span class="sxs-lookup"><span data-stu-id="8f00b-116">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="8f00b-117">İleti, ' %3 ' öğesine gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="8f00b-117">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="8f00b-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="8f00b-118">Details</span></span>  
  
|<span data-ttu-id="8f00b-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="8f00b-119">Data Item Name</span></span>|<span data-ttu-id="8f00b-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="8f00b-120">Data Item Type</span></span>|<span data-ttu-id="8f00b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f00b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="8f00b-122">Eylem</span><span class="sxs-lookup"><span data-stu-id="8f00b-122">Action</span></span>|`xs:string`|<span data-ttu-id="8f00b-123">Giden iletinin SOAP eylem üst bilgisi.</span><span class="sxs-lookup"><span data-stu-id="8f00b-123">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="8f00b-124">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="8f00b-124">Contract Name</span></span>|`xs:string`|<span data-ttu-id="8f00b-125">Sözleşmenin adı.</span><span class="sxs-lookup"><span data-stu-id="8f00b-125">The name of the contract.</span></span> <span data-ttu-id="8f00b-126">Örnek: Icalbir.</span><span class="sxs-lookup"><span data-stu-id="8f00b-126">Example: ICalculator.</span></span>|  
|<span data-ttu-id="8f00b-127">Hedef</span><span class="sxs-lookup"><span data-stu-id="8f00b-127">Destination</span></span>|`xs:string`|<span data-ttu-id="8f00b-128">İletinin gönderildiği hizmet uç noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="8f00b-128">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="8f00b-129">HostReference</span><span class="sxs-lookup"><span data-stu-id="8f00b-129">HostReference</span></span>|`xs:string`|<span data-ttu-id="8f00b-130">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="8f00b-130">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="8f00b-131">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8f00b-131">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="8f00b-132">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="8f00b-132">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="8f00b-133">AppDomain</span><span class="sxs-lookup"><span data-stu-id="8f00b-133">AppDomain</span></span>|`xs:string`|<span data-ttu-id="8f00b-134">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="8f00b-134">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
