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
ms.openlocfilehash: 5750748f2885418b8992ce54bbdf6a92b8e1fe39
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="219---serviceexception"></a><span data-ttu-id="c30ae-102">219 - ServiceException</span><span class="sxs-lookup"><span data-stu-id="c30ae-102">219 - ServiceException</span></span>
## <a name="properties"></a><span data-ttu-id="c30ae-103">Özellikler</span><span class="sxs-lookup"><span data-stu-id="c30ae-103">Properties</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c30ae-104">Kimlik</span><span class="sxs-lookup"><span data-stu-id="c30ae-104">ID</span></span>|<span data-ttu-id="c30ae-105">219</span><span class="sxs-lookup"><span data-stu-id="c30ae-105">219</span></span>|  
|<span data-ttu-id="c30ae-106">Anahtar Sözcükler</span><span class="sxs-lookup"><span data-stu-id="c30ae-106">Keywords</span></span>|<span data-ttu-id="c30ae-107">Sorun giderme, ServiceModel EndToEndMonitoring, ögesi,</span><span class="sxs-lookup"><span data-stu-id="c30ae-107">EndToEndMonitoring, HealthMonitoring, Troubleshooting, ServiceModel</span></span>|  
|<span data-ttu-id="c30ae-108">Düzey</span><span class="sxs-lookup"><span data-stu-id="c30ae-108">Level</span></span>|<span data-ttu-id="c30ae-109">Hata</span><span class="sxs-lookup"><span data-stu-id="c30ae-109">Error</span></span>|  
|<span data-ttu-id="c30ae-110">Kanal</span><span class="sxs-lookup"><span data-stu-id="c30ae-110">Channel</span></span>|<span data-ttu-id="c30ae-111">Microsoft Windows uygulama sunucusu-uygulamalar/analitik</span><span class="sxs-lookup"><span data-stu-id="c30ae-111">Microsoft-Windows-Application Server-Applications/Analytic</span></span>|  
  
## <a name="description"></a><span data-ttu-id="c30ae-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c30ae-112">Description</span></span>  
 <span data-ttu-id="c30ae-113">Bir WCF Hizmeti işlenmeyen bir özel durum karşılaştığında bu olay yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="c30ae-113">This event is emitted when a WCF service encounters an unhandled exception.</span></span> <span data-ttu-id="c30ae-114">Bu etkinleştirme, ileti işleme sırasında ve kullanıcı kodu sırasında işlenmeyen özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="c30ae-114">This includes unhandled exceptions during activation, during message processing, and in user code.</span></span>  
  
## <a name="message"></a><span data-ttu-id="c30ae-115">İleti</span><span class="sxs-lookup"><span data-stu-id="c30ae-115">Message</span></span>  
 <span data-ttu-id="c30ae-116">İleti işleme sırasında '%2' türünde işlenmeyen bir özel durum oluştu.</span><span class="sxs-lookup"><span data-stu-id="c30ae-116">There was an unhandled exception of type '%2' during message processing.</span></span> <span data-ttu-id="c30ae-117">ToString tam özel durum: %1.</span><span class="sxs-lookup"><span data-stu-id="c30ae-117">Full Exception ToString: %1.</span></span>  
  
## <a name="details"></a><span data-ttu-id="c30ae-118">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="c30ae-118">Details</span></span>  
  
|<span data-ttu-id="c30ae-119">Veri öğesi adı</span><span class="sxs-lookup"><span data-stu-id="c30ae-119">Data Item Name</span></span>|<span data-ttu-id="c30ae-120">Veri öğesi türü</span><span class="sxs-lookup"><span data-stu-id="c30ae-120">Data Item Type</span></span>|<span data-ttu-id="c30ae-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c30ae-121">Description</span></span>|  
|--------------------|--------------------|-----------------|  
|<span data-ttu-id="c30ae-122">ExceptionToString</span><span class="sxs-lookup"><span data-stu-id="c30ae-122">ExceptionToString</span></span>|`xs:string`|<span data-ttu-id="c30ae-123">Arama sonucu `ToString`CLR özel durumunda ().</span><span class="sxs-lookup"><span data-stu-id="c30ae-123">The result of calling `ToString`() on the CLR exception.</span></span>|  
|<span data-ttu-id="c30ae-124">ExceptionTypeName</span><span class="sxs-lookup"><span data-stu-id="c30ae-124">ExceptionTypeName</span></span>|`xs:string`|<span data-ttu-id="c30ae-125">Özel durumun türü CLR tam adı.</span><span class="sxs-lookup"><span data-stu-id="c30ae-125">The CLR FullName of the exception's type.</span></span>|  
|<span data-ttu-id="c30ae-126">HostReference</span><span class="sxs-lookup"><span data-stu-id="c30ae-126">HostReference</span></span>|`xs:string`|<span data-ttu-id="c30ae-127">Bu alan, Web barındırılan hizmetler için Web hiyerarşi hizmetinde benzersiz olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c30ae-127">For Web-hosted services, this field uniquely identifies the service in the Web hierarchy.</span></span> <span data-ttu-id="c30ae-128">Biçimi olarak tanımlanan ' Web sitesi adı uygulamanın sanal yolu &#124; Hizmet sanal yolu &#124; ServiceName'.</span><span class="sxs-lookup"><span data-stu-id="c30ae-128">Its format is defined as 'Web Site Name Application Virtual Path&#124;Service Virtual Path&#124;ServiceName'.</span></span> <span data-ttu-id="c30ae-129">Örnek: ' varsayılan Web sitesi/CalculatorApplication, #124;/CalculatorService.svc &#124; CalculatorService'.</span><span class="sxs-lookup"><span data-stu-id="c30ae-129">Example: 'Default Web Site/CalculatorApplication&#124;/CalculatorService.svc&#124;CalculatorService'.</span></span>|  
|<span data-ttu-id="c30ae-130">AppDomain</span><span class="sxs-lookup"><span data-stu-id="c30ae-130">AppDomain</span></span>|`xs:string`|<span data-ttu-id="c30ae-131">AppDomain.CurrentDomain.FriendlyName tarafından döndürülen dize.</span><span class="sxs-lookup"><span data-stu-id="c30ae-131">The string returned by AppDomain.CurrentDomain.FriendlyName.</span></span>|
