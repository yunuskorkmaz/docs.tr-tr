---
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781647"
---
# <a name="222---operationfailed"></a><span data-ttu-id="299fb-102">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="299fb-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="299fb-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="299fb-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="299fb-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="299fb-104">ID</span></span>|<span data-ttu-id="299fb-105">222</span><span class="sxs-lookup"><span data-stu-id="299fb-105">222</span></span>|  
|<span data-ttu-id="299fb-106">anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="299fb-106">Keywords</span></span>|<span data-ttu-id="299fb-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="299fb-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="299fb-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="299fb-108">Level</span></span>|<span data-ttu-id="299fb-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="299fb-109">Warning</span></span>|  
|<span data-ttu-id="299fb-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="299fb-110">Channel</span></span>|<span data-ttu-id="299fb-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="299fb-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="299fb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="299fb-112">Description</span></span>  
 <span data-ttu-id="299fb-113">Bu olay yayılan olduğunda hizmet modelinin varsayılan `OperationInvoker` kendi metodu çağrılırken bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="299fb-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="299fb-114">Not öğesinden türetilen, özel durumlar `FaultException` değil derleyicisindeki bu olayın neden.</span><span class="sxs-lookup"><span data-stu-id="299fb-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="299fb-115">İleti</span><span class="sxs-lookup"><span data-stu-id="299fb-115">Message</span></span>  
 <span data-ttu-id="299fb-116">'%1' yöntemi tarafından OperationInvoker çağrıldığında işlenmeyen bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="299fb-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="299fb-117">Yöntem çağrısı süresi '%2' ms idi.</span><span class="sxs-lookup"><span data-stu-id="299fb-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="299fb-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="299fb-118">Details</span></span>  
  
|<span data-ttu-id="299fb-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="299fb-119">Data Item Name</span></span>|<span data-ttu-id="299fb-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="299fb-120">Data Item Type</span></span>|<span data-ttu-id="299fb-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="299fb-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="299fb-122">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="299fb-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="299fb-123">CLR adı tarafından çağrılan yöntemin `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="299fb-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="299fb-124">Süresi</span><span class="sxs-lookup"><span data-stu-id="299fb-124">Duration</span></span>|`xs:long`|<span data-ttu-id="299fb-125">Geçen milisaniye cinsinden zaman `OperationInvoker` yöntemini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="299fb-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="299fb-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="299fb-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="299fb-127">Bu alan, Web barındırılan hizmetleri, Web hiyerarşideki hizmet benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="299fb-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="299fb-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;HizmetAdı '.</span><span class="sxs-lookup"><span data-stu-id="299fb-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="299fb-129">Örnek: ' Varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="299fb-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="299fb-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="299fb-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="299fb-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="299fb-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
