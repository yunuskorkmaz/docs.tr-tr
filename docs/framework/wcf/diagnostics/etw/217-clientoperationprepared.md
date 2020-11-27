---
title: 217 - ClientOperationPrepared
ms.date: 03/30/2017
ms.assetid: ad207f04-b038-4f33-95e9-27a361df8ecd
ms.openlocfilehash: e8aaf65bdff0718e932d07937e052541b7134f11
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278888"
---
# <a name="217---clientoperationprepared"></a><span data-ttu-id="d2bd7-102">217 - ClientOperationPrepared</span><span class="sxs-lookup"><span data-stu-id="d2bd7-102">217 - ClientOperationPrepared</span></span>

## <a name="properties"></a><span data-ttu-id="d2bd7-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d2bd7-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d2bd7-104">ID</span><span class="sxs-lookup"><span data-stu-id="d2bd7-104">ID</span></span>|<span data-ttu-id="d2bd7-105">217</span><span class="sxs-lookup"><span data-stu-id="d2bd7-105">217</span></span>|  
|<span data-ttu-id="d2bd7-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="d2bd7-106">Keywords</span></span>|<span data-ttu-id="d2bd7-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d2bd7-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d2bd7-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d2bd7-108">Level</span></span>|<span data-ttu-id="d2bd7-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="d2bd7-109">Information</span></span>|  
|<span data-ttu-id="d2bd7-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d2bd7-110">Channel</span></span>|<span data-ttu-id="d2bd7-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="d2bd7-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d2bd7-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2bd7-112">Description</span></span>  

 <span data-ttu-id="d2bd7-113">Bu olay, yalnızca bir işlem hizmete gönderilmeden önce istemciler tarafından yayılır.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-113">This event is emitted by clients just before an operation is sent to the service.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d2bd7-114">İleti</span><span class="sxs-lookup"><span data-stu-id="d2bd7-114">Message</span></span>  

 <span data-ttu-id="d2bd7-115">Istemci, ' %2 ' sözleşmesiyle ilişkili ' %1 ' eylemini yürütüyor.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-115">The Client is executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="d2bd7-116">İleti, ' %3 ' öğesine gönderilecek.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-116">The message will be sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d2bd7-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d2bd7-117">Details</span></span>  
  
|<span data-ttu-id="d2bd7-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d2bd7-118">Data Item Name</span></span>|<span data-ttu-id="d2bd7-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d2bd7-119">Data Item Type</span></span>|<span data-ttu-id="d2bd7-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2bd7-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d2bd7-121">Eylem</span><span class="sxs-lookup"><span data-stu-id="d2bd7-121">Action</span></span>|`xs:string`|<span data-ttu-id="d2bd7-122">Giden iletinin SOAP eylem üst bilgisi.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-122">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="d2bd7-123">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="d2bd7-123">Contract Name</span></span>|`xs:string`|<span data-ttu-id="d2bd7-124">Sözleşmenin adı.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-124">The name of the contract.</span></span> <span data-ttu-id="d2bd7-125">Örnek: Icalbir.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-125">Example: ICalculator.</span></span>|  
|<span data-ttu-id="d2bd7-126">Hedef</span><span class="sxs-lookup"><span data-stu-id="d2bd7-126">Destination</span></span>|`xs:string`|<span data-ttu-id="d2bd7-127">İletinin gönderildiği hizmet uç noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-127">The address of the service endpoint that the message is sent to.</span></span>|  
|<span data-ttu-id="d2bd7-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="d2bd7-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="d2bd7-129">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d2bd7-130">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d2bd7-131">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d2bd7-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d2bd7-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d2bd7-133">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d2bd7-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
