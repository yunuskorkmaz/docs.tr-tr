---
title: 201 - ClientMessageInspectorAfterReceiveInvoked
ms.date: 03/30/2017
ms.assetid: 9ff637f1-cc26-4400-ab9b-546f70e5057d
ms.openlocfilehash: d84f6c6f38868f7915caaaf87e15885099b65456
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266681"
---
# <a name="201---clientmessageinspectorafterreceiveinvoked"></a><span data-ttu-id="28a7b-102">201 - ClientMessageInspectorAfterReceiveInvoked</span><span class="sxs-lookup"><span data-stu-id="28a7b-102">201 - ClientMessageInspectorAfterReceiveInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="28a7b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="28a7b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="28a7b-104">ID</span><span class="sxs-lookup"><span data-stu-id="28a7b-104">ID</span></span>|<span data-ttu-id="28a7b-105">201</span><span class="sxs-lookup"><span data-stu-id="28a7b-105">201</span></span>|  
|<span data-ttu-id="28a7b-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="28a7b-106">Keywords</span></span>|<span data-ttu-id="28a7b-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="28a7b-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="28a7b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="28a7b-108">Level</span></span>|<span data-ttu-id="28a7b-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="28a7b-109">Information</span></span>|  
|<span data-ttu-id="28a7b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="28a7b-110">Channel</span></span>|<span data-ttu-id="28a7b-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="28a7b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="28a7b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28a7b-112">Description</span></span>  

 <span data-ttu-id="28a7b-113">Bu olay, hizmet modeli `AfterReceiveReply` bir istemci ileti denetçisinde yöntemi çağırdıktan sonra yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="28a7b-113">This event is emitted after the Service Model has invoked the `AfterReceiveReply` method on a client message inspector.</span></span>  
  
## <a name="message"></a><span data-ttu-id="28a7b-114">İleti</span><span class="sxs-lookup"><span data-stu-id="28a7b-114">Message</span></span>  

 <span data-ttu-id="28a7b-115">Dağıtıcı, ' %1 ' türünde bir Clientmessageınspector üzerinde ' AfterReceiveReply ' çağırdı.</span><span class="sxs-lookup"><span data-stu-id="28a7b-115">The Dispatcher invoked 'AfterReceiveReply' on a ClientMessageInspector of type '%1'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="28a7b-116">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="28a7b-116">Details</span></span>  
  
|<span data-ttu-id="28a7b-117">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="28a7b-117">Data Item Name</span></span>|<span data-ttu-id="28a7b-118">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="28a7b-118">Data Item Type</span></span>|<span data-ttu-id="28a7b-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="28a7b-119">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="28a7b-120">TypeName</span><span class="sxs-lookup"><span data-stu-id="28a7b-120">TypeName</span></span>|`xs:string`|<span data-ttu-id="28a7b-121">Çağrılan Inspector türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="28a7b-121">The CLR FullName of the invoked inspector's type.</span></span>|  
|<span data-ttu-id="28a7b-122">HostReference</span><span class="sxs-lookup"><span data-stu-id="28a7b-122">HostReference</span></span>|`xs:string`|<span data-ttu-id="28a7b-123">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="28a7b-123">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="28a7b-124">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="28a7b-124">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="28a7b-125">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="28a7b-125">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="28a7b-126">AppDomain</span><span class="sxs-lookup"><span data-stu-id="28a7b-126">AppDomain</span></span>|`xs:string`|<span data-ttu-id="28a7b-127">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="28a7b-127">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
