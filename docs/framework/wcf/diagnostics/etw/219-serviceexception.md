---
title: 219 - ServiceException
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81e2efac-39aa-4ed2-85a9-97eb8793b844
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fceff5c748076c75c942f515e2621edff5106f4e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="219---serviceexception"></a><span data-ttu-id="fde4b-102">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="fde4b-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="fde4b-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="fde4b-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="fde4b-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="fde4b-104">ID</span></span>|<span data-ttu-id="fde4b-105">219</span><span class="sxs-lookup"><span data-stu-id="fde4b-105">219</span></span>|  
|<span data-ttu-id="fde4b-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="fde4b-106">Keywords</span></span>|<span data-ttu-id="fde4b-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="fde4b-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="fde4b-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="fde4b-108">Level</span></span>|<span data-ttu-id="fde4b-109">Hata</span><span class="sxs-lookup"><span data-stu-id="fde4b-109">Error</span></span>|  
|<span data-ttu-id="fde4b-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="fde4b-110">Channel</span></span>|<span data-ttu-id="fde4b-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="fde4b-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="fde4b-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fde4b-112">Description</span></span>  
 <span data-ttu-id="fde4b-113">Bir WCF Hizmeti işlenmeyen bir özel durum karşılaştığında bu olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="fde4b-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="fde4b-114">Bu etkinleştirme, ileti işleme sırasında ve kullanıcı kodu sırasında işlenmeyen özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="fde4b-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="fde4b-115">İleti</span><span class="sxs-lookup"><span data-stu-id="fde4b-115">Message</span></span>  
 <span data-ttu-id="fde4b-116">İleti işleme sırasında '%2' türünde işlenmeyen bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="fde4b-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="fde4b-117">ToString tam özel durum: %1.</span><span class="sxs-lookup"><span data-stu-id="fde4b-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="fde4b-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="fde4b-118">Details</span></span>  
  
|<span data-ttu-id="fde4b-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="fde4b-119">Data Item Name</span></span>|<span data-ttu-id="fde4b-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="fde4b-120">Data Item Type</span></span>|<span data-ttu-id="fde4b-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fde4b-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="fde4b-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="fde4b-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="fde4b-123">Arama sonucu `ToString`CLR özel durumunda ().</span><span class="sxs-lookup"><span data-stu-id="fde4b-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="fde4b-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="fde4b-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="fde4b-125">Özel durumun türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="fde4b-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="fde4b-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="fde4b-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="fde4b-127">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="fde4b-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="fde4b-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="fde4b-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="fde4b-129">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="fde4b-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="fde4b-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="fde4b-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="fde4b-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="fde4b-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
