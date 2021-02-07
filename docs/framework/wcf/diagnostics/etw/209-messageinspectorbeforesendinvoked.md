---
description: 'Hakkında daha fazla bilgi edinin: 209-Messageınspectorbeforesendıned'
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 337ed7d4c62d41d72cb2b4710c9f98f863305aee
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728008"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="2f911-103">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="2f911-103">209 - MessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="2f911-104">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2f911-104">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2f911-105">ID</span><span class="sxs-lookup"><span data-stu-id="2f911-105">ID</span></span>|<span data-ttu-id="2f911-106">209</span><span class="sxs-lookup"><span data-stu-id="2f911-106">209</span></span>|  
|<span data-ttu-id="2f911-107">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="2f911-107">Keywords</span></span>|<span data-ttu-id="2f911-108">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2f911-108">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="2f911-109">Level</span><span class="sxs-lookup"><span data-stu-id="2f911-109">Level</span></span>|<span data-ttu-id="2f911-110">Bilgi</span><span class="sxs-lookup"><span data-stu-id="2f911-110">Information</span></span>|  
|<span data-ttu-id="2f911-111">Kanal</span><span class="sxs-lookup"><span data-stu-id="2f911-111">Channel</span></span>|<span data-ttu-id="2f911-112">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="2f911-112">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="2f911-113">Description</span><span class="sxs-lookup"><span data-stu-id="2f911-113">Description</span></span>  

 <span data-ttu-id="2f911-114">Bu olay, hizmet modeli `BeforeSend` bir ileti denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="2f911-114">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="2f911-115">İleti</span><span class="sxs-lookup"><span data-stu-id="2f911-115">Message</span></span>  

 <span data-ttu-id="2f911-116">Dağıtıcı, ' %1 ' türünde bir Messageınspector üzerinde ' BeforeSendRequest ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="2f911-116">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="2f911-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="2f911-117">Details</span></span>  
  
|<span data-ttu-id="2f911-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="2f911-118">Data Item Name</span></span>|<span data-ttu-id="2f911-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="2f911-119">Data Item Type</span></span>|<span data-ttu-id="2f911-120">Description</span><span class="sxs-lookup"><span data-stu-id="2f911-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="2f911-121">TypeName</span><span class="sxs-lookup"><span data-stu-id="2f911-121">TypeName</span></span>|`xs:string`|<span data-ttu-id="2f911-122">Çağrılan türünün CLR FullName değeri `MessageInspector` .</span><span class="sxs-lookup"><span data-stu-id="2f911-122">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="2f911-123">HostReference</span><span class="sxs-lookup"><span data-stu-id="2f911-123">HostReference</span></span>|`xs:string`|<span data-ttu-id="2f911-124">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="2f911-124">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="2f911-125">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="2f911-125">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="2f911-126">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="2f911-126">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="2f911-127">AppDomain</span><span class="sxs-lookup"><span data-stu-id="2f911-127">AppDomain</span></span>|`xs:string`|<span data-ttu-id="2f911-128">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="2f911-128">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
