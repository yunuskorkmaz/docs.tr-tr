---
title: 211 - ParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: c0e21297-10b8-4456-a0e1-e019145cd5ac
ms.openlocfilehash: 7027b6557520a9ccb587f8d383d3598571da5838
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96279070"
---
# <a name="211---parameterinspectoraftercallinvoked"></a><span data-ttu-id="f472f-102">211 - ParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="f472f-102">211 - ParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="f472f-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="f472f-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f472f-104">ID</span><span class="sxs-lookup"><span data-stu-id="f472f-104">ID</span></span>|<span data-ttu-id="f472f-105">211</span><span class="sxs-lookup"><span data-stu-id="f472f-105">211</span></span>|  
|<span data-ttu-id="f472f-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="f472f-106">Keywords</span></span>|<span data-ttu-id="f472f-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f472f-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="f472f-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="f472f-108">Level</span></span>|<span data-ttu-id="f472f-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="f472f-109">Information</span></span>|  
|<span data-ttu-id="f472f-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="f472f-110">Channel</span></span>|<span data-ttu-id="f472f-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="f472f-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="f472f-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f472f-112">Description</span></span>  

 <span data-ttu-id="f472f-113">Bu olay, hizmet modeli bir üzerinde yöntemini çağırdıktan sonra yayınlanır `AfterCall` `ParameterInspector` .</span><span class="sxs-lookup"><span data-stu-id="f472f-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a `ParameterInspector`.</span></span>  
  
## <a name="message"></a><span data-ttu-id="f472f-114">İleti</span><span class="sxs-lookup"><span data-stu-id="f472f-114">Message</span></span>  

 <span data-ttu-id="f472f-115">Dağıtıcı, ' %1 ' türünde bir Parameterınspector üzerinde ' AfterCall ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="f472f-115">The Dispatcher invoked 'AfterCall' on a ParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="f472f-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="f472f-116">Details</span></span>  
  
|<span data-ttu-id="f472f-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="f472f-117">Data Item Name</span></span>|<span data-ttu-id="f472f-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="f472f-118">Data Item Type</span></span>|<span data-ttu-id="f472f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f472f-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="f472f-120">Tür adı</span><span class="sxs-lookup"><span data-stu-id="f472f-120">Type Name</span></span>|`xs:string`|<span data-ttu-id="f472f-121">Çağrılan türünün CLR FullName değeri `ParameterInspector` .</span><span class="sxs-lookup"><span data-stu-id="f472f-121">The CLR FullName of the type of the invoked `ParameterInspector`.</span></span>|  
|<span data-ttu-id="f472f-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="f472f-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="f472f-123">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f472f-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="f472f-124">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f472f-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="f472f-125">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="f472f-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="f472f-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="f472f-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="f472f-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="f472f-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
