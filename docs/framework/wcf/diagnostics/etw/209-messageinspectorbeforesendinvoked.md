---
title: 209 - MessageInspectorBeforeSendInvoked
ms.date: 03/30/2017
ms.assetid: 7d710875-fb77-4463-978b-bc86d59d84cd
ms.openlocfilehash: 50a9424f445781cac70d7d7fde58beea10231cfa
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267760"
---
# <a name="209---messageinspectorbeforesendinvoked"></a><span data-ttu-id="410cf-102">209 - MessageInspectorBeforeSendInvoked</span><span class="sxs-lookup"><span data-stu-id="410cf-102">209 - MessageInspectorBeforeSendInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="410cf-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="410cf-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="410cf-104">ID</span><span class="sxs-lookup"><span data-stu-id="410cf-104">ID</span></span>|<span data-ttu-id="410cf-105">209</span><span class="sxs-lookup"><span data-stu-id="410cf-105">209</span></span>|  
|<span data-ttu-id="410cf-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="410cf-106">Keywords</span></span>|<span data-ttu-id="410cf-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="410cf-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="410cf-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="410cf-108">Level</span></span>|<span data-ttu-id="410cf-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="410cf-109">Information</span></span>|  
|<span data-ttu-id="410cf-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="410cf-110">Channel</span></span>|<span data-ttu-id="410cf-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="410cf-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="410cf-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="410cf-112">Description</span></span>  

 <span data-ttu-id="410cf-113">Bu olay, hizmet modeli `BeforeSend` bir ileti denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="410cf-113">This event is emitted after the Service Model has invoked the `BeforeSend` method on a message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="410cf-114">İleti</span><span class="sxs-lookup"><span data-stu-id="410cf-114">Message</span></span>  

 <span data-ttu-id="410cf-115">Dağıtıcı, ' %1 ' türünde bir Messageınspector üzerinde ' BeforeSendRequest ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="410cf-115">The Dispatcher invoked 'BeforeSendRequest' on a MessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="410cf-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="410cf-116">Details</span></span>  
  
|<span data-ttu-id="410cf-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="410cf-117">Data Item Name</span></span>|<span data-ttu-id="410cf-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="410cf-118">Data Item Type</span></span>|<span data-ttu-id="410cf-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="410cf-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="410cf-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="410cf-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="410cf-121">Çağrılan türünün CLR FullName değeri `MessageInspector` .</span><span class="sxs-lookup"><span data-stu-id="410cf-121">The CLR FullName of the type of the invoked `MessageInspector`.</span></span>|  
|<span data-ttu-id="410cf-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="410cf-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="410cf-123">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="410cf-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="410cf-124">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="410cf-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="410cf-125">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="410cf-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="410cf-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="410cf-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="410cf-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="410cf-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
