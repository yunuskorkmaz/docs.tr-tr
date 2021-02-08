---
description: 'Hakkında daha fazla bilgi edinin: 211-ParameterInspectorAfterCallInvoked'
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: 6168528fb001b5669e80595c8327dc57651e815e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794435"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="5f757-103">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="5f757-103">211 - ParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="5f757-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="5f757-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5f757-105">ID</span><span class="sxs-lookup"><span data-stu-id="5f757-105">ID</span></span>|<span data-ttu-id="5f757-106">211</span><span class="sxs-lookup"><span data-stu-id="5f757-106">211</span></span>|  
|<span data-ttu-id="5f757-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="5f757-107">Keywords</span></span>|<span data-ttu-id="5f757-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5f757-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="5f757-109">Level</span><span class="sxs-lookup"><span data-stu-id="5f757-109">Level</span></span>|<span data-ttu-id="5f757-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="5f757-110">Information</span></span>|  
|<span data-ttu-id="5f757-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="5f757-111">Channel</span></span>|<span data-ttu-id="5f757-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="5f757-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="5f757-113">Description</span><span class="sxs-lookup"><span data-stu-id="5f757-113">Description</span></span>  

 <span data-ttu-id="5f757-114">Bu olay, hizmet modeli bir üzerinde yöntemini çağırdıktan sonra yayınlanır `AfterCall` `ParameterInspector` .</span><span class="sxs-lookup"><span data-stu-id="5f757-114">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="5f757-115">İleti</span><span class="sxs-lookup"><span data-stu-id="5f757-115">Message</span></span>  

 <span data-ttu-id="5f757-116">Dağıtıcı, ' %1 ' türünde bir Parameterınspector üzerinde ' AfterCall ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="5f757-116">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="5f757-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5f757-117">Details</span></span>  
  
|<span data-ttu-id="5f757-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="5f757-118">Data Item Name</span></span>|<span data-ttu-id="5f757-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="5f757-119">Data Item Type</span></span>|<span data-ttu-id="5f757-120">Description</span><span class="sxs-lookup"><span data-stu-id="5f757-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="5f757-121">Tür adı</span><span class="sxs-lookup"><span data-stu-id="5f757-121">Type Name</span></span>|`xs:string`|<span data-ttu-id="5f757-122">Çağrılan türünün CLR FullName değeri `ParameterInspector` .</span><span class="sxs-lookup"><span data-stu-id="5f757-122">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="5f757-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="5f757-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="5f757-124">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5f757-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="5f757-125">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5f757-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="5f757-126">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="5f757-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="5f757-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="5f757-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="5f757-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="5f757-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
