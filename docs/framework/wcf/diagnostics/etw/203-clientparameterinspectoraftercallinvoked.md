---
title: 203 - ClientParameterInspectorAfterCallInvoked
ms.date: 03/30/2017
ms.assetid: b9592212-07e2-43e0-8b00-affd195cf55a
ms.openlocfilehash: b964c26c9684cedef0fbe427bfd9ad232d199f12
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251535"
---
# <a name="203---clientparameterinspectoraftercallinvoked"></a><span data-ttu-id="d3a94-102">203 - ClientParameterInspectorAfterCallInvoked</span><span class="sxs-lookup"><span data-stu-id="d3a94-102">203 - ClientParameterInspectorAfterCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="d3a94-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="d3a94-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d3a94-104">ID</span><span class="sxs-lookup"><span data-stu-id="d3a94-104">ID</span></span>|<span data-ttu-id="d3a94-105">203</span><span class="sxs-lookup"><span data-stu-id="d3a94-105">203</span></span>|  
|<span data-ttu-id="d3a94-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="d3a94-106">Keywords</span></span>|<span data-ttu-id="d3a94-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d3a94-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="d3a94-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="d3a94-108">Level</span></span>|<span data-ttu-id="d3a94-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="d3a94-109">Information</span></span>|  
|<span data-ttu-id="d3a94-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="d3a94-110">Channel</span></span>|<span data-ttu-id="d3a94-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="d3a94-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="d3a94-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3a94-112">Description</span></span>  

 <span data-ttu-id="d3a94-113">Bu olay, hizmet modeli `AfterCall` bir istemci parametresi denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="d3a94-113">This event is emitted after the Service Model has invoked the `AfterCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="d3a94-114">İleti</span><span class="sxs-lookup"><span data-stu-id="d3a94-114">Message</span></span>  

 <span data-ttu-id="d3a94-115">Dağıtıcı, ' %1 ' türünde bir Clientparameterınspector üzerinde ' AfterCall ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="d3a94-115">The Dispatcher invoked 'AfterCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="d3a94-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="d3a94-116">Details</span></span>  
  
|<span data-ttu-id="d3a94-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="d3a94-117">Data Item Name</span></span>|<span data-ttu-id="d3a94-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="d3a94-118">Data Item Type</span></span>|<span data-ttu-id="d3a94-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3a94-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="d3a94-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="d3a94-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="d3a94-121">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="d3a94-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="d3a94-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="d3a94-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="d3a94-123">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d3a94-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="d3a94-124">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="d3a94-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="d3a94-125">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="d3a94-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="d3a94-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="d3a94-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="d3a94-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="d3a94-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
