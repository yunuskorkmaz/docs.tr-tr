---
description: 'Hakkında daha fazla bilgi edinin: 218-Clienentoperationcompleted'
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: 3719b77ce653c5177cf7b92901ecd51982504b83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794344"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="4bd75-103">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="4bd75-103">218 - ClientOperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="4bd75-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4bd75-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4bd75-105">ID</span><span class="sxs-lookup"><span data-stu-id="4bd75-105">ID</span></span>|<span data-ttu-id="4bd75-106">218</span><span class="sxs-lookup"><span data-stu-id="4bd75-106">218</span></span>|  
|<span data-ttu-id="4bd75-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4bd75-107">Keywords</span></span>|<span data-ttu-id="4bd75-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4bd75-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4bd75-109">Level</span><span class="sxs-lookup"><span data-stu-id="4bd75-109">Level</span></span>|<span data-ttu-id="4bd75-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="4bd75-110">Information</span></span>|  
|<span data-ttu-id="4bd75-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="4bd75-111">Channel</span></span>|<span data-ttu-id="4bd75-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="4bd75-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4bd75-113">Description</span><span class="sxs-lookup"><span data-stu-id="4bd75-113">Description</span></span>  

 <span data-ttu-id="4bd75-114">Bu olay, yalnızca bir işlem tamamlandıktan sonra istemciler tarafından yayılır.</span><span class="sxs-lookup"><span data-stu-id="4bd75-114">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="4bd75-115">Tek yönlü işlemlerde bu, ileti başarıyla gönderildikten hemen sonra olur.</span><span class="sxs-lookup"><span data-stu-id="4bd75-115">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="4bd75-116">İstek-yanıt işlemleri için, yanıt alındıktan sonra olur.</span><span class="sxs-lookup"><span data-stu-id="4bd75-116">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4bd75-117">İleti</span><span class="sxs-lookup"><span data-stu-id="4bd75-117">Message</span></span>  

 <span data-ttu-id="4bd75-118">Istemci, ' %2 ' sözleşmesiyle ilişkili ' %1 ' eylemini yürütmeyi tamamladı.</span><span class="sxs-lookup"><span data-stu-id="4bd75-118">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="4bd75-119">İleti, ' %3 ' öğesine gönderildi.</span><span class="sxs-lookup"><span data-stu-id="4bd75-119">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4bd75-120">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4bd75-120">Details</span></span>  
  
|<span data-ttu-id="4bd75-121">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4bd75-121">Data Item Name</span></span>|<span data-ttu-id="4bd75-122">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4bd75-122">Data Item Type</span></span>|<span data-ttu-id="4bd75-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bd75-123">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4bd75-124">Eylem</span><span class="sxs-lookup"><span data-stu-id="4bd75-124">Action</span></span>|<span data-ttu-id="4bd75-125">xs: String</span><span class="sxs-lookup"><span data-stu-id="4bd75-125">xs:string</span></span>|<span data-ttu-id="4bd75-126">Giden iletinin SOAP eylem üst bilgisi.</span><span class="sxs-lookup"><span data-stu-id="4bd75-126">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="4bd75-127">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="4bd75-127">Contract Name</span></span>|`xs:string`|<span data-ttu-id="4bd75-128">Sözleşmenin adı.</span><span class="sxs-lookup"><span data-stu-id="4bd75-128">The name of the contract.</span></span> <span data-ttu-id="4bd75-129">Örnek: Icalbir.</span><span class="sxs-lookup"><span data-stu-id="4bd75-129">Example: ICalculator.</span></span>|  
|<span data-ttu-id="4bd75-130">Hedef</span><span class="sxs-lookup"><span data-stu-id="4bd75-130">Destination</span></span>|`xs:string`|<span data-ttu-id="4bd75-131">İletinin gönderildiği hizmet uç noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="4bd75-131">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="4bd75-132">HostReference</span><span class="sxs-lookup"><span data-stu-id="4bd75-132">HostReference</span></span>|`xs:string`|<span data-ttu-id="4bd75-133">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4bd75-133">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4bd75-134">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4bd75-134">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4bd75-135">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="4bd75-135">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4bd75-136">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4bd75-136">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4bd75-137">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4bd75-137">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
