---
title: 202 - ClientMessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 0b02ca82-8a55-45e3-b2e2-ddfe28a7269c
ms.openlocfilehash: f05a0f817b8cb4857a4fa50eada15d3ff9e06855
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266629"
---
# <a name="202---clientmessageinspectorbeforesendinvoked"></a><span data-ttu-id="cb1e1-102">202 - ClientMessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="cb1e1-102">202 - ClientMessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="cb1e1-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="cb1e1-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cb1e1-104">ID</span><span class="sxs-lookup"><span data-stu-id="cb1e1-104">ID</span></span>|<span data-ttu-id="cb1e1-105">202</span><span class="sxs-lookup"><span data-stu-id="cb1e1-105">202</span></span>|  
|<span data-ttu-id="cb1e1-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="cb1e1-106">Keywords</span></span>|<span data-ttu-id="cb1e1-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cb1e1-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="cb1e1-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="cb1e1-108">Level</span></span>|<span data-ttu-id="cb1e1-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="cb1e1-109">Information</span></span>|  
|<span data-ttu-id="cb1e1-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="cb1e1-110">Channel</span></span>|<span data-ttu-id="cb1e1-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="cb1e1-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="cb1e1-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb1e1-112">Description</span></span>  

 <span data-ttu-id="cb1e1-113">Bu olay, hizmet modeli `BeforeSendRequest` bir istemci ileti denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="cb1e1-113">This event is emitted after the Service Model has invoked the `BeforeSendRequest` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="cb1e1-114">İleti</span><span class="sxs-lookup"><span data-stu-id="cb1e1-114">Message</span></span>  

 <span data-ttu-id="cb1e1-115">Dağıtıcı, ' %1 ' türünde bir Clientmessageınspector üzerinde ' BeforeSendRequest ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="cb1e1-115">The Dispatcher invoked 'BeforeSendRequest' on a ClientMessageInspector of type  '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="cb1e1-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="cb1e1-116">Details</span></span>  
  
|<span data-ttu-id="cb1e1-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="cb1e1-117">Data Item Name</span></span>|<span data-ttu-id="cb1e1-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="cb1e1-118">Data Item Type</span></span>|<span data-ttu-id="cb1e1-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cb1e1-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="cb1e1-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="cb1e1-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="cb1e1-121">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="cb1e1-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="cb1e1-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="cb1e1-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="cb1e1-123">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="cb1e1-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="cb1e1-124">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cb1e1-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="cb1e1-125">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="cb1e1-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="cb1e1-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="cb1e1-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="cb1e1-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="cb1e1-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
