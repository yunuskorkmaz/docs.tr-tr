---
description: 'Hakkında daha fazla bilgi edinin: 219-ServiceException'
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: b2ac12d6c5c68517b085b39dd7d0f81c39db9ebd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794331"
---
# <a name="219---serviceexception"></a><span data-ttu-id="957f5-103">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="957f5-103">219 - ServiceException</span></span>

## <a name="properties"></a><span data-ttu-id="957f5-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="957f5-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="957f5-105">ID</span><span class="sxs-lookup"><span data-stu-id="957f5-105">ID</span></span>|<span data-ttu-id="957f5-106">219</span><span class="sxs-lookup"><span data-stu-id="957f5-106">219</span></span>|  
|<span data-ttu-id="957f5-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="957f5-107">Keywords</span></span>|<span data-ttu-id="957f5-108">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="957f5-108">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="957f5-109">Level</span><span class="sxs-lookup"><span data-stu-id="957f5-109">Level</span></span>|<span data-ttu-id="957f5-110">Hata</span><span class="sxs-lookup"><span data-stu-id="957f5-110">Error</span></span>|  
|<span data-ttu-id="957f5-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="957f5-111">Channel</span></span>|<span data-ttu-id="957f5-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="957f5-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="957f5-113">Description</span><span class="sxs-lookup"><span data-stu-id="957f5-113">Description</span></span>  

 <span data-ttu-id="957f5-114">Bu olay, bir WCF hizmeti işlenmeyen bir özel durumla karşılaştığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="957f5-114">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="957f5-115">Bu, etkinleştirme sırasında, ileti işleme sırasında ve Kullanıcı kodunda işlenmeyen özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="957f5-115">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="957f5-116">İleti</span><span class="sxs-lookup"><span data-stu-id="957f5-116">Message</span></span>  

 <span data-ttu-id="957f5-117">İleti işleme sırasında ' %2 ' türünde işlenmeyen bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="957f5-117">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="957f5-118">Tam özel durum ToString: %1.</span><span class="sxs-lookup"><span data-stu-id="957f5-118">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="957f5-119">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="957f5-119">Details</span></span>  
  
|<span data-ttu-id="957f5-120">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="957f5-120">Data Item Name</span></span>|<span data-ttu-id="957f5-121">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="957f5-121">Data Item Type</span></span>|<span data-ttu-id="957f5-122">Description</span><span class="sxs-lookup"><span data-stu-id="957f5-122">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="957f5-123">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="957f5-123">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="957f5-124">`ToString`Clr özel durumuyla () çağırmanın sonucu.</span><span class="sxs-lookup"><span data-stu-id="957f5-124">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="957f5-125">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="957f5-125">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="957f5-126">Özel durum türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="957f5-126">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="957f5-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="957f5-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="957f5-128">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="957f5-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="957f5-129">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="957f5-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="957f5-130">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="957f5-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="957f5-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="957f5-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="957f5-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="957f5-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
