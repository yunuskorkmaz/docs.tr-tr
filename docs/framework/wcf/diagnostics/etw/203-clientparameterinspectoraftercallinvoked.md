---
description: 'Hakkında daha fazla bilgi edinin: 203-ClientParameterInspectorAfterCallInvoked'
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: bacdc2a74fc2cef6d7e473fa58c0cbbcffffcf16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645028"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="aacfc-103">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="aacfc-103">203 - ClientParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="aacfc-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="aacfc-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aacfc-105">ID</span><span class="sxs-lookup"><span data-stu-id="aacfc-105">ID</span></span>|<span data-ttu-id="aacfc-106">203</span><span class="sxs-lookup"><span data-stu-id="aacfc-106">203</span></span>|  
|<span data-ttu-id="aacfc-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="aacfc-107">Keywords</span></span>|<span data-ttu-id="aacfc-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="aacfc-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="aacfc-109">Level</span><span class="sxs-lookup"><span data-stu-id="aacfc-109">Level</span></span>|<span data-ttu-id="aacfc-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="aacfc-110">Information</span></span>|  
|<span data-ttu-id="aacfc-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="aacfc-111">Channel</span></span>|<span data-ttu-id="aacfc-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="aacfc-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="aacfc-113">Description</span><span class="sxs-lookup"><span data-stu-id="aacfc-113">Description</span></span>  

 <span data-ttu-id="aacfc-114">Bu olay, hizmet modeli `AfterCall` bir istemci parametresi denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="aacfc-114">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="aacfc-115">İleti</span><span class="sxs-lookup"><span data-stu-id="aacfc-115">Message</span></span>  

 <span data-ttu-id="aacfc-116">Dağıtıcı, ' %1 ' türünde bir Clientparameterınspector üzerinde ' AfterCall ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="aacfc-116">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="aacfc-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="aacfc-117">Details</span></span>  
  
|<span data-ttu-id="aacfc-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="aacfc-118">Data Item Name</span></span>|<span data-ttu-id="aacfc-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="aacfc-119">Data Item Type</span></span>|<span data-ttu-id="aacfc-120">Description</span><span class="sxs-lookup"><span data-stu-id="aacfc-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="aacfc-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="aacfc-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="aacfc-122">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="aacfc-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="aacfc-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="aacfc-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="aacfc-124">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="aacfc-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="aacfc-125">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="aacfc-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="aacfc-126">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="aacfc-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="aacfc-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="aacfc-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="aacfc-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="aacfc-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
