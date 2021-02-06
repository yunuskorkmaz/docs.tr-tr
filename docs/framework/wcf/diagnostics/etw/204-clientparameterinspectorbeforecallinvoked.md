---
description: 'Hakkında daha fazla bilgi edinin: 204-Clientparameterınspectorbefoyeniden hesaplama Linvoked'
title: 204 - ClientParameterInspectorBeforeCallInvoked
ms.date: 03/30/2017
ms.assetid: 8253555a-9002-4565-8ede-33d7a33a895f
ms.openlocfilehash: fa5646da7c48f624dc40f4fcc54a890c0758b4ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645002"
---
# <a name="204---clientparameterinspectorbeforecallinvoked"></a><span data-ttu-id="08252-103">204 - ClientParameterInspectorBeforeCallInvoked</span><span class="sxs-lookup"><span data-stu-id="08252-103">204 - ClientParameterInspectorBeforeCallInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="08252-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="08252-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="08252-105">ID</span><span class="sxs-lookup"><span data-stu-id="08252-105">ID</span></span>|<span data-ttu-id="08252-106">204</span><span class="sxs-lookup"><span data-stu-id="08252-106">204</span></span>|  
|<span data-ttu-id="08252-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="08252-107">Keywords</span></span>|<span data-ttu-id="08252-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="08252-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="08252-109">Level</span><span class="sxs-lookup"><span data-stu-id="08252-109">Level</span></span>|<span data-ttu-id="08252-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="08252-110">Information</span></span>|  
|<span data-ttu-id="08252-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="08252-111">Channel</span></span>|<span data-ttu-id="08252-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="08252-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="08252-113">Description</span><span class="sxs-lookup"><span data-stu-id="08252-113">Description</span></span>  

 <span data-ttu-id="08252-114">Bu olay, hizmet modeli `BeforeCall` bir istemci parametresi denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="08252-114">This event is emitted after the Service Model has invoked the `BeforeCall` method on a client parameter inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="08252-115">İleti</span><span class="sxs-lookup"><span data-stu-id="08252-115">Message</span></span>  

 <span data-ttu-id="08252-116">Dağıtıcı, ' %1 ' türünde bir Clientparameterınspector üzerinde ' Befohatırla ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="08252-116">The Dispatcher invoked 'BeforeCall' on a ClientParameterInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="08252-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="08252-117">Details</span></span>  
  
|<span data-ttu-id="08252-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="08252-118">Data Item Name</span></span>|<span data-ttu-id="08252-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="08252-119">Data Item Type</span></span>|<span data-ttu-id="08252-120">Description</span><span class="sxs-lookup"><span data-stu-id="08252-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="08252-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="08252-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="08252-122">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="08252-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="08252-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="08252-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="08252-124">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="08252-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="08252-125">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="08252-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="08252-126">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="08252-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="08252-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="08252-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="08252-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="08252-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
