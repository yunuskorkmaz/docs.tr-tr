---
title: 218 - ClientOperationCompleted
ms.date: 03/30/2017
ms.assetid: b069bced-7bb2-4e01-8227-e5dbda17af09
ms.openlocfilehash: d74aa77aff7b45b50f6891c999889011d9e03381
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96278862"
---
# <a name="218---clientoperationcompleted"></a><span data-ttu-id="ac9d4-102">218 - ClientOperationCompleted</span><span class="sxs-lookup"><span data-stu-id="ac9d4-102">218 - ClientOperationCompleted</span></span>

## <a name="properties"></a><span data-ttu-id="ac9d4-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="ac9d4-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ac9d4-104">ID</span><span class="sxs-lookup"><span data-stu-id="ac9d4-104">ID</span></span>|<span data-ttu-id="ac9d4-105">218</span><span class="sxs-lookup"><span data-stu-id="ac9d4-105">218</span></span>|  
|<span data-ttu-id="ac9d4-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="ac9d4-106">Keywords</span></span>|<span data-ttu-id="ac9d4-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ac9d4-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="ac9d4-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="ac9d4-108">Level</span></span>|<span data-ttu-id="ac9d4-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="ac9d4-109">Information</span></span>|  
|<span data-ttu-id="ac9d4-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="ac9d4-110">Channel</span></span>|<span data-ttu-id="ac9d4-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="ac9d4-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="ac9d4-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac9d4-112">Description</span></span>  

 <span data-ttu-id="ac9d4-113">Bu olay, yalnızca bir işlem tamamlandıktan sonra istemciler tarafından yayılır.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-113">This event is emitted by clients just after an operation completes.</span></span> <span data-ttu-id="ac9d4-114">Tek yönlü işlemlerde bu, ileti başarıyla gönderildikten hemen sonra olur.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-114">For one-way operations, this is just after the message is sent successfully.</span></span> <span data-ttu-id="ac9d4-115">İstek-yanıt işlemleri için, yanıt alındıktan sonra olur.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-115">For request-response operations this is after the response is received.</span></span>  
  
## <a name="message"></a><span data-ttu-id="ac9d4-116">İleti</span><span class="sxs-lookup"><span data-stu-id="ac9d4-116">Message</span></span>  

 <span data-ttu-id="ac9d4-117">Istemci, ' %2 ' sözleşmesiyle ilişkili ' %1 ' eylemini yürütmeyi tamamladı.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-117">The Client completed executing Action '%1' associated with the '%2' contract.</span></span> <span data-ttu-id="ac9d4-118">İleti, ' %3 ' öğesine gönderildi.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-118">The message was sent to '%3'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="ac9d4-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="ac9d4-119">Details</span></span>  
  
|<span data-ttu-id="ac9d4-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="ac9d4-120">Data Item Name</span></span>|<span data-ttu-id="ac9d4-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="ac9d4-121">Data Item Type</span></span>|<span data-ttu-id="ac9d4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ac9d4-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="ac9d4-123">Eylem</span><span class="sxs-lookup"><span data-stu-id="ac9d4-123">Action</span></span>|<span data-ttu-id="ac9d4-124">xs: String</span><span class="sxs-lookup"><span data-stu-id="ac9d4-124">xs:string</span></span>|<span data-ttu-id="ac9d4-125">Giden iletinin SOAP eylem üst bilgisi.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-125">The SOAP action header of the outgoing message.</span></span>|  
|<span data-ttu-id="ac9d4-126">Sözleşme adı</span><span class="sxs-lookup"><span data-stu-id="ac9d4-126">Contract Name</span></span>|`xs:string`|<span data-ttu-id="ac9d4-127">Sözleşmenin adı.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-127">The name of the contract.</span></span> <span data-ttu-id="ac9d4-128">Örnek: Icalbir.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-128">Example: ICalculator.</span></span>|  
|<span data-ttu-id="ac9d4-129">Hedef</span><span class="sxs-lookup"><span data-stu-id="ac9d4-129">Destination</span></span>|`xs:string`|<span data-ttu-id="ac9d4-130">İletinin gönderildiği hizmet uç noktasının adresi.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-130">The address of the service endpoint that the message was sent to.</span></span>|  
|<span data-ttu-id="ac9d4-131">HostReference</span><span class="sxs-lookup"><span data-stu-id="ac9d4-131">HostReference</span></span>|`xs:string`|<span data-ttu-id="ac9d4-132">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-132">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="ac9d4-133">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-133">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="ac9d4-134">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-134">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="ac9d4-135">AppDomain</span><span class="sxs-lookup"><span data-stu-id="ac9d4-135">AppDomain</span></span>|`xs:string`|<span data-ttu-id="ac9d4-136">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="ac9d4-136">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
