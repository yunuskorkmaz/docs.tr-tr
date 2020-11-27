---
title: 205 - OperationInvoked
ms.date: 03/30/2017
ms.assetid: 9c8d6c90-dfa5-4ae0-a589-96679a8fb3ba
ms.openlocfilehash: c36294a4a430c3e372e8213246e85dba45ce03c8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286025"
---
# <a name="205---operationinvoked"></a><span data-ttu-id="e5635-102">205 - OperationInvoked</span><span class="sxs-lookup"><span data-stu-id="e5635-102">205 - OperationInvoked</span></span>

## <a name="properties"></a><span data-ttu-id="e5635-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e5635-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e5635-104">ID</span><span class="sxs-lookup"><span data-stu-id="e5635-104">ID</span></span>|<span data-ttu-id="e5635-105">205</span><span class="sxs-lookup"><span data-stu-id="e5635-105">205</span></span>|  
|<span data-ttu-id="e5635-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="e5635-106">Keywords</span></span>|<span data-ttu-id="e5635-107">Sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e5635-107">Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="e5635-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="e5635-108">Level</span></span>|<span data-ttu-id="e5635-109">Bilgi</span><span class="sxs-lookup"><span data-stu-id="e5635-109">Information</span></span>|  
|<span data-ttu-id="e5635-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="e5635-110">Channel</span></span>|<span data-ttu-id="e5635-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="e5635-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="e5635-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5635-112">Description</span></span>  

 <span data-ttu-id="e5635-113">Bu olay, hizmet modeli varsayılanı `OperationInvoker` bir yönteme çağrı yapmaya başlamadan hemen önce yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="e5635-113">This event is emitted just before the Service Model's default `OperationInvoker` begins a call to a method.</span></span>  
  
## <a name="message"></a><span data-ttu-id="e5635-114">İleti</span><span class="sxs-lookup"><span data-stu-id="e5635-114">Message</span></span>  

 <span data-ttu-id="e5635-115">Bir OperationInvoker ' %1 ' metodunu çağırdı.</span><span class="sxs-lookup"><span data-stu-id="e5635-115">An OperationInvoker invoked the '%1' method.</span></span> <span data-ttu-id="e5635-116">Çağıran bilgileri: ' %2 '.</span><span class="sxs-lookup"><span data-stu-id="e5635-116">Caller information: '%2'.</span></span>  
  
## <a name="details"></a><span data-ttu-id="e5635-117">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="e5635-117">Details</span></span>  
  
|<span data-ttu-id="e5635-118">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="e5635-118">Data Item Name</span></span>|<span data-ttu-id="e5635-119">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="e5635-119">Data Item Type</span></span>|<span data-ttu-id="e5635-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5635-120">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="e5635-121">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="e5635-121">Method Name</span></span>|`xs:string`|<span data-ttu-id="e5635-122">Tarafından çağrılan metodun CLR adı `OperationInvoker` .</span><span class="sxs-lookup"><span data-stu-id="e5635-122">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="e5635-123">Arayan Bilgileri</span><span class="sxs-lookup"><span data-stu-id="e5635-123">Caller Information</span></span>|`xs:string`|<span data-ttu-id="e5635-124">İstemcinin IP adresi ve bağlantı noktası numarası ' IPAddress: bağlantınoktasınumarası ' biçiminde.</span><span class="sxs-lookup"><span data-stu-id="e5635-124">The IP address and port number of the client in the format 'IPAddress:PortNumber'.</span></span> <span data-ttu-id="e5635-125">İki değer, işlem bağlamı içindeki ' System. ServiceModel. Channels. RemoteEndpointMessageProperty ' ileti özelliğinden alınır.</span><span class="sxs-lookup"><span data-stu-id="e5635-125">The two values are retrieved from the 'System.ServiceModel.Channels.RemoteEndpointMessageProperty' message property within the operation context.</span></span> <span data-ttu-id="e5635-126">TCP olmayan bağlamalar için bu değeri unutmayın `null` .</span><span class="sxs-lookup"><span data-stu-id="e5635-126">Note that for non-TCP bindings this value `null`.</span></span>|  
|<span data-ttu-id="e5635-127">HostReference</span><span class="sxs-lookup"><span data-stu-id="e5635-127">HostReference</span></span>|`xs:string`|<span data-ttu-id="e5635-128">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e5635-128">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="e5635-129">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e5635-129">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="e5635-130">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="e5635-130">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="e5635-131">AppDomain</span><span class="sxs-lookup"><span data-stu-id="e5635-131">AppDomain</span></span>|`xs:string`|<span data-ttu-id="e5635-132">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="e5635-132">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
