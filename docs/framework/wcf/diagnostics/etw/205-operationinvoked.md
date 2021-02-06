---
description: 'Hakkında daha fazla bilgi edinin: 205-Operationçağrılan'
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: 09afe4c29c5f56b06bbf524dd13d88ddf2319063
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99644976"
---
# <a name="205---operationinvoked"></a><span data-ttu-id="3e2fe-103">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="3e2fe-103">205 - OperationInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="3e2fe-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3e2fe-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3e2fe-105">ID</span><span class="sxs-lookup"><span data-stu-id="3e2fe-105">ID</span></span>|<span data-ttu-id="3e2fe-106">205</span><span class="sxs-lookup"><span data-stu-id="3e2fe-106">205</span></span>|  
|<span data-ttu-id="3e2fe-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="3e2fe-107">Keywords</span></span>|<span data-ttu-id="3e2fe-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3e2fe-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="3e2fe-109">Level</span><span class="sxs-lookup"><span data-stu-id="3e2fe-109">Level</span></span>|<span data-ttu-id="3e2fe-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="3e2fe-110">Information</span></span>|  
|<span data-ttu-id="3e2fe-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="3e2fe-111">Channel</span></span>|<span data-ttu-id="3e2fe-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="3e2fe-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="3e2fe-113">Description</span><span class="sxs-lookup"><span data-stu-id="3e2fe-113">Description</span></span>  

 <span data-ttu-id="3e2fe-114">Bu olay, hizmet modeli varsayılanı `OperationInvoker` bir yönteme çağrı yapmaya başlamadan hemen önce yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="3e2fe-114">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="3e2fe-115">İleti</span><span class="sxs-lookup"><span data-stu-id="3e2fe-115">Message</span></span>  

 <span data-ttu-id="3e2fe-116">Bir OperationInvoker ' %1 ' metodunu çağırdı.</span><span class="sxs-lookup"><span data-stu-id="3e2fe-116">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="3e2fe-117">Çağıran bilgileri: ' %2 '.</span><span class="sxs-lookup"><span data-stu-id="3e2fe-117">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="3e2fe-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="3e2fe-118">Details</span></span>  
  
|<span data-ttu-id="3e2fe-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="3e2fe-119">Data Item Name</span></span>|<span data-ttu-id="3e2fe-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="3e2fe-120">Data Item Type</span></span>|<span data-ttu-id="3e2fe-121">Description</span><span class="sxs-lookup"><span data-stu-id="3e2fe-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="3e2fe-122">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="3e2fe-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="3e2fe-123">Tarafından çağrılan metodun CLR adı `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="3e2fe-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="3e2fe-124">Arayan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="3e2fe-124">Caller Information</span></span>|`xs:string`|<span data-ttu-id="3e2fe-125">İstemcinin IP adresi ve bağlantı noktası numarası ' IPAddress: bağlantınoktasınumarası ' biçiminde.</span><span class="sxs-lookup"><span data-stu-id="3e2fe-125">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="3e2fe-126">İki değer, işlem bağlamı içindeki ' System. ServiceModel. Channels. RemoteEndpointMessageProperty ' ileti özelliğinden alınır.</span><span class="sxs-lookup"><span data-stu-id="3e2fe-126">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="3e2fe-127">TCP olmayan bağlamalar için bu değeri unutmayın `null` .</span><span class="sxs-lookup"><span data-stu-id="3e2fe-127">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="3e2fe-128">HostReference</span><span class="sxs-lookup"><span data-stu-id="3e2fe-128">HostReference</span></span>|`xs:string`|<span data-ttu-id="3e2fe-129">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3e2fe-129">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="3e2fe-130">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3e2fe-130">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="3e2fe-131">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="3e2fe-131">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="3e2fe-132">AppDomain</span><span class="sxs-lookup"><span data-stu-id="3e2fe-132">AppDomain</span></span>|`xs:string`|<span data-ttu-id="3e2fe-133">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="3e2fe-133">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
