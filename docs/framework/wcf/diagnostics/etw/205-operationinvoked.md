---
title: 205 - OperationInvoked
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7385d34ac2ed0357e964e992a88f96a6a89b1a26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="205---operationinvoked"></a><span data-ttu-id="7bd91-102">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="7bd91-102">205 - OperationInvoked</span></span>
## <a name="properties"></a><span data-ttu-id="7bd91-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7bd91-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7bd91-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="7bd91-104">ID</span></span>|<span data-ttu-id="7bd91-105">205</span><span class="sxs-lookup"><span data-stu-id="7bd91-105">205</span></span>|  
|<span data-ttu-id="7bd91-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="7bd91-106">Keywords</span></span>|<span data-ttu-id="7bd91-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7bd91-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="7bd91-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="7bd91-108">Level</span></span>|<span data-ttu-id="7bd91-109">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="7bd91-109">Information</span></span>|  
|<span data-ttu-id="7bd91-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="7bd91-110">Channel</span></span>|<span data-ttu-id="7bd91-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="7bd91-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="7bd91-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bd91-112">Description</span></span>  
 <span data-ttu-id="7bd91-113">Bu olay yalnızca hizmet modelinin varsayılan önce gösterilen `OperationInvoker` bir yöntemine yapılan bir çağrı başlar.</span><span class="sxs-lookup"><span data-stu-id="7bd91-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="7bd91-114">İleti</span><span class="sxs-lookup"><span data-stu-id="7bd91-114">Message</span></span>  
 <span data-ttu-id="7bd91-115">'%1' yöntemi bir OperationInvoker çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7bd91-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="7bd91-116">Arayan bilgileri: '%2'.</span><span class="sxs-lookup"><span data-stu-id="7bd91-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="7bd91-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="7bd91-117">Details</span></span>  
  
|<span data-ttu-id="7bd91-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="7bd91-118">Data Item Name</span></span>|<span data-ttu-id="7bd91-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="7bd91-119">Data Item Type</span></span>|<span data-ttu-id="7bd91-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bd91-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="7bd91-121">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="7bd91-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="7bd91-122">Tarafından çağrılan yöntemin CLR adını `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="7bd91-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="7bd91-123">Arayan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="7bd91-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="7bd91-124">'IPAddress:PortNumber' biçiminde istemci IP adresi ve bağlantı noktası numarası.</span><span class="sxs-lookup"><span data-stu-id="7bd91-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="7bd91-125">İki değer 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' ileti özelliği işlemi bağlamında alınır.</span><span class="sxs-lookup"><span data-stu-id="7bd91-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="7bd91-126">TCP olmayan bağlantılarında unutmayın bu değer `null`.</span><span class="sxs-lookup"><span data-stu-id="7bd91-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="7bd91-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="7bd91-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="7bd91-128">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7bd91-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="7bd91-129">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="7bd91-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="7bd91-130">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="7bd91-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="7bd91-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="7bd91-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="7bd91-132">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="7bd91-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
