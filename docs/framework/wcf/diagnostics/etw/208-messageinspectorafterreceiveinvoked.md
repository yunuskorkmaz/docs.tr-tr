---
title: 208 - MessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: dfb5f7b0-4346-4949-8104-351726b1f502
ms.openlocfilehash: 4aa0f41b0b772551d9257920e5c15051961b7332
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267825"
---
# <a name="208---messageinspectorafterreceiveinvoked"></a><span data-ttu-id="4b7f2-102">208 - MessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="4b7f2-102">208 - MessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="4b7f2-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="4b7f2-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4b7f2-104">ID</span><span class="sxs-lookup"><span data-stu-id="4b7f2-104">ID</span></span>|<span data-ttu-id="4b7f2-105">208</span><span class="sxs-lookup"><span data-stu-id="4b7f2-105">208</span></span>|  
|<span data-ttu-id="4b7f2-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="4b7f2-106">Keywords</span></span>|<span data-ttu-id="4b7f2-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4b7f2-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="4b7f2-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="4b7f2-108">Level</span></span>|<span data-ttu-id="4b7f2-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="4b7f2-109">Information</span></span>|  
|<span data-ttu-id="4b7f2-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="4b7f2-110">Channel</span></span>|<span data-ttu-id="4b7f2-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="4b7f2-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="4b7f2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b7f2-112">Description</span></span>  

 <span data-ttu-id="4b7f2-113">Bu olay, hizmet modeli `AfterReceive` bir ileti denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="4b7f2-113">This event is emitted after the Service Model has invoked the `AfterReceive` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="4b7f2-114">İleti</span><span class="sxs-lookup"><span data-stu-id="4b7f2-114">Message</span></span>  

 <span data-ttu-id="4b7f2-115">Dağıtıcı, ' %1 ' türünde bir Messageınspector üzerinde ' AfterReceiveReply ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="4b7f2-115">The Dispatcher invoked 'AfterReceiveReply' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="4b7f2-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4b7f2-116">Details</span></span>  
  
|<span data-ttu-id="4b7f2-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="4b7f2-117">Data Item Name</span></span>|<span data-ttu-id="4b7f2-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="4b7f2-118">Data Item Type</span></span>|<span data-ttu-id="4b7f2-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4b7f2-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="4b7f2-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="4b7f2-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="4b7f2-121">Çağrılan türünün CLR FullName değeri `MessageInspector` .</span><span class="sxs-lookup"><span data-stu-id="4b7f2-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="4b7f2-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="4b7f2-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="4b7f2-123">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4b7f2-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="4b7f2-124">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4b7f2-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="4b7f2-125">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="4b7f2-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="4b7f2-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="4b7f2-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="4b7f2-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="4b7f2-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
