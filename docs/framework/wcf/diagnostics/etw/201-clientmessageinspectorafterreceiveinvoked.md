---
description: 'Hakkında daha fazla bilgi edinin: 201-ClientMessageInspectorAfterReceiveInvoked'
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: 511f8bd039219d031c311f7def7b360b74df1a0a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99645158"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="3ebf6-103">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="3ebf6-103">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="3ebf6-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3ebf6-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3ebf6-105">ID</span><span class="sxs-lookup"><span data-stu-id="3ebf6-105">ID</span></span>|<span data-ttu-id="3ebf6-106">201</span><span class="sxs-lookup"><span data-stu-id="3ebf6-106">201</span></span>|  
|<span data-ttu-id="3ebf6-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="3ebf6-107">Keywords</span></span>|<span data-ttu-id="3ebf6-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3ebf6-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3ebf6-109">Level</span><span class="sxs-lookup"><span data-stu-id="3ebf6-109">Level</span></span>|<span data-ttu-id="3ebf6-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="3ebf6-110">Information</span></span>|  
|<span data-ttu-id="3ebf6-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="3ebf6-111">Channel</span></span>|<span data-ttu-id="3ebf6-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="3ebf6-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3ebf6-113">Description</span><span class="sxs-lookup"><span data-stu-id="3ebf6-113">Description</span></span>  

 <span data-ttu-id="3ebf6-114">Bu olay, hizmet modeli `AfterReceiveReply` bir istemci ileti denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="3ebf6-114">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3ebf6-115">İleti</span><span class="sxs-lookup"><span data-stu-id="3ebf6-115">Message</span></span>  

 <span data-ttu-id="3ebf6-116">Dağıtıcı, ' %1 ' türünde bir Clientmessageınspector üzerinde ' AfterReceiveReply ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="3ebf6-116">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3ebf6-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3ebf6-117">Details</span></span>  
  
|<span data-ttu-id="3ebf6-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="3ebf6-118">Data Item Name</span></span>|<span data-ttu-id="3ebf6-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="3ebf6-119">Data Item Type</span></span>|<span data-ttu-id="3ebf6-120">Description</span><span class="sxs-lookup"><span data-stu-id="3ebf6-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3ebf6-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="3ebf6-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="3ebf6-122">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="3ebf6-122">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="3ebf6-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="3ebf6-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="3ebf6-124">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3ebf6-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3ebf6-125">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3ebf6-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3ebf6-126">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="3ebf6-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3ebf6-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3ebf6-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3ebf6-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="3ebf6-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
