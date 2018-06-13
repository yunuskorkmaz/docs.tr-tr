---
title: 222 - OperationFailed
ms.date: 03/30/2017
ms.assetid: 6b530ded-8f20-4d78-8bfe-1875276df6ba
ms.openlocfilehash: c49aad0f93ce47b66306d75741267530dc6d3fe5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33460748"
---
# <a name="222---operationfailed"></a><span data-ttu-id="89d4a-102">222 - OperationFailed</span><span class="sxs-lookup"><span data-stu-id="89d4a-102">222 - OperationFailed</span></span>
## <a name="properties"></a><span data-ttu-id="89d4a-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="89d4a-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="89d4a-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="89d4a-104">ID</span></span>|<span data-ttu-id="89d4a-105">222</span><span class="sxs-lookup"><span data-stu-id="89d4a-105">222</span></span>|  
|<span data-ttu-id="89d4a-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="89d4a-106">Keywords</span></span>|<span data-ttu-id="89d4a-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="89d4a-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="89d4a-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="89d4a-108">Level</span></span>|<span data-ttu-id="89d4a-109">Uyarı</span><span class="sxs-lookup"><span data-stu-id="89d4a-109">Warning</span></span>|  
|<span data-ttu-id="89d4a-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="89d4a-110">Channel</span></span>|<span data-ttu-id="89d4a-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="89d4a-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="89d4a-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89d4a-112">Description</span></span>  
 <span data-ttu-id="89d4a-113">Bu olay yayılan, hizmet modelinin varsayılan `OperationInvoker` kendi yönteminin çağrılması sırasında bir özel durumla karşılaştı.</span><span class="sxs-lookup"><span data-stu-id="89d4a-113">This event is emitted when the Service Model's default `OperationInvoker` has encountered an exception while invoking its method.</span></span> <span data-ttu-id="89d4a-114">Not öğesinden türetilen bu özel durumlar `FaultException` değil yayınlaması için bu olay neden.</span><span class="sxs-lookup"><span data-stu-id="89d4a-114">Note that exceptions that derive from `FaultException` cause this event to not be emitted.</span></span>  
  
## <a name="message"></a><span data-ttu-id="89d4a-115">İleti</span><span class="sxs-lookup"><span data-stu-id="89d4a-115">Message</span></span>  
 <span data-ttu-id="89d4a-116">'%1' yöntemi, OperationInvoker tarafından çağrıldığında işlenmeyen bir özel durum oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="89d4a-116">The '%1' method threw an unhandled exception when invoked by the OperationInvoker.</span></span> <span data-ttu-id="89d4a-117">Yöntem çağrısı süre, '%2' ms idi.</span><span class="sxs-lookup"><span data-stu-id="89d4a-117">The method call duration was '%2' ms.</span></span>  
  
## <a name="details"></a><span data-ttu-id="89d4a-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="89d4a-118">Details</span></span>  
  
|<span data-ttu-id="89d4a-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="89d4a-119">Data Item Name</span></span>|<span data-ttu-id="89d4a-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="89d4a-120">Data Item Type</span></span>|<span data-ttu-id="89d4a-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89d4a-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="89d4a-122">Yöntem adı</span><span class="sxs-lookup"><span data-stu-id="89d4a-122">Method Name</span></span>|`xs:string`|<span data-ttu-id="89d4a-123">Tarafından çağrılan yöntemin CLR adını `OperationInvoker`.</span><span class="sxs-lookup"><span data-stu-id="89d4a-123">The CLR name of the method that was invoked by the `OperationInvoker`.</span></span>|  
|<span data-ttu-id="89d4a-124">Süre</span><span class="sxs-lookup"><span data-stu-id="89d4a-124">Duration</span></span>|`xs:long`|<span data-ttu-id="89d4a-125">Geçen milisaniye cinsinden süre `OperationInvoker` yöntemini çağırmak için.</span><span class="sxs-lookup"><span data-stu-id="89d4a-125">The time, in milliseconds, that it took the `OperationInvoker` to invoke the method.</span></span>|  
|<span data-ttu-id="89d4a-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="89d4a-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="89d4a-127">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="89d4a-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="89d4a-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu&#124;hizmet sanal yolu&#124;ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="89d4a-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="89d4a-129">Örnek: ' varsayılan Web sitesi/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="89d4a-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="89d4a-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="89d4a-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="89d4a-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="89d4a-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
