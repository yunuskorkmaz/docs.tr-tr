---
title: 219 - ServiceException
ms.date: 03/30/2017
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
ms.openlocfilehash: 832ced406b6079fad8f4b9bea512a6d390bdcc0f
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241947"
---
# <a name="219---serviceexception"></a><span data-ttu-id="78062-102">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="78062-102">219 - ServiceException</span></span>

## <a name="properties"></a><span data-ttu-id="78062-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="78062-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="78062-104">ID</span><span class="sxs-lookup"><span data-stu-id="78062-104">ID</span></span>|<span data-ttu-id="78062-105">219</span><span class="sxs-lookup"><span data-stu-id="78062-105">219</span></span>|  
|<span data-ttu-id="78062-106">Anahtar sözcükler</span><span class="sxs-lookup"><span data-stu-id="78062-106">Keywords</span></span>|<span data-ttu-id="78062-107">EndToEndMonitoring, HealthMonitoring, sorun giderme, ServiceModel</span><span class="sxs-lookup"><span data-stu-id="78062-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="78062-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="78062-108">Level</span></span>|<span data-ttu-id="78062-109">Hata</span><span class="sxs-lookup"><span data-stu-id="78062-109">Error</span></span>|  
|<span data-ttu-id="78062-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="78062-110">Channel</span></span>|<span data-ttu-id="78062-111">Microsoft-Windows-uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="78062-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="78062-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78062-112">Description</span></span>  

 <span data-ttu-id="78062-113">Bu olay, bir WCF hizmeti işlenmeyen bir özel durumla karşılaştığında yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="78062-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="78062-114">Bu, etkinleştirme sırasında, ileti işleme sırasında ve Kullanıcı kodunda işlenmeyen özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="78062-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="78062-115">İleti</span><span class="sxs-lookup"><span data-stu-id="78062-115">Message</span></span>  

 <span data-ttu-id="78062-116">İleti işleme sırasında ' %2 ' türünde işlenmeyen bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="78062-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="78062-117">Tam özel durum ToString: %1.</span><span class="sxs-lookup"><span data-stu-id="78062-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="78062-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="78062-118">Details</span></span>  
  
|<span data-ttu-id="78062-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="78062-119">Data Item Name</span></span>|<span data-ttu-id="78062-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="78062-120">Data Item Type</span></span>|<span data-ttu-id="78062-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="78062-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="78062-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="78062-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="78062-123">`ToString`Clr özel durumuyla () çağırmanın sonucu.</span><span class="sxs-lookup"><span data-stu-id="78062-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="78062-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="78062-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="78062-125">Özel durum türünün CLR FullName değeri.</span><span class="sxs-lookup"><span data-stu-id="78062-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="78062-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="78062-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="78062-127">Web 'de barındırılan hizmetler için, bu alan hizmeti Web hiyerarşisinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="78062-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="78062-128">Biçimi ' Web sitesi adı uygulama sanal yolu&#124;hizmet sanal yolu&#124;ServiceName ' olarak tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="78062-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="78062-129">Örnek: ' Default Web site/Hesaplatooypplication&#124;/Hesaplatorservice.exe&#124;Hesaplatorservice '.</span><span class="sxs-lookup"><span data-stu-id="78062-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="78062-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="78062-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="78062-131">AppDomain. CurrentDomain. FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="78062-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
