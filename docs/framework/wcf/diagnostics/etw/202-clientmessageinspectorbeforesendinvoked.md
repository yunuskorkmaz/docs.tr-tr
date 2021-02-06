---
description: 'Hakkında daha fazla bilgi edinin: 202-Clientmessageınspectorbeforesendıned'
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: 0267304ba805c8f23109c820c8516a27958c3040
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645054"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="220bc-103">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="220bc-103">202 - ClientMessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="220bc-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="220bc-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="220bc-105">ID</span><span class="sxs-lookup"><span data-stu-id="220bc-105">ID</span></span>|<span data-ttu-id="220bc-106">202</span><span class="sxs-lookup"><span data-stu-id="220bc-106">202</span></span>|  
|<span data-ttu-id="220bc-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="220bc-107">Keywords</span></span>|<span data-ttu-id="220bc-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="220bc-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="220bc-109">Level</span><span class="sxs-lookup"><span data-stu-id="220bc-109">Level</span></span>|<span data-ttu-id="220bc-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="220bc-110">Information</span></span>|  
|<span data-ttu-id="220bc-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="220bc-111">Channel</span></span>|<span data-ttu-id="220bc-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="220bc-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="220bc-113">Description</span><span class="sxs-lookup"><span data-stu-id="220bc-113">Description</span></span>  

 <span data-ttu-id="220bc-114">Bu olay, hizmet modeli `BeforeSendRequest` bir istemci ileti denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="220bc-114">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="220bc-115">İleti</span><span class="sxs-lookup"><span data-stu-id="220bc-115">Message</span></span>  

 <span data-ttu-id="220bc-116">Dağıtıcı, ' %1 ' türünde bir Clientmessageınspector üzerinde ' BeforeSendRequest ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="220bc-116">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="220bc-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="220bc-117">Details</span></span>  
  
|<span data-ttu-id="220bc-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="220bc-118">Data Item Name</span></span>|<span data-ttu-id="220bc-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="220bc-119">Data Item Type</span></span>|<span data-ttu-id="220bc-120">Description</span><span class="sxs-lookup"><span data-stu-id="220bc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="220bc-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="220bc-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="220bc-122">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="220bc-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="220bc-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="220bc-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="220bc-124">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="220bc-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="220bc-125">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="220bc-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="220bc-126">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="220bc-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="220bc-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="220bc-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="220bc-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="220bc-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
